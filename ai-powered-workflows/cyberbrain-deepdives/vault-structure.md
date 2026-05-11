>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Vault Structure and Why Each Folder Exists

*Companion to [Building a Cyberbrain: Step 1 - Set Up Your Vault](../building-a-cyberbrain-guide.md#step-1-set-up-your-vault)*

---

# Why Folder Structure Matters More Than You Think

Most people start a knowledge base by creating notes and dumping them wherever feels right. A week later, they have 40 files in a flat list with names like "meeting notes," "ideas," and "stuff to remember." A month later, they stop using it because finding anything takes longer than just re-doing the research.

The folder structure is not about organization for the sake of neatness. It is about retrieval. Every folder in this vault exists to answer one question: when the AI (Artificial Intelligence) searches for something later, where should it look first?

If you get this wrong, everything downstream suffers. Your AI will misfile entries. Your scheduled tasks will scan the wrong folders. Your searches will return noise instead of signal. The vault becomes a junk drawer with a search bar - exactly the problem you were trying to solve.

If you get this right, the AI knows where to look before it even starts searching. A question about a task? Check `08-todo/`. A question about a person? Check `02-people/`. A question about what you decided last month? Check `03-decisions/`. The folder structure is a routing table for retrieval.

---

# The Full Hierarchy, Folder by Folder

Here is the complete vault structure with every folder explained:

```
your-vault/
|
|-- 00-inbox/
|   |-- mobile/
|   |-- desktop/
|
|-- 01-projects/
|   |-- project-alpha/
|   |-- project-beta/
|   |-- project-gamma/
|
|-- 02-people/
|
|-- 03-decisions/
|
|-- 04-facts/
|
|-- 05-procedures/
|
|-- 06-ideas/
|
|-- 07-areas/
|   |-- finances/
|   |-- health/
|   |-- learning/
|
|-- 08-todo/
|   |-- archived/
|   |-- daily/
|
|-- AI/
|   |-- sessions/
|   |-- daily-briefs/
|   |-- weekly-reviews/
|
|-- _system/
|   |-- taxonomy.md
|   |-- schema.md
|   |-- changelog.md
|
|-- CLAUDE.md
```

---

## `00-inbox/` - The Staging Area

**What it does:** This is where every new capture lands before it has been classified. Nothing stays here permanently. It is a holding pen.

**Why it matters:** Without a dedicated inbox, raw captures end up scattered across your vault. You end up with unstructured notes sitting in project folders alongside properly classified entries, and your AI can't tell the difference. The inbox creates a clean separation between "stuff that just arrived" and "stuff that has been processed."

**How it works:** The inbox has two subfolders:

- `mobile/` - Captures from your phone via the Dispatch app (voice notes, screenshots, photos, text)
- `desktop/` - Quick captures from your desktop sessions

When the morning briefing runs, it scans both subfolders and proposes classifications for anything sitting there. You confirm, and the AI moves the entry to the correct folder. The inbox should be empty (or nearly empty) after each review cycle.

**Common mistake:** Using the inbox as permanent storage. If captures sit in the inbox for weeks, you have a classification backlog that will snowball. The system is designed so that inbox items get processed within 24 hours - either by you in real time or by the morning briefing.

---

## `01-projects/` - Active Ventures and Initiatives

**What it does:** Each subfolder represents one active project. All knowledge entries, decisions, conversations, and references tied to a specific project live here.

**Why it matters:** Projects are the primary axis of your knowledge base. When you ask "what do I know about Project Alpha?" the AI looks here first. Without project-level separation, entries from different initiatives bleed together and retrieval becomes noisy.

**How to customize it:** Replace the example names with your actual projects. Use lowercase slugs with hyphens: `side-hustle`, `day-job`, `app-idea`, `consulting-gig`. Each slug should match a project key in your taxonomy (more on that in the [Taxonomy and Schema deep dive](./taxonomy-schema.md)).

**What goes here:** Anything tied to a specific, time-bound initiative. Meeting notes about that project, decisions you made, research you collected, insights you had. If it belongs to a project, it goes in that project's folder.

**What does not go here:** Tasks (those go in `08-todo/`), people profiles (those go in `02-people/`), and general knowledge that applies across projects (that goes in `04-facts/`).

**Common mistake:** Creating too many project subfolders. If a project has fewer than 5 entries, it probably doesn't need its own folder yet. Let it live in the parent `01-projects/` folder until it grows. You can always restructure later.

---

## `02-people/` - Relationship CRM (Customer Relationship Management)

**What it does:** Stores structured profiles for everyone you interact with professionally (and personally, if you want). Each person gets one note with YAML (a human-readable data format used for structured metadata) frontmatter tracking the relationship.

**Why it matters:** Relationships are context. When the AI processes a meeting note that mentions "Sarah," it links to Sarah's profile. When you ask "when did I last talk to the team at that partner company?" the AI cross-references people entries with conversation entries. Without structured people data, the AI has no way to connect information across interactions.

**What goes here:** One markdown file per person. The file includes structured metadata (who they are, their role, which projects they're connected to, how you met, last interaction date) and freeform notes about the relationship.

**Common mistake:** Only creating people entries for close contacts. The system works best when you also track occasional contacts - that vendor you talked to once, the advisor who gave you a useful insight, the recruiter who reached out. These are exactly the relationships you'll forget about without a system.

---

## `03-decisions/` - Cross-Project Decision Log

**What it does:** A dedicated log for decisions that span multiple projects or don't belong to a single project.

**Why it matters:** Decisions are one of the highest-value types of knowledge, and they're the easiest to forget. You remember that you decided something, but not what you decided, or why, or what the alternatives were. A decision log solves this by capturing the chosen option, the rationale, the date, and who was involved.

**What goes here:** Decisions that affect more than one project, strategic choices, and any decision where you want to remember the reasoning later. Project-specific decisions can go in either `01-projects/` or `03-decisions/` - pick the one that makes more sense for how you'll search for it later.

**Common mistake:** Not logging decisions at all. Most people only log tasks and facts. Decisions are the connective tissue between them. When something goes wrong six months later and you need to understand why you chose a particular path, the decision log is what saves you.

---

## `04-facts/` - Stable Reference Information

**What it does:** Stores information that is relatively stable over time: metrics, definitions, constraints, specifications, reference data.

**Why it matters:** Facts are the building blocks your AI uses to ground its answers. When you ask "what's the contract term with that vendor?" or "what are the specs for the product?" the AI pulls from here. Without a dedicated facts folder, stable reference information gets buried in project folders alongside transient notes.

**What goes here:** Anything that's true for a meaningful period and doesn't belong to a single project. Industry benchmarks, company policies, product specifications, contract terms, technical constraints.

**Common mistake:** Putting everything in facts. If information has an expiration date measured in days, it's probably not a fact. If it's about a decision, it goes in `03-decisions/`. If it's about a procedure, it goes in `05-procedures/`. Facts are for things that stay true.

---

## `05-procedures/` - Playbooks and How-Tos

**What it does:** Stores step-by-step processes, playbooks, and repeatable workflows.

**Why it matters:** Procedures are the answers to "how do I do this again?" questions. They're different from facts (which are static information) and decisions (which are one-time choices). Procedures are reusable instructions.

**What goes here:** How to set up a new project folder. How to run the quarterly review. How to onboard a new team member. How to configure a specific tool. Any process you've done more than once and might need to do again.

**Common mistake:** Writing procedures that are too vague. A good procedure has specific steps that someone (or an AI) could follow without additional context. "Set up the project" is not a procedure. "Create a new subfolder in 01-projects/, add the project key to taxonomy.md, create the first entry using the schema template" is a procedure.

---

## `06-ideas/` - Unvalidated Concepts

**What it does:** A parking lot for ideas that don't have a home yet. These are concepts you want to capture but haven't committed to pursuing.

**Why it matters:** Ideas are fragile. If you don't capture them immediately, they disappear. But if you try to classify them into a project before they're ready, you pollute your project folders with half-formed thoughts. The ideas folder gives them a place to exist without requiring commitment.

**What goes here:** "What if we..." thoughts. Product concepts. Business ideas. Creative angles. Research questions you want to explore someday. Anything that sparked interest but isn't actionable yet.

**Common mistake:** Never reviewing ideas. The ideas folder is not a graveyard. The weekly review includes a prompt to scan for ideas that have matured into something actionable. If an idea sits untouched for months, either promote it to a project or archive it.

---

## `07-areas/` - Life Domains

**What it does:** Stores knowledge related to ongoing life domains that are not time-bound projects.

**Why it matters:** Not everything you track is a project. Your finances, your health, your learning goals - these are ongoing areas of life with no end date. They need their own space so they don't clutter project folders.

**How areas differ from projects:** Projects are time-bound initiatives with a start and end. Areas are ongoing domains you maintain indefinitely. "Launch the product" is a project. "Manage my finances" is an area. This distinction matters because projects get archived when they're done, but areas persist forever.

**Default subfolders:** `finances/`, `health/`, `learning/`. Add whatever life domains matter to you. Some people add `home/`, `social/`, `career/`, `hobbies/`.

**Common mistake:** Making areas too granular. You don't need a subfolder for every possible life domain. Start with 3 or 4 and add more only when a domain accumulates enough entries to justify its own folder.

---

## `08-todo/` - Task Tracking

**What it does:** Every task in the system lives here as an individual markdown file with extended YAML frontmatter (urgency, importance, impact, effort, due dates, scoring).

**Why it matters:** Tasks are the actionable layer of your knowledge base. The morning briefing, evening review, weekly review, and dashboard all read from this folder. If tasks are scattered across project folders, the automated systems can't find them.

**Subfolders:**

- `archived/` - Done tasks older than 7 days get moved here by the morning briefing and weekly review. This keeps the active task list clean without losing history.
- `daily/` - Auto-generated daily focus plans. Each day gets a file (`YYYY-MM-DD.md`) with the morning plan and evening review appended to it.

**Common mistake:** Creating tasks without the full extended schema. A task file that only has a title and status is missing the metadata that makes scoring and prioritization work. Impact, effort, urgency, importance, quadrant - these fields are what the scoring formula uses. Skip them and your morning briefing has nothing to rank.

---

## `AI/` - The AI's Workspace

**What it does:** This is where the AI writes its own outputs: session summaries, daily briefs, and weekly reviews.

**Why it matters:** Separating AI-generated content from your knowledge entries keeps the vault clean. You always know that content in `01-projects/` or `04-facts/` is human-confirmed knowledge, while content in `AI/` is the AI's own operational output.

**Subfolders:**

- `sessions/` - Session summaries written when a Cowork session ends (if configured in your CLAUDE.md session protocol)
- `daily-briefs/` - The scannable morning brief generated by the morning briefing scheduled task
- `weekly-reviews/` - The full weekly audit report

**Common mistake:** Treating AI-generated briefs as ground truth. Daily briefs and weekly reviews are summaries and recommendations. They reflect the AI's interpretation of vault data at that point in time. If something looks off in a brief, check the source entries directly.

---

## `_system/` - Operating Documents

**What it does:** Houses the core operating files that define how the entire system works: the taxonomy, the schema, and the changelog.

**Why it matters:** These are the files your AI reads to know how to classify, structure, and file information. They're the rules of the game. Without them, your AI has no shared vocabulary and no template to follow.

**Contents:**

- `taxonomy.md` - The controlled vocabulary: project keys, knowledge types, life areas, source kinds, task status pipeline. See the [Taxonomy and Schema deep dive](./taxonomy-schema.md).
- `schema.md` - The YAML frontmatter template for memory entries and extended task entries. Defines every field the AI should populate.
- `changelog.md` - A running log of changes to the taxonomy over time. When you add a project, rename a type, or change a status value, log it here. This is how you (and the AI) track how the classification system evolves.

**Common mistake:** Forgetting to update `_system/` files when things change. If you start a new project but don't add it to the taxonomy, the AI will either invent a label or misclassify entries under the wrong project. Keep these files current.

---

## `CLAUDE.md` - The Agent Constitution

**What it does:** This is the system prompt that every session and every scheduled task reads first. It defines who you are, how the vault works, what rules the AI must follow, and the three operating modes (intake, recall, task management).

**Why it lives at the vault root (not in `_system/`):** CLAUDE.md needs to be the first thing the AI finds. Placing it at the root of the vault makes it the default starting point. Files in `_system/` are referenced by CLAUDE.md, but CLAUDE.md itself needs to be at the top level for discoverability.

**Why it matters:** Without CLAUDE.md, every session starts from zero. The AI has no rules, no modes, no knowledge of your vault structure. CLAUDE.md is what makes behavior consistent across sessions and scheduled tasks. It is the single most important file in the system. See the [Writing an Effective CLAUDE.md deep dive](./claude-md.md) for the full breakdown.

---

# The Inbox Pattern: How Information Flows Through the Vault

The core pattern is simple: everything enters through `00-inbox/`, gets classified, and moves to the right folder. Nothing bypasses the inbox unless you're creating an entry directly in a session where the AI classifies it in real time.

```
Raw capture arrives (Dispatch, desktop, paste, voice)
  --> Lands in 00-inbox/mobile/ or 00-inbox/desktop/
    --> AI classifies: project, type, topic, tags, people
      --> You confirm the classification
        --> Entry moves to the correct folder with full metadata
```

This pattern exists because classification is the most critical step. If the AI misfiles something, you lose it. By routing everything through the inbox and requiring confirmation, you build trust in the system and catch errors early. Once you're confident the AI is classifying correctly, you can start trusting it to propose placements without as much scrutiny. But the inbox pattern gives you an audit trail during the trust-building phase.

---

# Obsidian Sync: Why It Matters for the Full Loop

If you're only using the vault on desktop, you can skip Obsidian Sync. But if you're using Dispatch for mobile capture (and you should be - it's the fastest way to feed the system), you need Sync.

Here's why: when you capture a voice note on your phone and the AI processes it on your desktop, the resulting entry gets written to the vault on desktop. Obsidian Sync propagates that entry to all connected devices. Without Sync, your mobile Obsidian wouldn't see entries created on desktop, and your desktop wouldn't see files created from mobile captures until you manually moved them.

**Setup:** Obsidian Settings > Core Plugins > enable Sync > create a remote vault > connect. It's $4-8/month and uses end-to-end encryption so your data is encrypted in transit and at rest. Obsidian never has access to your unencrypted content.

**What to sync:** Everything. There's no reason to exclude folders. The vault is small (markdown files and YAML frontmatter), so sync is fast even on slow connections.

---

# How to Customize This for Your Use Case

The folder structure above is what I use. Your version will differ based on what you track. Here are the most common customizations:

**Adding more project folders:** Just create a subfolder in `01-projects/` and add the project key to your taxonomy. The AI will start classifying entries to it immediately.

**Adding more life areas:** Create subfolders in `07-areas/` for whatever domains you want to track. If you're a student, you might add `courses/` and `research/`. If you're a freelancer, you might add `clients/` and `invoicing/`.

**Adding a CRM-heavy structure:** If relationship tracking is a big part of your workflow, you might add subfolders to `02-people/` by category: `partners/`, `team/`, `advisors/`, `vendors/`.

**Removing folders you don't need:** If you don't track procedures, delete `05-procedures/`. If you don't use life areas, delete `07-areas/`. The system works with fewer folders - just update your taxonomy and CLAUDE.md to reflect the change.

The only folders I would not remove are `00-inbox/`, `08-todo/`, `AI/`, and `_system/`. These are structural to how the automated systems work.

---

# Common Mistakes

**Flat structure with no hierarchy.** Putting every note in one folder and relying on search. This works for 20 notes. It does not work for 200. The folder hierarchy is a pre-filter that narrows search scope before the AI even starts looking.

**Too many subfolders.** Going three or four levels deep creates navigation overhead and makes classification harder. Two levels is the sweet spot for most people: top-level folder (the category) and one subfolder (the project or area).

**Inconsistent naming.** Mixing `Project Alpha`, `project-alpha`, `projectAlpha`, and `alpha` in different places. Pick a convention (lowercase slugs with hyphens) and stick to it across folder names, taxonomy keys, and file names.

**Not updating the structure as projects change.** When a project ends, archive its folder. When a new project starts, create its folder and add it to the taxonomy. A stale folder structure leads to misfiles because the AI is working with an outdated map.

**Treating the vault as a dump.** The vault is structured storage, not a backup drive. Don't put PDFs, images, or large binary files in it. Those should live in cloud storage with a reference entry in the vault pointing to them. Keep the vault lightweight: markdown files with YAML frontmatter.

---

*Next: [Taxonomy and Schema Design](./taxonomy-schema.md) - how to build the controlled vocabulary and entry templates that make classification and retrieval actually work.*
