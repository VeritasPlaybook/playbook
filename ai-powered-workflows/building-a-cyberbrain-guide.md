>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Building a Cyberbrain: A Step-by-Step Guide to an AI-Augmented Second Brain

---

# Why I Built This

I found myself drowning. Not in water, but in context.

I run multiple ventures. At any given moment I'm context-switching between product strategy, partnership negotiations, hiring conversations, financial models, research rabbit holes, and the thousand small decisions that pile up when you're building things simultaneously. My actual human memory couldn't keep up. I'd have a critical insight during a phone call on Tuesday, and by Thursday I couldn't remember which project it belonged to, let alone the specifics. Important details were leaking out of my brain faster than I could capture them.

Then I thought about something that had been rattling around in my head for years: cyberpunk. Ghost in the Shell. The idea of a "cyberbrain," a second brain wired directly into your consciousness that stores, retrieves, and augments everything you know. In those worlds, the human isn't replaced by technology. The human is *amplified* by it. Memory becomes perfect. Context becomes infinite. You focus on thinking, deciding, and creating while the system handles remembering.

I realized I could actually build this. Not with neural implants, but with tools that exist right now. An AI model (Claude) that can read, write, classify, and recall. A local knowledge base (Obsidian) that stores everything as structured files I own. An integration layer (MCP, or Model Context Protocol) that connects the two. A mobile capture app (Dispatch) that lets me dump thoughts from my phone in five seconds. And scheduled automations that maintain the whole system while I sleep.

So I built it. And it 10x'd both my memory and my ability to hold context across everything I'm working on. I offload to the system so I can hyperfocus as a human being, fully augmented by AI. This guide shows you exactly how to build the same thing.

---

# Why This Works

This system works because it mirrors how your brain actually wants to operate.

Your brain is brilliant at making connections, recognizing patterns, and generating ideas. It is terrible at storing and retrieving specific details on demand. You have an insight during a phone call on Tuesday, and by Friday you can't remember which project it belonged to, who said it, or what you decided to do about it. The details leak. The more you're juggling, the faster they leak.

The natural response is to capture more. Write it down. Save the screenshot. Bookmark the link. And most people do this already, in some form. But capturing isn't the problem. The problem is that raw captures are useless without structure. A pile of unsorted notes is just a junk drawer with a search bar. You know the information is in there somewhere, but finding it when you need it takes so long that you end up just re-researching from scratch.

This system solves that by putting AI in the middle. You capture fast, in whatever form is most natural in the moment: a voice note while you're walking, a screenshot from your phone, a pasted conversation, a photo of a whiteboard. That's all you do. The AI handles the part humans consistently fail at: classifying, structuring, tagging, filing, and linking the information so it can be recalled later. It builds the metadata you would never bother to write yourself. It asks "which project is this for?" and "who was involved?" and "what type of knowledge is this?" and files it in the right place with the right labels.

Then it closes the loop. Automated maintenance keeps the system alive without you touching it. A morning briefing scores your priorities. An evening review closes out the day. A weekly audit catches drift. And when you ask "what do I know about X?" weeks or months later, the AI retrieves the structured entries and gives you an answer grounded in your own stored knowledge, not its training data and not a vague memory of something you maybe wrote down somewhere.

No single traditional tool does all of this. Note apps store but don't process. AI chat tools process but don't persist. Manual knowledge management systems persist but require you to do the tedious structuring work that you'll eventually stop doing. This system chains them together into a loop where each piece compensates for the weaknesses of the others.

---

# How This Compares to What You Might Already Use

**vs. note-taking apps (Notion, Evernote, Apple Notes, Google Keep):**
These are great at capturing and storing. They are bad at structuring, classifying, and retrieving with context. You end up with hundreds of notes you never look at again because finding the right one is harder than just re-doing the work. This system adds the AI processing layer that turns raw captures into structured, searchable, interconnected knowledge entries.

**vs. AI chat tools without persistence (ChatGPT, Claude, Gemini used in standalone conversations):**
These are great at processing and reasoning. But every conversation starts from zero. You can't say "remember what we discussed about that partnership three weeks ago" because the AI doesn't have access to your past context. This system gives AI a persistent knowledge base it can read from and write to, so your context accumulates over time instead of resetting every session.

**vs. manual PKM systems (Obsidian, Zettelkasten, Logseq without AI):**
These are great at structured storage if you do the work. The problem is you have to do the work. Writing frontmatter, tagging, linking, filing, reviewing, archiving. It's a part-time job. Most people start strong and stop within a month because the maintenance overhead kills the habit. This system automates the tedious parts (classification, filing, maintenance, scoring) so the only thing you have to do is capture.

**A note on the landscape:** This is what works for me today. The AI productivity space is moving fast, and there may be tools out there now or coming soon that do parts of this as well or better. I'm not claiming this is the only way. I'm sharing what I built, how it works, and why, so you can take what's useful and adapt it.

---

# When and How to Use This

The system handles anything you want to remember, in whatever form is easiest for you in the moment. Here are real examples of how I use it:

**You're in a meeting and someone says something important.**
You pull out your phone, open Dispatch, and record a 10-second voice note: "Call with the manufacturer - they can't hit the Q3 timeline, pushing to October, need to rethink the launch sequence." The AI transcribes it, classifies it as a decision tied to the right project, tags the people involved, and files it. Two weeks later when you're planning the launch, you ask "what did we decide about the timeline?" and the AI pulls up that exact entry with full context.

**You find an article or a conversation thread with useful information.**
Screenshot it. Send it to Dispatch. The AI extracts the key information, identifies what type of knowledge it is (fact, reference, insight), tags it, and files it. You don't have to write a summary. You don't have to decide where it goes. You just capture and move on.

**You're working on something and have a thought you don't want to lose.**
Voice note. Text note. Whatever's fastest. "Idea: what if we used the same onboarding flow for both products instead of building two?" Five seconds. The AI structures it as an idea, links it to the relevant project, and it shows up in your next morning briefing if it scores high enough on priority.

**You have a document, a PDF, a research paper, or a long email you want to extract the key points from.**
Send it to the AI. It reads the whole thing, extracts the vital information, structures it with metadata, and files it in your knowledge base. You get the essence without having to re-read the full document every time you need it.

**You have a conversation with someone (AI or human) and want to save the important parts.**
Paste the transcript or the key quotes. The AI parses out the decisions, action items, facts, and insights, classifies each one separately, and files them in the right places. One conversation can generate multiple structured entries across different projects.

**Optional: augmenting your captures with AI-driven follow-up questions.**
When you save something, the AI doesn't have to just file it passively. You can pair this system with a [context prompt](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md) that tells the AI to ask you follow-up questions before filing: "Who else was involved? What's the deadline? How does this relate to what you decided last week?" This enriches the entry with context you might not have included on your own, making future retrieval even more precise. Completely optional, but powerful if you want to go deeper.

The pattern across all of these is the same: capture in whatever way is fastest for you, let the AI do the structuring and filing, and trust that you can retrieve it later because the metadata is solid.

---

# What This System Actually Does

The cyberbrain is a closed loop. Every component feeds the next, and the system cycles continuously:

**Capture** - On your phone, you grab whatever you need to remember. A voice note about a meeting. A screenshot of something interesting. A photo of a whiteboard. A quick text thought. It takes five seconds. The capture app sends it to your AI automatically.

**Process** - Your AI receives the raw capture and does the heavy lifting. It extracts the content (transcribes voice, reads images, parses text), classifies it against your personal taxonomy (which project? what type of knowledge? who was involved?), structures it into a formatted entry with metadata, and proposes where to file it.

**Store** - After you confirm, the structured entry lands in the correct folder in your knowledge base with full metadata: project tags, people mentioned, related entries, confidence level, timestamps. It's now searchable and retrievable.

**Maintain** - Automated tasks run on a schedule without you lifting a finger. Every morning, the system scores your tasks and builds your daily focus plan. Every evening, it closes out the day, defers unfinished work, and previews tomorrow. Every week, it runs a full audit: stale tasks, misfiles, priority drift, taxonomy gaps.

**Visualize** - A live dashboard pulls fresh data from your knowledge base every time you open it. Three views: today's focus, a kanban board, and a priority matrix. You can drag tasks between statuses or quadrants, edit metadata inline, and everything writes back to the knowledge base in real time.

**Retrieve** - When you ask "what do I know about X?" or "who was at that meeting?" or "what did we decide about Y?", your AI searches the knowledge base, retrieves the relevant structured entries, and generates an answer grounded in your actual stored knowledge, not its training data.

Then back to **Capture**. The loop never stops.

---

# What You'll Need

**A note on tool choices:** This guide is written for Claude (Anthropic's AI) because that's what I use and what this system was built on. The underlying concept - AI-powered capture, classification, storage, maintenance, and retrieval - is not locked to Claude. You could likely adapt this to work with GPT-5.x, Gemini, or another frontier model that supports tool integrations. Similarly, I chose Obsidian as the storage layer because it's local-first, markdown-based, and has strong plugin support, but the architecture could work with other structured storage systems. I'm writing what I know and what I've tested. Adapt as you see fit.

| Item | Cost | Required? |
|------|------|-----------|
| Obsidian (desktop + mobile) | Free | Yes |
| Obsidian Sync (E2E encrypted cross-device sync) | $4-8/month | Yes |
| Claude Desktop app (Cowork mode) | Free (requires Claude subscription) | Yes |
| Claude Pro or Max subscription | Subscription required | Yes |
| Node.js (needed for the MCP server install) | Free | Yes |
| Obsidian MCP (Model Context Protocol) server | Free (open source) | Yes |
| Obsidian Local REST API plugin | Free | Yes |
| Dispatch app (mobile capture) | Free (included with Claude) | Yes |

**Total incremental cost beyond your Claude subscription: $4-8/month** (Obsidian Sync only).

**Technical comfort level:** You don't need to be a developer. If you can install apps, copy-paste configuration, and follow step-by-step instructions, you can build this. The hardest part is the initial MCP setup, and I walk through it below. Node.js is only needed to install the MCP server - you won't be writing any code.

**Time investment:** Plan for a weekend afternoon to get the core system running (Steps 1-6). The scheduled tasks and dashboard (Steps 7-8) can come after you've used the basics for a few days and understand the flow.

---

# The Steps

---

## Step 1: Set Up Your Vault

**Why this matters:** The vault is your filing cabinet. Without a deliberate folder structure, your knowledge base becomes a junk drawer within a week. Every folder has a purpose, and the structure tells your AI where things go.

**What to do:**

1. Install Obsidian on your desktop.
2. Create a new vault. Pick a location you won't accidentally move or delete.
3. Create this folder structure inside the vault:

```
your-vault/
|
|-- 00-inbox/                    # Everything lands here first
|   |-- mobile/                  # Captures from your phone
|   |-- desktop/                 # Quick captures from desktop
|
|-- 01-projects/                 # Active projects and initiatives
|   |-- project-alpha/           # (your projects go here)
|   |-- project-beta/
|   |-- project-gamma/
|
|-- 02-people/                   # Relationship tracking (CRM)
|
|-- 03-decisions/                # Cross-project decision log
|
|-- 04-facts/                    # Stable reference info
|
|-- 05-procedures/               # How-tos, playbooks, processes
|
|-- 06-ideas/                    # Ideas without a home yet
|
|-- 07-areas/                    # Life domains (non-project)
|   |-- finances/
|   |-- health/
|   |-- learning/
|
|-- 08-todo/                     # Task tracking
|   |-- archived/                # Done tasks older than 7 days
|   |-- daily/                   # Auto-generated daily focus plans
|
|-- AI/                          # Your AI's workspace
|   |-- sessions/                # Session summaries
|   |-- daily-briefs/            # Auto-generated morning briefs
|   |-- weekly-reviews/          # Auto-generated weekly reviews
|
|-- _system/                     # Operating docs
|   |-- taxonomy.md              # Controlled vocabulary
|   |-- schema.md                # Entry templates
|   |-- changelog.md             # Taxonomy changes over time
|
|-- CLAUDE.md                    # Agent constitution (system prompt)
```

4. Customize the `01-projects/` subfolders for your actual projects. Use lowercase slugs (e.g., `side-hustle`, `day-job`, `app-idea`).

5. Set up Obsidian Sync so your vault stays in sync across devices. Go to Obsidian Settings > Core Plugins > enable Sync > create a remote vault > connect. This is required so that files written by your AI on desktop are readable on mobile, and captures from your phone are available to your AI. ($4-8/month, E2E encrypted.)

> **[Deep Dive: Vault Structure and Why Each Folder Exists](./deep-dives/vault-structure.md)**

---

## Step 2: Set Up Claude Desktop and Cowork

**Why this matters:** Cowork is the mode in Claude's desktop app where your AI can read and write files, run scheduled tasks, and connect to external tools like Obsidian through MCP. Without this, your AI has no way to interact with your vault. You need to install the app, start a Cowork project, and point it at your vault folder.

**What to do:**

1. Download and install the [Claude Desktop app](https://claude.ai/download) if you haven't already.
2. Open Claude Desktop and switch to Cowork mode.
3. Create a new Cowork project and select your Obsidian vault folder as the working directory. This gives Claude direct access to read and write files in your vault.
4. Verify the connection by asking Claude to list the files in your vault folder. If it can see your folder structure from Step 1, you're connected.

From this point on, you'll be working inside Cowork for all remaining steps. Claude can help you create the taxonomy, schema, and CLAUDE.md files directly in your vault.

---

## Step 3: Create Your Taxonomy and Schema

**Why this matters:** The taxonomy is the controlled vocabulary your AI must use when classifying anything. Without it, your AI invents inconsistent labels and your knowledge base becomes unsearchable. The schema is the template for every entry. Together, they are what make future retrieval actually work.

**What to do:**

1. Create `_system/taxonomy.md` in your vault. This file defines:

   - **Projects:** A table listing each project key, full name, and status (active/paused/archived)
   - **Knowledge types:** What kind of entry it is: decision, fact, conversation, reference, task, procedure, insight, question, person, idea
   - **Life areas:** Your non-project domains (finances, health, learning, etc.)
   - **Source kinds:** How the information arrived: screenshot, voice_note, meeting_note, web_clip, written_note, document, etc.
   - **Task status pipeline:** backlog > planned > in-progress > blocked > done > archived

2. Create `_system/schema.md` in your vault. This file defines the YAML (a human-readable data format) frontmatter template that every knowledge entry uses:

```yaml
---
id: mem-YYYY-MM-DD-NNN
project: [project key from taxonomy, or "personal"]
topic: [subject within the project]
type: [type key from taxonomy]
summary: [1-2 sentence plain English summary]
source_kind: [from taxonomy]
created_at: [ISO-8601 timestamp]
tags: [array]
people: [array]
confidence: [high | medium | low]
status: [active | archived | superseded]
---
```

   Task entries use an extended schema that adds fields for urgency, importance, Eisenhower quadrant, impact/effort scores, due dates, energy level, and recurrence.

3. Create `_system/changelog.md` as an empty file. You'll log taxonomy changes here over time so you can track how your classification system evolves.

> **[Deep Dive: Taxonomy and Schema Design](./deep-dives/taxonomy-schema.md)**

---

## Step 4: Write Your CLAUDE.md

**Why this matters:** CLAUDE.md is the single most important file in the system. It's the agent constitution: the system prompt that every session and every automated task reads first. It defines who you are, how the vault works, what rules your AI must follow, and the three operating modes (intake, recall, task management). Without it, your AI has no instructions and your system has no consistency.

**What to do:**

1. Create `CLAUDE.md` in the root of your vault.
2. Define these sections:

   - **Who you are:** Your ventures, roles, and what you track. This gives your AI context about you as a person.
   - **Vault structure:** The folder map from Step 1 so your AI knows where everything lives.
   - **Operating rules:** The non-negotiable rules your AI must follow. Key ones include: never invent facts, never write without confirmation, always consult the taxonomy before classifying, all knowledge goes to the vault (never to the AI's internal memory).
   - **Three operating modes:**
     - **INTAKE MODE:** Triggered by "remember this" or "save this." AI extracts content, builds a structured candidate using the schema, proposes placements with confidence scores, and waits for your confirmation before writing.
     - **RECALL MODE:** Triggered by questions like "what do I know about X?" AI searches the vault, retrieves relevant entries, and generates an answer grounded in your stored knowledge.
     - **TASK MANAGEMENT MODE:** Triggered by "I need to..." or "new task:" or "done with..." Handles natural-language task creation, status updates, and the automated review sequences.
   - **Session protocols:** What your AI should read when a session starts and what it should write when one ends.

3. Keep CLAUDE.md as a living document. You'll refine it as you use the system and discover what rules you need.

> **[Deep Dive: Writing an Effective CLAUDE.md](./deep-dives/claude-md.md)**

---

## Step 5: Connect MCP to Obsidian

**Why this matters:** MCP (Model Context Protocol) is the integration layer that gives your AI direct read/write access to your Obsidian vault. Without this connection, your AI can't search, read, create, or update notes. This is the glue that makes everything work.

**What to do:**

1. If you don't have Node.js installed, download and install it from [nodejs.org](https://nodejs.org). You need this to install the MCP server. Pick the LTS (Long Term Support) version.
2. In Obsidian, go to Settings > Community Plugins > Browse. Search for "Local REST API" by Adam Coddington. Install and enable it.
3. In the plugin settings, copy the API key. Note the default URL: `https://127.0.0.1:27124`.
4. Install the MCP server that wraps this REST API into tools your AI can call:

```bash
npm install -g obsidian-mcp-server
```

5. Configure the MCP server in your Claude Desktop config. On Windows, edit `%APPDATA%\Claude\claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": ["obsidian-mcp-server"],
      "env": {
        "OBSIDIAN_API_KEY": "YOUR_API_KEY_FROM_PLUGIN",
        "OBSIDIAN_BASE_URL": "https://127.0.0.1:27124",
        "OBSIDIAN_VERIFY_SSL": "false",
        "OBSIDIAN_ENABLE_CACHE": "true"
      }
    }
  }
}
```

6. Restart Claude Desktop. Open a new conversation and ask Claude to list its MCP tools and search your vault for any file. If the connection works, Claude will find your files.

**Important:** Obsidian must be open on your desktop for the MCP connection to work. If Obsidian is closed, all MCP calls fail. This is a known constraint.

> **[Deep Dive: MCP Setup, Tools, and Troubleshooting](./deep-dives/mcp-setup.md)**

---

## Step 6: Set Up Dispatch (Mobile Capture)

**Why this matters:** You will not use Obsidian on your phone. The mobile app is fine for reading, but the capture experience is too slow when you're on the move. You need to grab a thought in five seconds, not navigate folders and write frontmatter. Dispatch solves this by letting you voice-note, screenshot, photograph, or type a quick thought and send it to your AI automatically.

**What to do:**

1. Install the Dispatch app on your phone.
2. Connect it to your Claude account.
3. Start capturing. Dispatch supports:
   - **Voice notes:** Speak a thought, Dispatch transcribes it
   - **Screenshots:** Screenshot anything on your phone, send it
   - **Photos:** Snap a whiteboard, receipt, business card, anything
   - **Text:** Type quick notes

4. When your AI receives a Dispatch capture on the desktop side, it runs INTAKE MODE from your CLAUDE.md: extracts the content, classifies it, structures it, proposes placements, and waits for your confirmation before writing to the vault.

This creates a clean ETL (Extract, Transform, Load) pipeline:

```
Raw capture (voice/photo/screenshot/text)
  --> AI extracts and structures it
    --> Classified entry with full metadata
      --> Written to the correct vault folder
```

The quality of your future retrieval depends entirely on how well the ingestion side structures things. The taxonomy, schema, and classification process from Steps 2-3 are what make this work.

> **[Deep Dive: The Dispatch Pipeline and RAG (Retrieval-Augmented Generation) Ingestion](./deep-dives/dispatch-pipeline.md)**

---

## Step 7: Build Your Scheduled Tasks

**Why this matters:** Without automation, your vault goes stale within a week. Tasks pile up, inbox captures sit unprocessed, done items never get archived, and your daily priorities drift. Scheduled tasks are the heartbeat of the system. They keep everything alive without you lifting a finger.

**What to do:**

Set up three scheduled tasks in Cowork (Claude's desktop app) using the `/schedule` skill. Each task gets a prompt that reads your CLAUDE.md first, inheriting all your rules and modes.

**1. Morning Briefing (daily, e.g. 6:00 AM)**

This task runs an automated sequence every morning:
- Archives done tasks older than 7 days
- Flags stale in-progress tasks (no activity in 5+ days)
- Checks the inbox for unprocessed captures and proposes classifications (never auto-files)
- Scores all open tasks using a priority formula based on impact, effort, urgency, due dates, and focus dates
- Generates a "Top 3-5" daily focus plan with rationale
- Writes a daily note and a scannable daily brief

**2. Evening Review (daily, e.g. 9:00 PM)**

This task closes out the day:
- Checks which tasks from the morning plan were completed
- Identifies unfinished items and defers them to tomorrow (blocked tasks go to a separate list)
- Previews tomorrow's top candidates
- Appends an evening review section to today's daily note

**3. Weekly Review (e.g. Sunday 7:00 PM)**

This task runs a full vault audit:
- Summarizes completed and carried-over tasks by project
- Flags stale backlog (14+ days inactive)
- Checks for priority drift (quadrant labels that don't match urgency/importance)
- Verifies recurring tasks have next instances scheduled
- Counts new notes by project and type
- Flags potential misfiles and suggests taxonomy updates
- Writes a structured weekly review

After a week of running, your vault accumulates daily briefs, daily notes with morning plans and evening reviews, and weekly audit reports. You'll have a scannable summary waiting for you every morning and a clean close-out every night.

> **[Deep Dive: Scheduled Task Design and Prompt Engineering](./deep-dives/scheduled-tasks.md)**

---

## Step 8: Build Your Dashboard

**Why this matters:** A knowledge base you can't see is a knowledge base you won't use. The dashboard turns your vault's task data into a visual, interactive interface. It's not a static export; it's a live application that reads from and writes back to your vault every time you open it.

**What to do:**

Build a Cowork artifact (a persisted HTML page in Claude's sidebar) that calls your MCP tools on load to pull live task data. The dashboard should include:

**Three views:**

1. **Today's Focus** - Tasks with a focus date of today or due soon, sorted by priority score, with quick actions to mark done or defer.
2. **Kanban Board** - Drag-and-drop columns for each status in your pipeline (backlog, planned, in-progress, blocked, done). Dragging a task between columns writes the status change back to the vault.
3. **Priority Matrix** - An Eisenhower quadrant grid (urgent+important, important but not urgent, urgent but not important, neither). Drag-and-drop between quadrants updates the urgency/importance flags and recalculates the priority score. All changes write back to the vault.

**Editable detail panel:**

Click any task card to open a detail overlay where you can edit metadata inline: impact, effort, energy level, due date, time estimate, tags, people. All edits save immediately to the vault.

**Starter template:** I've included a [ready-to-use dashboard HTML](./brain-dashboard-starter.html) that you can load as a Cowork artifact to get started immediately. It has all three views, drag-and-drop, editable detail panels, and vault write-back already wired up. Use it as-is or as a foundation to customize for your own workflow and design preferences.

**Building approach:** Work iteratively with Claude to build on top of the starter template or create your own from scratch. My first version looked rough and I didn't want to open it. Investing in a proper design system (color palette, typography, spacing) made it something I actually use daily. Either way, start functional and then refine.

> **[Deep Dive: Dashboard Iteration Story (v1 to v3.5)](./deep-dives/dashboard-iteration.md)**

---

# The Full Loop

Once all seven steps are in place, the system runs as a continuous cycle:

```
Capture (Dispatch, phone)
  --> Process (AI, ETL/ingestion)
    --> Store (Obsidian vault, structured markdown)
      --> Maintain (scheduled tasks, automated)
        --> Visualize (dashboard, live)
          --> Retrieve (RAG, on demand)
            --> back to Capture
```

Every component feeds the next. Nothing exists in isolation. The system is only as good as the weakest link in the chain, which is why the ingestion and classification step matters as much as the retrieval side.

---

# What I Learned

**The knowledge base is the filing cabinet, not the interface.** I never open Obsidian to find things. The AI is my interface. Obsidian is just storage. This simplifies everything.

**The schema is the product.** The YAML frontmatter, the taxonomy, the classification process: these aren't bureaucracy. They're what make future recall actually work. Without structured metadata, you're just grepping through a folder of text files.

**Scheduled tasks are the heartbeat.** Without the morning briefing and evening review, the vault goes stale within a week. Automation keeps it alive and keeps you honest about what you're actually working on.

**Design matters for tools you use daily.** If the dashboard looks rough, you won't open it. Invest in making it something you want to look at.

**Mobile capture must be frictionless.** If capturing a thought takes more than five seconds, you won't capture. Dispatch solved this. One tap for a voice note, one tap for a screenshot.

**The MCP layer is the glue.** Everything depends on the AI being able to read and write to Obsidian. Keep it simple: one MCP server, not five. If that connection breaks, the whole system stops.

**You will iterate.** The first version of everything (the taxonomy, the CLAUDE.md, the dashboard, the scheduled task prompts) will be rough. That's expected. The system improves as you use it and discover what's missing. The important thing is to start capturing and classifying, because you can always restructure later. You can't retroactively capture what you never recorded.

---

# Deep Dives (Coming Soon)

These companion guides go deeper into the design decisions, tradeoffs, and iteration stories behind each step:

| Guide | What It Covers |
|-------|---------------|
| [Vault Structure](./deep-dives/vault-structure.md) | Why each folder exists, how the hierarchy supports retrieval, and how to customize it for your use case |
| [Taxonomy and Schema Design](./deep-dives/taxonomy-schema.md) | How to build a classification system that scales, the full task schema with scoring formulas, and common taxonomy mistakes |
| [Writing an Effective CLAUDE.md](./deep-dives/claude-md.md) | The full agent constitution breakdown: operating rules, mode definitions, session protocols, and how to evolve it over time |
| [MCP Setup and Troubleshooting](./deep-dives/mcp-setup.md) | Complete MCP tool reference, SSL configuration, connection debugging, and what we tried and dropped |
| [The Dispatch Pipeline and RAG Ingestion](./deep-dives/dispatch-pipeline.md) | How raw captures become structured knowledge entries, the ETL flow in detail, and how ingestion quality drives retrieval quality |
| [Scheduled Task Design](./deep-dives/scheduled-tasks.md) | Full prompt engineering for each scheduled task, the scoring formulas, and how to tune the automation to your workflow |
| [Dashboard Iteration Story](./deep-dives/dashboard-iteration.md) | From rough v1 to polished v3.5: the design feedback loop, the technical architecture, drag-drop write-back, and the structuredContent fix |
