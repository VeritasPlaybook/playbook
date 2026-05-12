>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: Scheduled Task Design and Prompt Engineering

*Companion to [Building a Cyberbrain: Step 7 - Build Your Scheduled Tasks](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Building%20a%20Cyberbrain.md#step-7-build-your-scheduled-tasks)*

---

# Why Automation Is Non-Negotiable

Without automated maintenance, your vault goes stale within a week. Here is what happens:

- Done tasks sit in `08-todo/` forever, cluttering the active task list
- In-progress tasks you forgot about never get flagged
- Inbox captures pile up unprocessed because you didn't get around to classifying them
- You stop checking the vault because opening it means confronting a mess
- The whole system dies

Scheduled tasks are the heartbeat of the system. They run without you lifting a finger: every morning, every evening, every week. They archive, flag, score, plan, review, and clean. They keep the vault alive so that when you do interact with it, everything is current and actionable.

---

# How Scheduled Tasks Work in Cowork

Cowork (Claude's desktop app) has a built-in scheduling system. You create tasks using the `/schedule` skill, and each task runs on a cron schedule.

**How it works:**

1. You define a task with an ID, a description, a cron expression, and a prompt
2. The prompt becomes a `SKILL.md` file stored at `%APPDATA%\Claude\Scheduled\{task-id}\SKILL.md`
3. On each scheduled run, Cowork spawns a new Claude session that executes the SKILL.md prompt autonomously
4. The session runs, does its work, and finishes. You can inspect the session transcript later.

**Key concepts:**

- **Task ID:** A slug that identifies the task (e.g., `second-brain-morning-briefing`). Must be unique.
- **Cron expression:** Standard cron syntax. `0 6 * * *` means "daily at 6:00 AM." `0 21 * * *` means "daily at 9:00 PM." `0 19 * * 0` means "Sundays at 7:00 PM."
- **SKILL.md:** The prompt file. This is the full set of instructions the AI (Artificial Intelligence) follows on each run. Think of it as the script for an autonomous agent.

---

# The Three Scheduled Tasks

## 1. Morning Briefing

**Schedule:** Daily at 6:00 AM (or whenever you want your day to start)
**Task ID:** `second-brain-morning-briefing`

This is an 11-step automated sequence. Every step is explicit in the SKILL.md prompt, and every step reads from or writes to specific vault locations.

### Step 1: LOAD OPERATING RULES

Read `CLAUDE.md` and `_system/schema.md` to load all rules, modes, and scoring formulas.

**Why this is first:** Every subsequent step depends on the rules in CLAUDE.md. Without loading them first, the AI might use wrong formatting, wrong folder paths, or wrong scoring formulas.

### Step 2: SYNC

List all files in `08-todo/` (excluding `archived/`). Note any status changes since yesterday's daily note.

**What this catches:** Tasks that were updated outside of the scheduled system - manually edited, updated during a Cowork session, or modified by another scheduled task.

### Step 3: ARCHIVE

Find done tasks with `completed_at` older than 7 days. Move them to `08-todo/archived/`. Limit: 10 per run.

**Why the limit:** Archiving too many files in one run can be slow and error-prone. 10 per day keeps it manageable. If you have a backlog of done tasks, they'll get archived over a few days.

### Step 4: STALE CHECK

Find in-progress tasks not updated in 5+ days. Add `stale: true` to their frontmatter.

**What this does:** Flags tasks you might have forgotten about. The stale flag shows up in the daily brief so you can decide to either push forward, defer, or drop the task.

### Step 5: INBOX CHECK

List all files in `00-inbox/mobile/` and `00-inbox/desktop/`. For each item, propose a classification: type, project, topic, suggested folder.

**Critical constraint: this step NEVER auto-files.** It proposes classifications only. You confirm or correct them during your morning review. This was a deliberate design decision - I wanted to build trust in the classification system before enabling any automation. The inbox check surfaces what's waiting, but the human makes the final call.

### Step 6: CONTEXT LOAD

Read `08-todo/context.md` for current project priorities and constraints.

**What `context.md` is:** A short file you maintain that tells the AI what matters right now. "This week's priority is the product launch." "I'm blocked on the partnership until Thursday." "Ignore everything in project-gamma until next month." The morning briefing uses this to weight its recommendations.

### Step 7: FOCUS DATE PULL

Find all open tasks where `focus_date` matches today's date.

**What this means:** If you explicitly set a task's focus_date to today (either manually or because the evening review deferred it to today), it gets pulled into the daily plan automatically. Focus dates are commitments.

### Step 8: PRIORITY SCORING

Compute `daily_score` for all open tasks using the formula:

```
daily_score = priority_score + deadline_pressure + focus_boost
```

Where:
- `priority_score = (impact * 2) + ((6 - effort) * 1) + (urgency_bonus * 3) + (importance_bonus * 2)` (range 2-20)
- `deadline_pressure` = 5 if overdue, 3 if due today, 2 if due tomorrow, 1 if due this week, 0 otherwise
- `focus_boost` = 10 if focus_date = today

Sort all open tasks by daily_score, descending.

### Step 9: GENERATE TOP 3-5

Select the top 3-5 tasks from the scored list. For each, write a 1-sentence rationale explaining why it ranked high and referencing any relevant context from `context.md`.

**Why 3-5 and not more:** You can realistically focus on 3-5 things in a day. A list of 15 priorities is not a priority list - it's a backlog. The briefing forces prioritization by capping the daily plan.

### Step 10: WRITE DAILY NOTE

Write the daily plan to `08-todo/daily/YYYY-MM-DD.md` with sections:
- **Today's Focus** - The top 3-5 tasks with rationale
- **Inbox Review Needed** - Items awaiting classification (from Step 5)
- **Stale Flags** - In-progress tasks flagged as stale (from Step 4)

### Step 11: WRITE DAILY BRIEF

Write a concise, scannable brief to `AI/daily-briefs/YYYY-MM-DD.md`. This is the quick-glance version - just the task list and any alerts, no detailed rationale.

---

## 2. Evening Review

**Schedule:** Daily at 9:00 PM (or whenever your workday ends)
**Task ID:** `second-brain-evening-review`

A 7-step sequence that closes out the day.

### Step 1: LOAD OPERATING RULES

Read `CLAUDE.md` and `_system/schema.md`.

### Step 2: LOAD TODAY'S PLAN

Read today's daily note from `08-todo/daily/YYYY-MM-DD.md` and extract the focus list.

**Edge case handling:** If no daily note exists (the morning briefing didn't run or was skipped), search for tasks with `focus_date = today` instead.

### Step 3: COMPLETED TODAY

Search for tasks with `completed_at` = today. List them grouped by project.

### Step 4: UNFINISHED ITEMS

From the focus list, identify tasks still in-progress or planned with `focus_date` = today.

### Step 5: DEFER UNFINISHED

For each unfinished task: update `focus_date` to tomorrow using `obsidian_manage_frontmatter`.

**Critical constraint:** Blocked tasks are NOT deferred. They go to a separate "Blocked - needs attention" list. Deferring a blocked task is pointless - it will still be blocked tomorrow. Instead, blocked tasks get surfaced explicitly so you can take action on the blocker.

**Scope constraint:** Only defers tasks that were on today's explicit focus list. Does not bulk-defer all open tasks. If a task wasn't on today's plan, it stays wherever it is.

### Step 6: TOMORROW PREVIEW

Compute `daily_score` for all open tasks. List the top 3 candidates for tomorrow.

### Step 7: WRITE EVENING REVIEW

Append an evening review section to today's daily note (`08-todo/daily/YYYY-MM-DD.md`) with:
- Completed today (by project)
- Deferred to tomorrow
- Blocked - needs attention
- Tomorrow's preview

---

## 3. Weekly Review

**Schedule:** Sunday at 7:00 PM (or your preferred weekly review time)
**Task ID:** `second-brain-weekly-review`

A 12-step full vault sweep. This is the deepest audit in the system.

### Step 1: COMPLETED THIS WEEK

Tasks done in the last 7 days, grouped by project. This gives you a sense of momentum and shows where your effort went.

### Step 2: CARRIED OVER

Tasks with `focus_date` this week that are still not done. These are commitments you made but didn't finish.

### Step 3: STALE BACKLOG

Backlog or planned tasks with no activity in 14+ days. These are potential dead weight. Either promote them (set a focus_date), drop them, or acknowledge they're long-term parking.

### Step 4: PRIORITY DRIFT CHECK

Verify that quadrant labels match the urgent/important booleans. Catches drift where a task was marked Q1 (urgent + important) but one of the booleans says otherwise. This happens when you manually adjust a quadrant on the dashboard but forget to update the underlying flags.

### Step 5: Q1 CAP CHECK

If more than 5 tasks are in Q1 (urgent + important), flag for re-evaluation. Having too many Q1 tasks means either your urgency calibration is off, or you genuinely have too many crises - either way, it needs attention.

### Step 6: UPCOMING DUE DATES

All open tasks due in the next 14 days. A two-week horizon gives you time to prepare.

### Step 7: RECURRENCE CHECK

Verify that recurring tasks have a next instance scheduled (`recurrence_next` is set and in the future). If a recurring task completed but the next instance wasn't created, flag it.

### Step 8: ARCHIVE

Move done tasks older than 7 days to `08-todo/archived/`. Limit: 20 per run (higher than the daily limit since this runs weekly).

### Step 9: MEMORY REVIEW

Count all notes added this week, grouped by project and type. This shows your capture patterns: are you capturing mostly for one project? Mostly one type? Are there projects with no captures at all?

### Step 10: MIS-FILE CHECK

Flag notes where:
- The `type` doesn't match the folder (e.g., a `task` entry sitting in `04-facts/`)
- The `project` key isn't in the taxonomy (might be a typo or an unregistered project)

### Step 11: TAXONOMY SUGGESTIONS

Identify emerging patterns:
- Topics appearing frequently with no taxonomy entry
- Inconsistent tags (e.g., both `pricing` and `price-strategy` appearing)
- Missing knowledge types (entries being forced into the wrong type repeatedly)

**Critical constraint:** This step only suggests. It never makes changes to the taxonomy. You review the suggestions and decide what to update.

### Step 12: WRITE WEEKLY REVIEW

Write the full structured review to `AI/weekly-reviews/YYYY-MM-DD.md`.

---

# Vault Output Structure

After a week of running, your vault accumulates:

```
AI/daily-briefs/
  2026-05-05.md
  2026-05-06.md
  ...
  2026-05-11.md

AI/weekly-reviews/
  2026-05-11.md

08-todo/daily/
  2026-05-05.md    (morning plan + evening review)
  2026-05-06.md
  ...
  2026-05-11.md
```

Each daily brief is a scannable summary you read to start your day. Each daily note has both the morning plan and the evening review appended to it. The weekly review is a comprehensive audit.

---

# Prompt Engineering Tips

Writing the SKILL.md prompts for scheduled tasks is the most important prompt engineering in the system. Here's what I learned:

**Be explicit about what to read first.** The first line of every SKILL.md should be: "Read CLAUDE.md and _system/schema.md." If you don't specify this, the AI might skip the operating rules and produce output that doesn't follow your conventions.

**Define the output format precisely.** Don't say "write a daily brief." Say "write a daily brief to `AI/daily-briefs/YYYY-MM-DD.md` with sections: Today's Focus (top 3-5 tasks with rationale), Inbox Items (count and status), Stale Flags (list), Format: scannable, no paragraphs, one line per task."

**Set limits.** "Archive done tasks" without a limit means the AI might try to archive 50 files in one run. "Archive done tasks, limit 10 per run" keeps the operation bounded and predictable.

**Handle edge cases explicitly.** What if there's no daily note from this morning? What if the vault is unreachable? What if there are zero open tasks? The prompt should address these: "If no daily note exists for today, search for tasks with focus_date = today instead." "If the vault is unreachable, write an error note and exit."

**Keep each step atomic.** Each step in the sequence should do one thing. "SYNC - list all files in 08-todo/" is clear. "SYNC - list all files in 08-todo/, check for changes, archive old ones, and flag stale tasks" is four steps crammed into one, and the AI is more likely to skip something.

**Test with dry runs.** Before setting a scheduled task live, run the prompt manually in a Cowork session. Watch what the AI does at each step. Correct any missteps, update the SKILL.md, and run it again. Once it produces clean output manually, schedule it.

---

# Key Design Constraints

**The morning briefing never auto-files inbox items.** It proposes classifications, but you confirm. This is a trust-building mechanism. As you use the system and see that classifications are consistently accurate, you might choose to relax this constraint. But start with manual confirmation.

**The evening review only defers tasks on today's explicit focus list.** It does not touch tasks that weren't planned for today. This prevents scope creep where the evening review starts rearranging your entire backlog.

**All prompts read CLAUDE.md first.** This ensures every scheduled run inherits your operating rules, formatting preferences, scoring formulas, and mode definitions. If you update CLAUDE.md, the changes take effect on the next scheduled run automatically.

**Scheduled tasks handle vault-unreachable gracefully.** If Obsidian isn't running when a task fires, the task writes an error note and exits instead of producing garbage. No data is at risk - the task just doesn't do its work until the next run.

---

# Common Mistakes

**Not testing prompts before scheduling.** Running a scheduled task for the first time on a cron schedule means you won't see the output until it runs. Test manually first. Fix issues. Then schedule.

**Prompts that are too vague.** "Review my tasks and write a summary" gives the AI too much room to interpret. Spell out every step, every file path, every output format. Scheduled tasks run autonomously - there's no human in the loop to course-correct.

**Not including the CLAUDE.md read instruction.** The most common failure mode: the scheduled task runs but doesn't follow your operating rules because it never loaded them. Always start with "Read CLAUDE.md."

**Setting the archive limit too high.** Archiving 50 files in one run creates long-running sessions that are more likely to hit timeouts or errors. Keep limits conservative (10 per daily run, 20 per weekly run) and let the task chip away at the backlog over multiple runs.

**Forgetting about time zones.** Cron expressions use the system's local time. If your machine's clock is set to UTC but you live in Eastern Time, `0 6 * * *` runs at 1:00 AM your time, not 6:00 AM. Make sure your cron times match your actual schedule.

---

*Next: [Dashboard Iteration Story (v1 to v3.5)](./dashboard-iteration.md) - how the task dashboard went from rough prototype to a polished daily-use tool.*
