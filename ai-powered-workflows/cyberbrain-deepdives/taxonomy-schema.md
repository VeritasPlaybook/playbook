>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Taxonomy and Schema Design

*Companion to [Building a Cyberbrain: Step 3 - Create Your Taxonomy and Schema](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Building%20a%20Cyberbrain.md#step-3-create-your-taxonomy-and-schema)*

---

# Why Your AI Needs a Controlled Vocabulary

Here's what happens without a taxonomy: you capture a meeting note and the AI (Artificial Intelligence) tags it as "meeting." Next time, it tags one as "conversation." Then "call notes." Then "discussion." Four entries about the same kind of knowledge, four different labels, and now when you search for all your meeting notes, you only find a quarter of them.

A taxonomy is a controlled vocabulary - a fixed set of labels your AI must choose from when classifying anything. It eliminates inconsistency by constraining the options. Instead of inventing a label each time, the AI picks from the list you defined. "Conversation" is a valid type. "Meeting," "call notes," and "discussion" are not. The AI has to use what's in the taxonomy, period.

This sounds like bureaucracy. It is not. It is the single most important design decision in the system. Your taxonomy and schema are what make future retrieval work. Without them, you are building a pile of notes with inconsistent labels that no search can reliably navigate. With them, every entry speaks the same language and the AI can find anything by querying structured fields.

---

# The Taxonomy: What It Contains

The taxonomy lives at `_system/taxonomy.md` in your vault. It defines five things:

---

## 1. The Project Table

Every active project gets an entry with a key, full name, description, and status.

| Key | Full Name | Description | Status |
|-----|-----------|-------------|--------|
| project-alpha | Project Alpha | Consumer product launch | Active |
| project-beta | Project Beta | Software as a Service (SaaS) platform build | Active |
| project-gamma | Project Gamma | Consulting engagement | Paused |
| personal | Personal | Non-project items | Active |

**How to define your own projects:** Use lowercase slugs with hyphens as keys. These keys are what the AI uses in YAML (a human-readable data format used for structured metadata) frontmatter, not the full name. Keep descriptions to one sentence. Status values: `active`, `paused`, `archived`.

**When a project ends:** Change its status to `archived` in the taxonomy and log the change in `_system/changelog.md`. Don't delete the key - old entries still reference it, and you want to be able to search archived project history.

---

## 2. Knowledge Types

These are the categories of knowledge your system tracks. Each entry in the vault gets exactly one type.

| Type Key | What It Stores | Example |
|----------|---------------|---------|
| `decision` | Chosen option, rationale, date, who was involved | "Decided to push launch to October because the manufacturer can't hit Q3" |
| `fact` | Stable information, metrics, definitions, constraints | "The API rate limit is 1000 requests per minute" |
| `conversation` | Meeting points, stakeholder positions, discussion outcomes | "Call with partner team - they want to co-brand the launch" |
| `reference` | Links, documents, vendor info, external resources | "Product spec PDF from the engineering team" |
| `task` | Action items with owner, due date, status | "Review contract terms by Friday" |
| `procedure` | Repeatable steps, playbooks, processes | "How to submit an expense report" |
| `insight` | Synthesized interpretation, pattern recognition | "Noticing that every project stalls at the handoff stage" |
| `question` | Open issues, research gaps, unknowns | "What's the regulatory status for this product category?" |
| `person` | Who someone is, relationship context | "Sarah Chen - VP of Partnerships at the manufacturer" |
| `idea` | Raw concepts, not yet validated | "What if we bundled both products into one subscription?" |

**Why these ten types and not more:** Ten is enough to meaningfully differentiate entries without creating classification paralysis. Every type serves a different retrieval need. When you ask "what did we decide?" the AI filters on type `decision`. When you ask "who do I know at that company?" it filters on type `person`. More types create more ambiguity about which one to use. Fewer types create less useful retrieval.

**What if something doesn't fit?** If you genuinely can't classify an entry, use the closest type and add clarifying tags. Don't create a new type unless you find yourself repeatedly forcing entries into the wrong category. If that happens, log the new type in the changelog.

---

## 3. Life Areas vs. Projects

This is a distinction that trips people up: areas and projects are not the same thing.

**Projects** are time-bound. They have a start, an end, and a goal. "Launch the product" is a project. "Build the app" is a project. When the project is done, you archive it.

**Areas** are ongoing domains you maintain indefinitely. "Finances" is an area. "Health" is an area. "Learning" is an area. They never finish. They just persist.

The taxonomy lists your life areas separately from projects. Common defaults: `finances`, `health`, `learning`, `home`, `social`. Add whatever fits your life: `career`, `hobbies`, `relationships`, and so on. Entries in `07-areas/` use the area name as a pseudo-project key (meaning the area name fills the same role a project key normally would).

**Why the distinction matters for retrieval:** When you ask "what's happening with my finances?" the AI knows to look in `07-areas/finances/`, not in `01-projects/`. When you ask "what's the status on Project Alpha?" it looks in `01-projects/project-alpha/`. Without the distinction, the AI would have to search everywhere for everything.

---

## 4. Source Kinds

How the information originally arrived. This is tracked so you know the provenance of every entry.

| Source Kind | What It Means |
|-------------|--------------|
| `screenshot` | Screen capture from phone or desktop |
| `pasted_text` | Copied text from a conversation, document, or website |
| `chat_snippet` | Excerpt from an AI or messaging conversation |
| `meeting_note` | Notes from a live meeting or call |
| `web_clip` | Content clipped from a web page |
| `written_note` | Something you wrote from scratch |
| `voice_note` | Transcribed voice recording |
| `document` | Content extracted from a PDF, doc, or other file |

**Why track the source?** Because it affects confidence. A voice note captured while walking might be a rough thought that needs follow-up. A meeting note is typically higher-confidence because it captures something that was discussed and (often) agreed upon. When the AI retrieves entries, the source kind gives it context about how reliable the information might be.

---

## 5. Task Status Pipeline

Tasks move through a defined pipeline. There is no ambiguity about what each status means.

```
backlog --> planned --> in-progress --> blocked --> done --> archived
```

| Status | What It Means |
|--------|--------------|
| `backlog` | Captured but not scheduled. Might do it, might not. |
| `planned` | Committed to doing it. Has a focus_date or due date assigned. |
| `in-progress` | Actively working on it. |
| `blocked` | Can't proceed until something else happens. `blocked_by` field explains what. |
| `done` | Completed. `completed_at` timestamp is set. |
| `archived` | Done and moved to `08-todo/archived/` by the morning briefing or weekly review (after 7 days). |

**Why this specific pipeline?** Because each status triggers different behavior in the scheduled tasks. The morning briefing only scores tasks in `backlog`, `planned`, and `in-progress`. The evening review only defers tasks that were `in-progress` or `planned` with today's focus_date. The weekly review flags `backlog` tasks that haven't been touched in 14+ days as stale. If you add custom statuses, the automated systems won't know what to do with them.

---

# The Schema: The Template for Every Entry

The schema lives at `_system/schema.md`. It defines the YAML frontmatter that every knowledge entry uses.

## The Memory Entry Schema

```yaml
---
id: mem-YYYY-MM-DD-NNN
project: [project key from taxonomy, or "personal"]
topic: [subject within the project]
type: [type key from taxonomy]
summary: [1-2 sentence plain English summary]
source_kind: [from taxonomy]
source_ref: [hint for finding the original - URL, file name, "phone call", etc.]
created_at: [ISO-8601 timestamp, e.g. 2026-05-11T14:30:00]
tags: [array of relevant keywords]
people: [array of names mentioned]
entities: [array of tools, organizations, systems referenced]
confidence: [high | medium | low]
status: [active | archived | superseded]
related_ids: [array of other mem-IDs that connect to this entry]
---
```

**Field-by-field breakdown:**

- **id:** A unique identifier. The format `mem-YYYY-MM-DD-NNN` is a convention, not a requirement. The date prefix makes entries chronologically sortable. The NNN suffix handles multiple entries on the same day.
- **project:** Must match a key from the taxonomy's project table. This is the primary retrieval axis.
- **topic:** A freeform subject within the project. More specific than the project, less structured than a tag. Examples: "pricing strategy," "Q3 timeline," "onboarding flow."
- **type:** Must match a type key from the taxonomy. This is the secondary retrieval axis.
- **summary:** A plain English summary the AI can use for quick retrieval without reading the full body. Keep it to 1-2 sentences.
- **source_kind:** Must match a source kind from the taxonomy. Tracks provenance.
- **source_ref:** A breadcrumb for finding the original source. Could be a URL, a file name, "phone call with Sarah," or "team meeting."
- **created_at:** ISO-8601 timestamp. The AI fills this automatically.
- **tags:** An array of keywords for cross-cutting retrieval. Tags catch things that project and type don't cover. Use them sparingly - 2-5 tags per entry is a good range.
- **people:** Names of everyone mentioned or involved. Feeds cross-referencing with `02-people/` entries.
- **entities:** Tools, organizations, systems, or other non-person entities referenced. Useful for retrieval like "everything involving that vendor."
- **confidence:** How reliable the information is. `high` for confirmed facts and decisions. `medium` for meeting notes and conversations. `low` for rough thoughts and unverified claims.
- **status:** `active` is the default. `archived` for historical entries you don't need in active search. `superseded` for entries replaced by a newer version.
- **related_ids:** Links to other entries. The AI populates this by searching for related entries when writing a new one. This creates a web of connected knowledge.

## Body Sections

Below the YAML frontmatter, the body of a memory entry follows a standard structure:

- **Summary** - The key takeaway in 2-3 sentences
- **Key Points** - The important details, formatted for scanning
- **Decisions** (optional) - What was decided and by whom
- **Action Items** (optional) - What needs to happen next
- **Context** (optional) - Background that helps interpret the entry
- **Raw Appendix** (optional) - The original unprocessed content (full transcript, raw voice note text, etc.)

Not every entry needs every section. A quick fact might only have Summary and Key Points. A rich meeting note might use all six.

---

## The Task Schema (Extended)

Task entries use all the memory entry fields plus an extended set of task-specific fields:

```yaml
---
id: task-YYYY-MM-DD-NNN
project: [project key]
type: task
summary: [what needs to be done]
urgent: [true | false]
important: [true | false]
quadrant: [Q1 | Q2 | Q3 | Q4]
impact: [1-5]
effort: [1-5]
priority_score: [calculated, range 2-20]
due: [YYYY-MM-DD]
focus_date: [YYYY-MM-DD]
time_estimate: ["30m", "2h", "half day"]
energy: [low | medium | high]
context: [desk | phone | errand | meeting | deep-work]
status: [backlog | planned | in-progress | blocked | done | archived]
blocked_by: [description or task ID]
completed_at: [ISO-8601, filled when done]
recurrence: [daily | weekly | biweekly | monthly | quarterly | null]
recurrence_next: [YYYY-MM-DD]
tags: [array]
people: [array]
created_at: [ISO-8601]
---
```

**Key task-specific fields explained:**

- **urgent / important:** Boolean flags for the Eisenhower matrix. These drive the quadrant assignment.
- **quadrant:** The Eisenhower quadrant: Q1 (urgent + important), Q2 (important, not urgent), Q3 (urgent, not important), Q4 (neither). This is set based on the urgent/important booleans but can be overridden.
- **impact (1-5):** How much completing this task moves the needle. 5 = game-changing. 1 = negligible.
- **effort (1-5):** How much work it takes. 5 = massive undertaking. 1 = quick win.
- **priority_score:** Calculated from the formula (see below). Range 2-20. The morning briefing uses this to rank tasks.
- **due:** Hard deadline. The date this must be done by.
- **focus_date:** Soft date. The day you plan to work on this. The morning briefing pulls tasks with today's focus_date into the daily plan.
- **time_estimate:** How long you think it will take. Freeform string.
- **energy:** What energy level this task requires. Helps you match tasks to your state - heavy thinking tasks when you're sharp, low-energy tasks when you're winding down.
- **context:** Where or how you need to do this task. Enables filtering by situation.
- **blocked_by:** What's preventing progress. A freeform description or a reference to another task ID.
- **completed_at:** Timestamp filled when the task is marked done. Used by the archiving system to determine when to move done tasks to `archived/`.
- **recurrence / recurrence_next:** For recurring tasks. The recurrence field defines the cadence. The recurrence_next field is the date of the next instance. The weekly review checks that recurring tasks have a valid next instance.

---

# The Scoring Formulas

## Priority Score (Vault Level, Range 2-20)

This is the base score stored in the vault and used by the morning briefing to rank tasks:

```
priority_score = (impact * 2) + ((6 - effort) * 1) + (urgency_bonus * 3) + (importance_bonus * 2)
```

Where:
- `impact` is 1-5 (so `impact * 2` ranges from 2 to 10)
- `effort` is 1-5 (so `(6 - effort)` ranges from 1 to 5 - lower effort scores higher)
- `urgency_bonus` = 1 if urgent, 0 if not (so the term ranges from 0 to 3)
- `importance_bonus` = 1 if important, 0 if not (so the term ranges from 0 to 2)
- **Total range: 2 to 20**

**Why this formula?** It balances four factors: high-impact tasks rise to the top, low-effort tasks get a slight boost (quick wins), and urgency/importance flags add meaningful bumps without dominating.

## Daily Score (Used by Morning Briefing)

The daily score adds time-sensitive context on top of the base priority score:

```
daily_score = priority_score + deadline_pressure + focus_boost
```

Where:
- `deadline_pressure` = 5 if overdue, 3 if due today, 2 if due tomorrow, 1 if due this week, 0 otherwise
- `focus_boost` = 10 if focus_date = today, 0 otherwise

**Why the focus_boost is 10:** This is deliberately high. If you manually set a focus_date for today, it means you've explicitly decided to work on this task. The system should respect that decision by boosting it above almost everything else. A focus_date is a commitment, not a suggestion.

**Why deadline_pressure is graduated:** Overdue tasks get the biggest bump (5) because they're already late. Due-today gets 3, which is significant but doesn't automatically override a high-impact Q2 task with focus_date set. Due-tomorrow and due-this-week get smaller nudges to bring them into awareness without hijacking the plan.

---

# The Changelog: Tracking Taxonomy Evolution

The changelog lives at `_system/changelog.md`. It's a simple running log:

```markdown
## 2026-05-11
- Added project key `project-delta` (new consulting engagement, status: active)
- Changed `project-gamma` status from active to paused

## 2026-04-28
- Added source_kind `voice_note` (Dispatch voice capture support)
- Renamed type `note` to `conversation` for clarity
```

**Why track changes?** Because the taxonomy is a living document. Projects start and end. You discover that a type doesn't work and rename it. You add a new source kind when you start using a new capture method. Without the changelog, you lose the history of these decisions, and the AI can't tell whether an old entry's labels are current or outdated.

The weekly review includes a step that checks for taxonomy consistency - entries whose project key isn't in the taxonomy, or whose type doesn't match the folder they're in. The changelog gives you context when you encounter those mismatches: "Oh, this entry uses the old type name because we renamed it two weeks ago."

---

# Common Mistakes

**Too many types.** Creating 20+ types because you want precise classification. This backfires because the AI struggles to choose between closely related types, and you end up with inconsistent classifications anyway. Start with the 10 listed above. Only add a new type if you find yourself repeatedly forcing entries into the wrong category.

**Overlapping categories.** Having both "meeting" and "conversation" as types, or both "reference" and "fact." Each type should have a clear, non-overlapping definition. If you can't articulate the difference between two types in one sentence, merge them.

**Not updating the taxonomy as projects change.** Starting three new projects but never adding them to the taxonomy table. The AI will either invent keys or misclassify entries under the wrong project. Every new project needs a taxonomy entry before the first capture.

**Skipping the schema.** Writing entries without YAML frontmatter because it feels like overhead. The frontmatter is what makes retrieval work. Without it, you're back to grepping through text files. The AI fills in the frontmatter automatically - you just need the schema defined so it knows what fields to populate.

**Over-tagging.** Putting 10-15 tags on every entry. Tags should add retrieval value that project and type don't already cover. If an entry is project `project-alpha`, type `decision`, the tag `project-alpha-decision` adds nothing. Use tags for cross-cutting themes: `pricing`, `legal`, `launch-blocker`, `competitor-intel`.

---

*Next: [Writing an Effective CLAUDE.md](./claude-md.md) - the agent constitution that ties everything together and makes your AI behave consistently across sessions.*
