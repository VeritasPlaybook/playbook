>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Writing an Effective CLAUDE.md

*Companion to [Building a Cyberbrain: Step 4 - Write Your CLAUDE.md](../building-a-cyberbrain-guide.md#step-4-write-your-claudemd)*

---

# What CLAUDE.md Is and Why It's the Most Important File

CLAUDE.md is your agent constitution. It is the system prompt that every Cowork session and every scheduled task reads first, before doing anything else. It tells the AI (Artificial Intelligence) who you are, how the vault works, what rules it must follow, and how to behave in different situations.

Think of it as a contract between you and your AI. Without it, every new session starts from zero. The AI has no rules, no context, no knowledge of your vault structure, and no consistency. It will make up behaviors, invent filing conventions, and forget what you told it last time. With CLAUDE.md, every session inherits the same operating rules, the same modes, and the same understanding of your system.

This is not a nice-to-have. It is the single most important file in the entire system. Everything depends on it - the scheduled tasks read it before running, the intake process follows its rules, the recall mode follows its search protocol. If CLAUDE.md is wrong, vague, or incomplete, the entire system drifts.

---

# The Sections: What Goes in CLAUDE.md

A good CLAUDE.md has six core sections. Here's what each one does, why it matters, and what happens if you skip it.

---

## 1. Who You Are

**What it does:** Gives the AI personal context about you - your ventures, your roles, what you track, what matters to you.

**Why it matters:** An AI that knows you're running multiple ventures simultaneously handles context differently than one that thinks you're a student taking notes for one class. The "who you are" section shapes how the AI interprets ambiguous requests, which project to default to, and what level of detail to provide.

**What to include:**
- Your ventures and projects (briefly - the taxonomy has the full list)
- Your role in each (founder, consultant, employee, etc.)
- What you primarily track (decisions, tasks, people, research, all of the above)
- Any context that affects how the AI should assist you (time zone, work style, communication preferences)

**Example structure:**
```
I run [number] ventures simultaneously: [brief list].
My role: [description].
I primarily use this system to track: [what you track].
```

**What happens if you skip it:** The AI treats you as a generic user. It won't know which project you're likely referring to when you say "that meeting yesterday." It won't understand why you need fast capture or why you're tracking so many different domains at once.

---

## 2. Vault Structure

**What it does:** A folder map of the vault so the AI knows where everything lives.

**Why it matters:** Without this, the AI has to search the entire vault for every operation. With the folder map, it knows where to look first. "Save this fact" - the AI knows to go to `04-facts/`. "What's on my plate?" - the AI knows to go to `08-todo/`. The folder map is a routing table.

**What to include:** The full folder hierarchy from the [Vault Structure deep dive](./vault-structure.md), with a one-line description of each folder's purpose. Keep it concise - the AI just needs the map, not the full rationale.

**What happens if you skip it:** The AI will still find files (it can list directories), but it will waste time scanning the wrong folders and occasionally misfile entries because it doesn't know the intended purpose of each location.

---

## 3. Operating Rules

**What it does:** A numbered list of non-negotiable rules the AI must follow in every session and every scheduled task.

**Why it matters:** Rules prevent the most common failure modes. Without explicit rules, AI agents tend to invent facts when they don't know something, act without confirmation, and store information in places you didn't intend.

**The recommended starter set (eight rules):**

1. **Never invent facts.** If you don't know something, say so. Don't fabricate an answer.
2. **Never write without confirmation.** Always propose and wait for approval before writing to the vault.
3. **Memory routing rule:** All knowledge goes to the Obsidian vault, never to Cowork's internal memory system. The vault is the single source of truth. (This is critical. Without it, the AI splits your knowledge between two systems and you lose track of what's stored where.)
4. **Always consult the taxonomy before classifying.** Read `_system/taxonomy.md` before assigning project keys, types, or tags.
5. **Always use the schema template.** Read `_system/schema.md` before creating any new entry.
6. **Never auto-file inbox items.** Propose classifications and wait for confirmation.
7. **Define acronyms on first use.** In any written output, spell out the full term before using shorthand.
8. **Formatting rules.** Whatever formatting preferences you have (no certain punctuation, specific heading styles, etc.).

These eight rules are the complete recommended starter set. They cover the failure modes that show up most often in the first few weeks of running the system. You can add more rules over time as you discover situations the starter set doesn't cover, but you don't need to start with more. CLAUDE.md is a living document, not a finished spec.

**What happens if you skip it:** The AI will occasionally make up information, write to the vault without asking, split knowledge between the vault and its internal memory, and use inconsistent classification. Every one of these problems compounds over time.

---

## 4. Session Start and End Protocols

**What it does:** Defines what the AI should read when a session opens and what it should write when one closes.

**Why it matters:** Session protocols create continuity across conversations. Without them, each session starts from scratch and ends without leaving a trace.

**Session start protocol - what to read on open:**
- CLAUDE.md (itself - to load all rules)
- `_system/taxonomy.md` (current project list and types)
- `_system/schema.md` (entry templates)
- `08-todo/context.md` (current priorities and constraints, if it exists)
- The most recent daily brief from `AI/daily-briefs/` (to know what was planned for today)

**Session end protocol - what to write on close:**
- A session summary to `AI/sessions/` (what was discussed, what was created or modified, what's pending)
- Update any task statuses that changed during the session
- Note any unresolved items for the next session

**What happens if you skip it:** Sessions become isolated events. The AI won't know what was planned for today, what happened in the last session, or what priorities are current. You'll spend the first few minutes of every session re-briefing the AI.

---

## 5. The Three Operating Modes

This is the core of CLAUDE.md. The three modes define how the AI should behave in different situations.

### INTAKE MODE

**Triggered by:** "Remember this," "save this," or any request to store information.

**What the AI does:**
1. **Extract** - Parse the content. If it's a voice note, work from the transcription. If it's a screenshot or photo, run OCR (Optical Character Recognition) to extract text. If it's pasted text, parse the key information.
2. **Structure** - Build a structured candidate using `_system/schema.md`. Fill in every field: id, project, topic, type, summary, source_kind, tags, people, entities, confidence.
3. **Classify** - Assign the project key, type, and tags using the taxonomy. Propose the target folder.
4. **Propose placements** - Present 3 placement options with confidence scores. Example: "Option 1: `01-projects/project-alpha/` as type `decision` (confidence: high). Option 2: `03-decisions/` as type `decision` (confidence: medium). Option 3: `04-facts/` as type `fact` (confidence: low)."
5. **Wait for confirmation** - Do not write anything until the user confirms. This is non-negotiable.

**Why 3 placements?** Because classification is not always obvious. A meeting note might be primarily a decision (goes to `03-decisions/`) or primarily a project update (goes to `01-projects/`). Showing options with confidence scores lets you choose and teaches the AI your preferences over time.

### RECALL MODE

**Triggered by:** Questions like "What do I know about X?" or "Who was at that meeting?" or "What did we decide about Y?"

**What the AI does:**
1. **Search narrowest first** - Start with the most specific location. If the question mentions a project, search that project folder first. If it mentions a person, check `02-people/` first.
2. **Broaden if needed** - If confidence in the answer is below 0.75 (roughly, "I'm not sure this is complete"), expand the search to related folders and then the full vault.
3. **Return the answer** with three things: the answer itself, the source files (so you can verify), and the confidence level. If there are gaps ("I found meeting notes but no decision was recorded"), flag them.

**Why the confidence threshold?** Without it, the AI either gives you the first result it finds (which might be incomplete) or searches the entire vault every time (which is slow and noisy). The graduated search balances speed with thoroughness.

### TASK MANAGEMENT MODE

**Triggered by:** "I need to...," "new task:," "done with...," or any task-related instruction.

**What the AI does:**
- **Natural language task creation:** Extracts the task description, people, project, due date, urgency, and importance from natural language. "I need to review the contract for Project Alpha by Friday - it's urgent" becomes a structured task entry with all fields populated.
- **Status updates:** "Done with the contract review" finds the task and updates status to `done`, fills `completed_at`.
- **Batch operations:** "What's on my plate for Project Alpha?" retrieves and summarizes all active tasks for that project.
- **Review sequences:** The morning briefing, evening review, and weekly review run as task management sequences (detailed in the [Scheduled Tasks deep dive](./scheduled-tasks.md)).

---

## 6. People CRM (Customer Relationship Management) Template

**What it does:** Defines the structured format for entries in `02-people/`.

**Why it matters:** People entries are referenced constantly - every conversation, meeting note, and task that involves someone links back to their profile. A consistent template ensures every person entry has the same fields, making cross-referencing reliable.

**Template structure:**
```yaml
---
id: person-firstname-lastname
type: person
name: [Full Name]
role: [Their role/title]
organization: [Company or affiliation]
relationship: [How you know them - partner, advisor, vendor, team member, etc.]
projects: [Array of project keys they're connected to]
last_contact: [YYYY-MM-DD]
contact_info: [Email, phone, LinkedIn - whatever you track]
tags: [Array]
created_at: [ISO-8601]
status: [active | inactive]
---
```

**What happens if you skip it:** People entries become inconsistent. Some have contact info, others don't. Some track the relationship type, others just have a name. When the AI tries to cross-reference, it can't reliably extract structured data from freeform people notes.

---

# Scoring Formulas in CLAUDE.md

Your CLAUDE.md should include the priority score and daily score formulas so the AI can calculate them consistently. See the [Taxonomy and Schema deep dive](./taxonomy-schema.md) for the full formula breakdown.

Including the formulas directly in CLAUDE.md (rather than only in the schema) ensures that every session and scheduled task has immediate access to them without needing to read a second file. Redundancy here is intentional - these formulas are critical path.

Additionally, include the Eisenhower quadrant definitions:

- **Q1 (Do First):** Urgent AND important. Crises, deadlines, critical problems.
- **Q2 (Schedule):** Important but NOT urgent. Strategic work, planning, skill development. This is where high-value work lives.
- **Q3 (Delegate):** Urgent but NOT important. Interruptions, some emails, some meetings.
- **Q4 (Eliminate):** Neither urgent NOR important. Time-wasters, busywork.

---

# Why CLAUDE.md Should Be a Living Document

Your first CLAUDE.md will be incomplete. That's fine. You'll discover missing rules after the AI does something unexpected. You'll refine modes after you see how the AI interprets your instructions. You'll add protocols after you realize a session-end step is missing.

The important thing is to start with the core sections (vault structure, rules, modes) and iterate. After each session where the AI does something wrong, ask: "What rule would have prevented that?" Then add it.

Some rules I added after the first version:

- The memory routing rule (after discovering the AI was storing knowledge in Cowork's internal memory instead of the vault)
- The "never auto-file" rule (after the AI classified and filed an inbox item without asking)
- The "consult taxonomy first" rule (after the AI invented a project key that wasn't in the taxonomy)
- Formatting rules (after the AI used punctuation styles I didn't want in written outputs)

Each of these came from a real failure. The rules exist because the failure happened and I wanted to prevent it from happening again.

---

# Common Mistakes

**Making CLAUDE.md too long.** If it's 5,000 words, the AI will miss details buried in the middle. Keep each section as concise as possible while being complete. Rules should be one sentence each. Folder descriptions should be one line each. The modes should be procedural (step 1, step 2, step 3), not narrative.

**Forgetting to include the taxonomy reference.** CLAUDE.md should tell the AI to read `_system/taxonomy.md` before classifying anything. Without this instruction, the AI may rely on its own judgment instead of your controlled vocabulary.

**Not defining modes clearly enough.** If the intake mode says "classify the entry" but doesn't say "propose 3 placements with confidence scores and wait for confirmation," the AI will make a single classification and write it without asking. Be explicit about every step, especially the confirmation gates.

**Putting CLAUDE.md in `_system/` instead of the vault root.** The AI looks at the root level first. Burying CLAUDE.md inside a subfolder means it might not be read automatically at session start. Keep it at the root for maximum visibility.

**Not including examples.** Rules are clearer with examples. Instead of "classify entries appropriately," show a sample entry with correct classification. Instead of "propose placements," show what a good proposal looks like. One example is worth five sentences of explanation.

**Treating it as set-and-forget.** CLAUDE.md needs maintenance. When you add a project, update the vault structure section. When you change a rule, update it here. When you add a new mode or protocol, add it. A stale CLAUDE.md is worse than no CLAUDE.md because the AI will follow outdated instructions with confidence.

---

*Next: [MCP Setup, Tools, and Troubleshooting](./mcp-setup.md) - the integration layer that connects your AI to your vault.*
