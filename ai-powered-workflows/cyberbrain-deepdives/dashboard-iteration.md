>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Dashboard Iteration Story (v1 to v3.5)

*Companion to [Building a Cyberbrain: Step 8 - Build Your Dashboard](../building-a-cyberbrain-guide.md#step-8-build-your-dashboard)*

---

# What the Dashboard Is

The dashboard is a Cowork artifact, which means it is a persisted HTML (HyperText Markup Language, the standard format for web pages) page that lives in Claude's sidebar. It is not a static export or a screenshot. It is a live application that calls MCP (Model Context Protocol) tools on every load to pull fresh task data from your Obsidian vault, renders three interactive views, and writes changes back to the vault in real time when you edit anything.

You open it, you see your current tasks across three views, you drag things around or edit metadata inline, and every change persists in the vault. Close it, come back tomorrow, and it pulls fresh data again.

---

# v1: The Rough Start

The first version of the dashboard was functional but ugly. It had:

- A list of tasks pulled from `08-todo/`
- Simple colored badges for status
- Click to expand task details

It worked. You could see your tasks and their statuses. But it looked like a developer prototype - generic colors, poor spacing, no consistent design system. The kind of tool you build to prove the concept works, not the kind of tool you actually want to open every day.

And that's the problem. A task dashboard you don't want to open is a task dashboard you won't open. It becomes shelfware within a week.

---

# The Design Quality Feedback

After seeing v1, I told the AI (Artificial Intelligence) "it kinda looks like shit." Not the functionality, that was fine. The visual design. It felt rough, unfinished, like a homework assignment.

This led to an important realization: iterating on a rough UI (User Interface) in place is a trap. You tweak colors, adjust spacing, nudge fonts, and after 10 rounds of micro-adjustments it still looks like a polished version of something that was never designed. You can't iterate your way from "no design system" to "looks good." You need to start with design intent.

This feedback became a core operating rule: for any future UI work, either get a design spec first, use a design-first workflow, or reference a specific design system. Don't ship rough and iterate. Design first, build second.

---

# The Pivot: Design-First Process

Instead of continuing to tweak v1, we started fresh. I provided design direction - referencing specific apps and aesthetics I liked - and the AI built v3 from a clean design specification.

The result was dramatically better. Not because the functionality changed (it was basically the same three views), but because every visual decision was intentional: the color palette, the typography, the spacing, the card layout, the interaction patterns. It looked like a tool, not a prototype.

**The lesson:** Design matters for tools you use daily. If you're building a dashboard you plan to open every morning, invest in making it something you want to look at. The functional delta between v1 and v3.5 was small. The experiential delta was massive.

---

# v3.5: The Current Dashboard

Deployed 2026-05-03, last updated 2026-05-06. Built as pure vanilla HTML, CSS (Cascading Style Sheets, which control visual styling like colors and layout), and JS (JavaScript, the programming language that makes web pages interactive), with no CDN (Content Delivery Network) dependencies. Uses an oklch color system and Inter Tight font.

## The Three Views

### 1. Today's Focus

Tasks with `focus_date` = today or due soon, sorted by `priority_score`. Each task card shows the title, project, score, and quick-action buttons for Done and Defer.

**Done** marks the task as completed (updates `status` to `done` and sets `completed_at` in the vault). **Defer** pushes the `focus_date` to tomorrow. Both actions write back to the vault immediately via MCP.

This is the view you open first thing in the morning. It answers: "What should I work on today?"

### 2. Kanban Board

Five drag-and-drop columns: backlog, planned, in-progress, blocked, done.

Dragging a task card from one column to another updates the `status` field in the vault. Move a card from "planned" to "in-progress" and the vault file is updated in real time. No save button, no confirmation dialog. Drag, drop, done.

This view answers: "What's the status of everything?"

### 3. Priority Matrix

An Eisenhower quadrant grid:
- **Q1 (Do First):** Urgent + Important
- **Q2 (Schedule):** Important, not urgent
- **Q3 (Delegate):** Urgent, not important
- **Q4 (Eliminate):** Neither urgent nor important

Tasks appear as cards in their quadrant. You can drag a task from Q4 to Q1 and the dashboard updates the `urgent` and `important` booleans in the vault, recalculates the `priority_score`, and re-renders the card in its new position.

A project filter lets you focus the matrix on one project at a time.

This view answers: "Am I working on the right things?"

---

## The Scoring System (0-100 Scale)

The dashboard uses a richer scoring formula than the vault's base priority_score (which ranges 2-20). The dashboard score scales to 0-100:

```
score = impact * 7                                    (0-35)
      + urgency bonus (today=30, soon=20, normal=10)  (10-30)
      + quadrant boost (Q1=20, Q2=15, Q3=10, Q4=0)   (0-20)
      + fit bonus ((impact - effort + 4) * 1.5,       (0-15)
                    clamped 0-15)
```

**Why a different scale?** The vault's 2-20 range is designed for the morning briefing's daily_score calculation, which adds deadline_pressure and focus_boost. The dashboard's 0-100 range gives more visual granularity - a score ring on each task card fills proportionally, so you can see at a glance which tasks score highest.

**Auto-recalculation:** When you change impact, effort, energy, or quadrant on the dashboard, the score recalculates instantly and overwrites `priority_score` in the vault.

---

## The Editable Detail Panel

Click any task card to open a fixed overlay panel (scaled 1.5x for readability). Close it via click-outside, Esc key, or X button.

The panel shows:

- **Full title**
- **Editable metadata grid:**
  - Impact (1-5 clickable dots - click dot 3 to set impact to 3)
  - Effort (1-5 clickable dots)
  - Energy (low/medium/high clickable dots)
  - Due date (click to edit inline)
  - Time estimate (click to edit inline)
  - Tags (add new tags, remove existing ones)
  - People (add/remove with a picker that shows all people across all tasks)
- **Blockers** (what's preventing progress)
- **Related tasks** (linked task IDs)
- **Markdown body** (the task's full description)
- **Score ring** (visual representation of the 0-100 score)

Every edit saves immediately to the Obsidian vault. Change the impact from 3 to 5, and the vault file is updated within a second. No save button needed.

---

## Key Technical Details

### Data Flow

```
Page load
  --> Call obsidian_list_notes to discover all files in 08-todo/
  --> For each file: call obsidian_get_note (format: full) to read frontmatter + body
  --> Parse the YAML frontmatter and markdown body
  --> Render all three views

User edits a field
  --> Update the local task object in memory
  --> Recalculate the score
  --> Call obsidian_replace_in_note to write the change to the vault
  --> Re-render the affected views
```

### The structuredContent Fix

One technical issue worth mentioning: when the dashboard calls MCP tools via `window.cowork.callMcpTool()`, the responses come back wrapped in Cowork's `structuredContent` format. The actual data is nested inside `result` objects, sometimes multiple layers deep.

The dashboard's `extractData()` function handles this by progressively unwrapping:

```javascript
function extractData(response) {
  let data = response;
  if (data.structuredContent) data = data.structuredContent;
  if (data.result) data = data.result;
  // ... further unwrapping as needed
  return data;
}
```

This was not documented anywhere. We discovered it by probing the actual response shapes during the build. If you're building your own Cowork artifacts that call MCP tools, you'll likely run into the same wrapping and need similar unwrapping logic.

### Key JavaScript Functions

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

### MCP Tools Used by the Dashboard

The dashboard only needs three MCP tools:

- `obsidian_list_notes` - Discovers all task files in `08-todo/`
- `obsidian_get_note` (format: "full") - Reads each task's frontmatter and body
- `obsidian_replace_in_note` - Writes edits back to the vault

That's it. The simplicity is intentional. Fewer tool dependencies means fewer failure points.

---

## Known Limitations

**Desktop only.** Cowork artifacts run on the desktop app. There's no mobile dashboard view. On mobile, tasks are managed through Claude via voice or text commands in Dispatch - a different interface but the same underlying vault data.

**Checkbox write-back.** If a task's markdown body contains checkbox items (`- [ ] subtask`), toggling them in the detail panel is UI-only. The toggle doesn't write back to the vault. This is a known limitation that hasn't been addressed yet.

**Requires Obsidian running.** Like everything in the MCP stack, the dashboard only works when Obsidian is open on your desktop. If Obsidian is closed, the dashboard loads but can't pull any data.

---

# The Starter Template

The `brain-dashboard-starter.html` file is included in the POC (Proof of Concept) publish folder and linked from Step 8 of the main guide. This is a ready-to-use dashboard that has all three views, the scoring system, the editable detail panel, and vault write-back already wired up.

**How to get it running:**

1. Download `brain-dashboard-starter.html` from the POC publish folder to your computer (save it somewhere you can find again, like your Downloads folder).
2. Open the Claude Desktop app and switch to Cowork mode.
3. Open the Cowork project that is already connected to your Obsidian vault (the one you set up in Step 2 of the main guide). If you don't have one yet, set that up first or the dashboard won't have any data to read.
4. Drag the HTML file into the chat window and type: "Use this HTML to build me a task dashboard as a Cowork artifact."
5. Claude will create a pinned artifact from the HTML. You'll see a new artifact appear in the right-hand sidebar.
6. Click the artifact to open the dashboard. It will pull live data from your vault on first load. If you've already created tasks in Steps 3 through 7 of the main guide, they'll show up across the three views.

**What success looks like:** The Today's Focus view shows tasks with focus_date = today, the Kanban board shows your tasks distributed across status columns, and the Priority Matrix shows tasks in their Eisenhower quadrants. If the dashboard loads but shows no tasks, check that Obsidian is open and that you actually have task files in `08-todo/` with the proper extended schema.

From there, iterate. Tell Claude what you want changed (different colors, different layout, additional features) and it updates the artifact. The starter template is a starting point, not a final product.

---

# The Iteration Mindset

The v1-to-v3.5 journey taught me something important: the first version of any tool in this system will be rough. That's fine. What matters is that you get it working, use it for a few days, identify what's missing or frustrating, and then improve it.

But "iterate" doesn't mean "tweak endlessly." The pivot from v1 to v3 wasn't a gradual evolution - it was a restart with a design-first approach. Sometimes the right move is to throw away the prototype and rebuild from a clean spec. Other times, a few targeted tweaks are all you need.

The signal is whether you're opening the tool. If you stop opening the dashboard, something is wrong - either the data isn't useful or the experience is painful. Fix whichever one it is. A tool you don't use is a tool that doesn't exist.

---

*This is the final deep dive. Return to the [main guide](../building-a-cyberbrain-guide.md) for the full system overview.*
