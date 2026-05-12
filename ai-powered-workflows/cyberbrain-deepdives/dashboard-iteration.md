>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Dashboard Iteration Story

*Companion to [Building a Cyberbrain: Step 8 - Build Your Dashboard](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Building%20a%20Cyberbrain.md#step-8-build-your-dashboard)*

---

# Why This Guide Exists

The other deep dives in this series tell you *what* the system became. This one tells you *how the dashboard got there*. The actual ping-pong between me (the human) and Claude over a couple dozen turns.

The reason that matters: Claude looks magical in a demo, but a real tool is built in the messy middle. Knowing how to drive through the messy middle is the skill. You will hit the same kinds of issues I hit. The patterns below are what I would do differently and what I would do exactly the same.

Below is the actual sequence of prompts I gave, what Claude got right on the first try, where it got stuck, and the patterns I would repeat next time.

---

# The Setup

I started by writing a real design brief in markdown (a `.md` file with goals, audience, the four views I wanted, sample task data, scoring philosophy, the aesthetic I was after). I described the aesthetic as Things 3 crossed with Sunsama, in dark mode. I attached the brief and said: "see the brief, design something."

**Lesson 0:** A written brief is the single highest-leverage move. The brief took 20 minutes to write. It saved hours of back-and-forth and probably bought 70% of the final design quality. If you are tempted to skip it, do not.

---

# Turn 1: First Shot

Claude did not ask any clarifying questions. The brief had enough. It built four views (Today, Kanban, Matrix, Settings) plus a token sheet, in React with split files for components, icons, data, and each view.

**What worked:** Modular file structure (`view-today.jsx`, `view-kanban.jsx`, components, icons, styles, data) meant later edits could be surgical, not whole-file rewrites.

**What I had to fix:** The first version used initials (`JT`, `KW`, `MR`) for people. I had to say "names are hard to know" and ask for full names with colored tags. Small thing, but it shows that even a thorough brief leaves gaps the AI fills with reasonable-but-wrong defaults.

---

# The White Space Saga (A Cautionary Tale)

This was the longest single thread. The Today's Focus view had a huge dead zone above the cards and everything was squished bottom-left.

What Claude got wrong, in order:

1. **First guess:** stray `height: "955px"` inline style on a wrapper. Removed it. Did not fix it.
2. **Second guess:** the `.view` element collapsing inside a flex column parent. Added `flex: 1 1 auto; min-height: 0`. Did not fix it.
3. **Third guess:** the whole grid was not sizing correctly. Restructured `.app` grid to `auto auto 1fr`, gave the inner column `height: 100%; min-height: 0; overflow: hidden`. **This was the actual fix.**

That is three full iterations on the same bug. I (the human) had to keep telling Claude "no, this still looks wrong" with screenshots before it would re-examine the assumption instead of patching downstream.

**Lessons from this thread:**

- **Screenshots beat descriptions.** Once I sent a marked-up screenshot showing exactly where the dead space was, Claude found it faster than my verbal description ever achieved.
- **AI (Artificial Intelligence) confidence is a trap.** Claude said "fixed!" three times in a row, each time wrong. Treat every "fixed" as a hypothesis until you have seen it with your own eyes.
- **CSS (Cascading Style Sheets) layout bugs propagate.** The real bug was at the `.app` grid level. Patches at the leaf elements just shuffled the problem around. When fixes do not stick, climb the DOM (Document Object Model) tree.

If I were doing this again I would say "before you fix it, eval the computed heights of `.app`, `.main`, `.view`, and tell me what you see." That probe-first habit saves rounds.

---

# The Quick Wins (Where Claude Shined)

In contrast, some asks went from prompt to working in one shot:

| Ask | Result |
|---|---|
| "Make the detail panel half the page width" | One-shot. `clamp(440px, 50vw, 720px)` as a fixed overlay. |
| "Let me close it by clicking outside, or the same task, or Esc" | One-shot. Three event listeners, all working. |
| "Make impact/effort/energy clickable" | One-shot. Click dots to set values, click same value to clear. |
| "Auto-recompute score live" | One-shot. Formula function, called on every edit, updates everywhere. |
| "Tags should be editable. Click + to add, × to remove." | One-shot. Inline input, Enter to save, Esc to cancel. |
| "Add new people, not just pick from existing" | One-shot. Picker with "+ new person" that prompts for a name. |
| "Drag cards between matrix quadrants" | One-shot. Dragover/drop handlers, score recomputes after move. |
| "Strip my personal info and make a shareable version" | One-shot. Renamed projects, people, scrubbed task content while keeping structure. |

The pattern in these: they are **structural changes** with clear semantics. CSS layout debugging is the opposite. Small surface area, lots of invisible interactions. AI is better at the former than the latter.

---

# The Score Formula Conversation

I asked "what's the max score and how does it add up to it" because the existing 1 to 20 number was opaque.

Claude **proposed an explicit formula before writing any code**:

```
impact (1-5) * 7   -> 0-35   (how much it moves the needle)
urgency            -> 0-30   (Today=30, Soon=20, Normal=10)
quadrant boost     -> 0-20   (Important&Urgent=20, Important=15, Urgent=10, Neither=0)
fit bonus          -> 0-15   ((impact - effort + 4) * 1.5, capped)
                   = 0-100
```

I said "use that" and it shipped. Color tiers: 80+ top (gold glow), 60 to 79 high, 40 to 59 normal, under 40 low.

**Lesson:** When the AI proposes a formula, schema, or system in writing **before** building it, *that is the moment to push back*. Words are cheap to change. Once it is in code, every edit is a CSS hunt. I should have done this on day one with the 1 to 20 score. I just accepted whatever came out and lived with confusion until the conversation forced clarity.

---

# The structuredContent Surprise

Partway through the build I hit a wall that was not in the brief and was not documented anywhere. When the dashboard called MCP (Model Context Protocol) tools via `window.cowork.callMcpTool()`, the responses came back wrapped in Cowork's `structuredContent` format. The actual data was nested inside `result` objects, sometimes multiple layers deep.

The first version of the dashboard rendered blank because the data parser was looking at the wrong layer of the response. Claude diagnosed it by logging the raw response shape, then wrote an `extractData()` function that progressively unwraps the response:

```javascript
function extractData(response) {
  let data = response;
  if (data.structuredContent) data = data.structuredContent;
  if (data.result) data = data.result;
  // further unwrapping as needed
  return data;
}
```

If you build your own Cowork artifacts that call MCP tools, you will likely run into the same wrapping. The fix is straightforward once you see the shape. The hard part is realizing the wrapping is there in the first place. Lesson: when an AI-built tool renders blank and the network calls look fine, log the raw response shape before debugging anything else.

---

# The Font-Size Regression

One representative failure I want to be honest about:

I asked for everything to be 50% bigger. Claude used `body { zoom: 1.5 }`. That worked visually but **broke the Kanban and Matrix layouts** because the viewport math did not account for zoom. Five Kanban columns got cut off; the Matrix bottom row was clipped.

I sent screenshots. Claude dropped the zoom and shrunk individual font sizes back down. Now the layouts fit, but the text was small again. I had to say "you regressed" with another screenshot.

The final fix was a hand-tuned set of `!important` font-size overrides per component class. Not elegant, but it works, and it does not break layout.

**Lesson:** When the AI reaches for a "global hack" (like `zoom`, `transform: scale`, or `* { font-size: ... }`), that is the moment to ask "what is the explicit list of things you are changing, and what is the failure mode?" Those broad strokes are tempting because they are one line. They are dangerous for the same reason.

---

# Patterns That Worked Repeatedly

After two dozen turns, these are the prompts that consistently got good results.

### 1. Use screenshots, not just words

"This looks wrong" plus screenshot beats three paragraphs of description. Especially for layout, color, and spacing.

### 2. Name the regression

"You regressed. The font is back to small. Look at screenshot 1 vs the current state." This forces the AI to compare states, not just respond to the immediate ask in isolation.

### 3. Ask for the system before the code

"What is the formula?" "What is the list of CSS variables?" "What is the data model?" Get it in prose first. Edit it. Then say "build that."

### 4. Use version copies as a safety net

I asked Claude to create a `v3` rather than overwrite `v2` mid-major-change. When `v3` broke in a confusing way, I still had `v2` as a known-good reference. **This is the cheapest insurance you can buy in iterative AI work.**

### 5. Push back when the AI claims a fix without evidence

"You said fixed three times. Re-read your last three fixes. What assumption are you not questioning?" This works. It forces the AI out of patch-mode.

### 6. Ask for cross-cutting features in one prompt

"Make impact, effort, energy, due date, and time estimate editable, and recompute the score live on every change." Better than five separate prompts. The AI can see the shape of the whole feature and design coherently. When the features are unrelated, separate them. When they share a code path, bundle them.

---

# Patterns That Failed

### 1. Vague feedback

"The view looks weird." This got me a guess-and-check cycle. "There is a 400px dead zone above the first card, between the tab bar and the content" got me a fix.

### 2. Assuming a fix worked

Claude says "fixed." I move on. Two prompts later I realize it never worked. Now I always re-screenshot after every layout-touching fix.

### 3. Letting the AI add UI (User Interface) noise unprompted

In the first pass Claude added cute touches I did not ask for. Score breakdowns, formula footers, decorative dots. Some I kept, some I cut. **Lesson:** Tell it what to remove, not just what to add. The detail panel went through three rounds of "remove the quadrant chip from the card header, the detail header, the related tasks list" because the chip showed up in multiple places.

### 4. Letting the chat get too long without snipping or summarizing

When you are 20 turns deep, the AI starts losing the thread on what version of what file is canonical. Periodically saying "we are now working on `v3`. `v2` is frozen, ignore it" helps. Claude can prune its own context but a human checkpoint is still useful.

---

# What I'd Do Differently Next Time

1. **Write the formula and data model in markdown first.** Get the 0 to 100 score, the field names, the people roster, the project list nailed down in a doc *before* asking for any UI. Treat the UI build as the easy part.

2. **Build a screenshot ritual.** After every layout or visual change, screenshot the relevant view immediately. Do not rely on the AI's "it should look like X now."

3. **Ask for a debug-probe before a fix.** "Before you change anything, eval `getComputedStyle` on the elements involved and tell me what you see." This catches phantom bugs (like the inline `height: "955px"` that took three rounds to find) immediately.

4. **Snapshot before risky changes.** "Copy the current HTML (HyperText Markup Language) file to a `-before-scoring-rework` copy, then make the change." If the change is bad, you have a clean rollback.

5. **Be honest about scope creep.** I asked for editable scores, then editable people, then drag-and-drop quadrants, then a font-size bump, then a scoring formula change. Each was fine individually, but the cumulative effect was that the file's complexity grew faster than its organization. By turn 25 I had `!important` overrides stacked three deep. A periodic "refactor what we have before adding more" pass would have helped.

---

# The Output (What Actually Ships)

What I got out of this build and that I can share with you:

- [`Brain Dashboard - Shareable.html`](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/cyberbrain-deepdives/Brain%20Dashboard%20-%20Shareable.html): same as v3 but with all personal data scrubbed (generic project, people, and task names) so it can be shared publicly. This is the file linked from Step 8 of the main guide.

Features that ended up in the final cut:

- Three views (Today, Kanban, Matrix) plus a Settings panel and Token sheet
- Click-to-open detail panel as a 50vw fixed overlay
- Three close paths: X button, click outside, Esc, or click the same task
- Editable impact (1 to 5), effort (1 to 5), energy (low/med/high), due date, time estimate, tags, people
- "Add new person" inline (auto-generates initials and a color)
- 0 to 100 score, recomputes live from impact + urgency + quadrant + fit
- Drag-and-drop between quadrants in the Matrix view (score recomputes after move)
- Drag-and-drop between columns in Kanban (status updates)
- Quadrant labels: Important & Urgent / Important / Urgent / Neither (no more Q1/Q2/Q3/Q4 mystery codes)
- Detail panel text bumped 1.5x via `font-size: 1.5em` on the overlay container, so all `em`-based children scale with it

---

# Known Limitations

- **Desktop only.** Cowork artifacts run on the desktop app. There is no mobile dashboard view. On mobile, tasks are managed through Claude via voice or text commands in Dispatch. Different interface, same underlying vault data.
- **Checkbox write-back.** If a task's markdown body contains checkbox items (`- [ ] subtask`), toggling them in the detail panel is UI-only. The toggle does not write back to the vault. This is a known limitation that has not been addressed yet.
- **Requires Obsidian running.** Like everything in the MCP stack, the dashboard only works when Obsidian is open on your desktop. If Obsidian is closed, the dashboard loads but cannot pull any data.

---

# Reference: How It Works Under the Hood

If you are planning to fork the dashboard or build a similar Cowork artifact, here are the technical details worth knowing.

## Data flow

```
Page load
  -> Call obsidian_list_notes to discover all files in 08-todo/
  -> For each file: call obsidian_get_note (format: full) to read frontmatter + body
  -> Parse the YAML (a human-readable data format) frontmatter and markdown body
  -> Render all three views

User edits a field
  -> Update the local task object in memory
  -> Recalculate the score
  -> Call obsidian_replace_in_note to write the change to the vault
  -> Re-render the affected views
```

## MCP tools used

The dashboard only needs three MCP tools:

- `obsidian_list_notes`: discovers all task files in `08-todo/`
- `obsidian_get_note` (format: "full"): reads each task's frontmatter and body
- `obsidian_replace_in_note`: writes edits back to the vault

That is it. The simplicity is intentional. Fewer tool dependencies means fewer failure points.

## Key JavaScript functions

| Function | What It Does |
|----------|-------------|
| `recomputeScore(t)` | Recalculates the 0-100 score from impact, effort, quadrant, and urgency. Saves updated score to the vault. |
| `vaultUpdateField(task, field, value)` | Regex-replaces a single frontmatter field in the vault file. |
| `vaultUpdateArray(task, field, arr)` | Rewrites an entire YAML array line (for tags and people). |
| `saveScoreFields(task)` | Batch saves impact, effort, energy, and priority_score in one MCP call. |
| `inlineEditCell(t, field, opts)` | Creates a click-to-edit inline text field for due date and time estimate. |
| `editableDotsScale(t, field, max, mode)` | Renders a clickable 1-5 dot scale for impact and effort. |
| `editableEnergyDots(t)` | Renders a clickable low/medium/high energy selector. |
| `collectAllPeople()` | Gathers unique names from all tasks to populate the people picker dropdown. |

## How to get the starter template running

The `Brain Dashboard - Shareable.html` file is the starter template linked from Step 8 of the main guide. It is the same as v3 but with all personal data scrubbed, so you can use it as a starting point without seeing my actual stuff.

1. Download [`Brain Dashboard - Shareable.html`](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/cyberbrain-deepdives/Brain%20Dashboard%20-%20Shareable.html) from the repo to your computer (save it somewhere you can find again, like your Downloads folder).
2. Open the Claude Desktop app and switch to Cowork mode.
3. Open the Cowork project that is already connected to your Obsidian vault (the one you set up in Step 2 of the main guide). If you do not have one yet, set that up first or the dashboard will not have any data to read.
4. Drag the HTML file into the chat window and type: "Use this HTML to build me a task dashboard as a Cowork artifact."
5. Claude will create a pinned artifact from the HTML. You will see a new artifact appear in the right-hand sidebar.
6. Click the artifact to open the dashboard. It will pull live data from your vault on first load.

**What success looks like:** The Today's Focus view shows tasks with `focus_date` = today, the Kanban board shows your tasks distributed across status columns, and the Priority Matrix shows tasks in their Eisenhower quadrants. If the dashboard loads but shows no tasks, check that Obsidian is open and that you actually have task files in `08-todo/` with the proper extended schema.

From there, iterate. Tell Claude what you want changed (different colors, different layout, additional features) and it updates the artifact. The starter template is a starting point, not a final product.

---

# The Meta-Lesson

The most surprising thing about this whole process: **Claude is not a vending machine where you put in a prompt and get out a finished product.** It is a junior designer with a fast pencil and infinite patience. The quality of what you get out is governed almost entirely by:

- How clearly you stated the goal
- How quickly you spotted regressions
- How willing you were to say "no, do it again, look at the screenshot"
- How honest you were about what was actually working

That last one is the hardest. It is tempting to accept "good enough" because the AI sounds confident and you are three turns deep into a thread. Resist it. The version of the tool you do not actually want to open every day is the version that ate four hours of your life and produced nothing.

The dashboard I am using now took maybe 30 turns of conversation. About 8 of those turns were where the real progress happened. The other 22 were finding bugs, recovering from regressions, and discovering that yes, the AI did secretly add an `!important` somewhere and did not tell me.

That ratio, about 1 in 3 turns making real forward progress, feels about right for serious work with current AI tools. Plan for it. Do not be surprised by it. And keep the version copies.

---

*This is the final deep dive in the dashboard series. Return to the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Building%20a%20Cyberbrain.md) for the full system overview.*
