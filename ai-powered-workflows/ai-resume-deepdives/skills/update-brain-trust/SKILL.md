---
name: update-brain-trust
description: Use at the END of any job application thread where the user tailored a resume or cover letter, to ingest the finished application back into their Career Brain Trust. Folds new framings, metrics, and cover letter hooks into the master source-of-truth. Trigger phrases include "update the brain trust", "ingest this into the brain trust", "fold this back into the brain trust", "ingest tailored resume", "log this application", or any phrasing where the user wants to close the loop on a finished application. Always trigger when the user mentions ingesting, updating, folding back, or logging an application, even if the wording differs. Runs a three-phase workflow: ingest the resume, cover letter, and Job Description from thread with confirmation; ask clarifying questions in multi-choice format about new variants and contradictions; then update the brain trust, save copies to Past Resumes, and append an entry to the application log. Do NOT use for tailoring NEW resumes from scratch (that is the resume-builder skill).
---

# Update Brain Trust skill

This skill folds a finished tailored resume and cover letter back into the user's Career Brain Trust at the end of an application thread. It runs after the `resume-builder` skill (or any tailoring conversation) has produced the actual application material.

The workflow has three phases. Follow them in order. Each phase has explicit pauses for the user's input.

**Why this skill exists.** Without a close-the-loop step, every application starts from the same place yesterday's started. New framings discovered in last week's draft are stuck in last week's thread. New metrics do not propagate. Cover-letter hooks for archetypes the user had never encountered are gone the moment the tab closes. This skill folds the new material back into the source of truth so the next application starts smarter.

---

## Overview

```
[End of tailoring thread]
       |
       v
[Phase 1: Ingest] -- pull resume + cover + JD from thread, confirm with the user
       |
       v
[Phase 2: Clarify] -- diff against brain trust child files, flag contradictions, ask the user
       |
       v
[Phase 3: Update] -- apply changes to the right child files, refresh INDEX, save copies, log application, report
       |
       v
[Done]
```

---

## Phase 1: Ingest

### Step 1.1 — Locate the tailored application material in thread context

The tailoring thread will have produced one of these patterns:

- A combined `.docx` saved by the `resume-builder` skill at `[Your Applications folder]/[Company] - [Role].docx` (cover letter on page 1, page break, resume on page 2 and beyond).
- A standalone resume `.docx` or `.md` pasted or uploaded mid-thread.
- A cover letter as a separate file.

Search the conversation context for:

1. The most recent `.docx` file produced or saved by Claude in this thread.
2. Any explicit file paths matching `Applications/`, `Past Resumes/`, or the workspace root.
3. The company name and role title (usually surfaced in the tailoring thread's opening turns).
4. The Job Description (pasted text, URL, or PDF that the tailoring was based on).

### Step 1.2 — Confirm with the user before proceeding

Show the user a preview:

> I found this material in our thread:
>
> **Application file:** `[path]`
> **Company:** `[name]`
> **Role:** `[title]`
> **Resume preview (first 5 lines):** ...
> **Cover letter preview (first 5 lines):** ...
> **Job description:** found or not found
>
> Is this the right material to ingest into the brain trust?

Use the AskUserQuestion tool with copy-paste answer sheet format. Options:

```
Q1: Confirm material to ingest?
A. Yes, this is the right one
B. Wrong file, I will paste or upload the correct one
C. Multiple applications in this thread, I will specify which
```

PAUSE HERE. Wait for confirmation.

If the user says wrong file or cannot find it, ask them to either paste the resume and cover letter text directly into the next message, or give a file path.

### Step 1.3 — Parse the application into resume and cover letter sections

If the source is a combined `.docx`, parse it into two logical sections using `python-docx`:

- **Cover letter section:** content from the top through the page break.
- **Resume section:** content from after the page break through the end.

The page break separator is the `<w:br w:type="page"/>` element.

If the source is two separate files (resume and cover) or pasted text, keep them already separated.

Extract from the resume:

- Positioning paragraph if present
- Role-by-role bullets (mapped to the canonical roles in the brain trust Experience folder)
- Big-number metrics mentioned
- Skills or core competencies block if present

Extract from the cover letter:

- Opener line
- The four bolded reason headers and their elaboration
- Closing line
- Distinctive hooks (the user-specific anecdotes or credentials)

---

## Phase 2: Clarify

### Step 2.1 — Read the brain trust (selective, INDEX-driven)

Brain trust child files live under `[Your Career Brain Trust folder]/`. Selective read; do not load the whole corpus.

1. Read `[Your Career Brain Trust folder]/INDEX.md` first.
2. Read always-load files:
   - `[Your Career Brain Trust folder]/0 How To Use.md`
   - `[Your Career Brain Trust folder]/1 Identity.md`
   - `[Your Career Brain Trust folder]/2 Chronology.md`
   - `[Your Career Brain Trust folder]/5 Skills.md`
   - `[Your Career Brain Trust folder]/6 Achievements.md`
   - `[Your Career Brain Trust folder]/7 Education.md`
   - `[Your Career Brain Trust folder]/Cover Letters/4.0 Patterns.md`
   - `[Your Career Brain Trust folder]/Cover Letters/4.20 Reusable Hooks.md`
3. For each role mentioned in the new resume, read the matching `Experience/3.X [Role].md` file.
4. If a cover letter for this target company already exists in the Cover Letters folder, read it. Otherwise note that a new archetype file will be created in Phase 3.

Note especially:

- `1 Identity.md` Section 1C (positioning statements): see what tagged angles already exist.
- Per-role `Experience/3.X [Role].md` files: each has a Variant Framings subsection where new framings will go.
- `Cover Letters/` folder: see if a cover letter for this company already exists.
- `Cover Letters/4.20 Reusable Hooks.md`: see what hook lines are already cataloged.
- `6 Achievements.md`: verify any new metrics are not already there.
- Data Discrepancies block in `2 Chronology.md`: the canonical facts list.

### Step 2.2 — Run the contradiction check against canonical facts

The user maintains a canonical facts cheat sheet that records every metric and named entity worth defending across applications. This list grows over time as the user discovers contradictions between drafts.

**How the canonical facts cheat sheet works.** Every time the user notices a contradiction between a tailored draft and the canonical truth (for example, a metric quoted with different numbers in two different applications, or a company name spelled two different ways), the cheat sheet gets a new row. Future runs of this skill check every quantified statement and named entity in the new draft against the cheat sheet, and flag any contradiction without auto-correcting.

The cheat sheet lives in this SKILL.md, near the bottom under "Canonical facts cheat sheet". By default it is empty placeholder structure showing the format. Fill it in over time as you discover contradictions worth locking down.

Format:

| Fact | Canonical | Outdated framings to flag |
|------|-----------|---------------------------|
| [Your most recent role lifetime impact] | [canonical metric] | [outdated variant 1], [outdated variant 2] |
| [Earlier role specific metric] | [canonical metric] | [outdated variant] |
| [Company or product name spelling] | [canonical spelling] | [misspelling 1], [misspelling 2] |

For each match against an outdated framing in the new draft, flag it. Do NOT auto-correct. The user decides in Phase 2.4 whether to update the tailored draft to canonical, update the canonical to match the new draft, or quarantine for later.

### Step 2.3 — Identify new variants worth ingesting

For each role in the new resume:

1. Compare its bullets against existing canonical and variant bullets in the matching `Experience/3.X [Role].md` file.
2. Skip near-duplicates. Apply judgment. If the phrasing is roughly 80 percent or more identical to an existing variant, skip.
3. Flag genuinely new framings, new metrics, new tags, or new angles for ingestion.
4. Also check the cover letter: is there a fresh hook worth adding to `Cover Letters/4.20 Reusable Hooks.md`?

### Step 2.4 — Generate clarifying questions in multi-choice format

Use the AskUserQuestion tool. Always present multi-choice with copy-paste answer sheet at the end:

```
Q1: [Question]
A. ...
B. ...
C. ...

Q2: ...

Copy-paste answer sheet:
Q1:
Q2:
```

Always ask in this order:

1. **Contradictions check** (only if any flagged in Step 2.2). For each flagged contradiction:
   - "The tailored resume uses '[outdated framing]'. The canonical is '[canonical]'. What should I do?"
   - A. Update the tailored resume copy in `Past Resumes/` to use canonical (recommended)
   - B. Quarantine in 'Needs Review' section, decide later
   - C. The tailored resume is correct; update the canonical fact
   - D. Ignore and ingest as-is

2. **New positioning statement** (if a fresh angle for Section 1C is detected):
   - "I would add this as a tagged positioning statement: '[angle]'. Tags: `[tag1] [tag2]`. Keep, revise, or skip?"
   - A. Keep as-is
   - B. Revise (the user specifies)
   - C. Skip

3. **New variant framings** (group by role):
   - For each role with new variants: "Add these new variants under [Role]?"
   - A. Add all
   - B. Add only these specific ones [list]
   - C. Skip all

4. **New big numbers** (if surfaced):
   - "Add to `6 Achievements.md`?"
   - A. Yes, all
   - B. Specific ones only
   - C. Skip

5. **Cover letter handling** (always ask):
   - "How should I file the cover letter for [Company]?"
   - A. Create new archetype file `Cover Letters/4.NN [Company].md` (next available number)
   - B. Append as a variant inside an existing archetype file (the user specifies which)
   - C. Skip cover letter ingestion

6. **Cover letter hooks** (if new ones detected):
   - "Add to `Cover Letters/4.20 Reusable Hooks.md`?"
   - A. Yes, all
   - B. Specific ones
   - C. Skip

7. **Application log metadata** (always ask):
   - "Quick log fields: JD source (LinkedIn, referral, recruiter, direct), salary range (optional), current status (Applied, Phone screen, Onsite, Offer, Rejected, Ghosted, TBD), any notes?"
   - Free-text answer accepted.

PAUSE HERE. Wait for answers.

---

## Phase 3: Update

### Step 3.1 — Apply additive changes to the brain trust child files

Each change goes to a SPECIFIC child file. Do not write to a monolithic file.

- **New positioning statement:** append to `[Your Career Brain Trust folder]/1 Identity.md` Section 1C. Match the existing tagged format: `` **`#Tag1 #Tag2` ([Company] angle):** `` followed by the quoted statement.
- **New variant framings per role:** for each role with new variants approved, append them under the Variant Framings block inside `[Your Career Brain Trust folder]/Experience/3.X [Role].md`. Match the existing bullet format: `- "[verbatim phrase]" [Company], note: [any tag or context]`.
- **Cover letter handling:**
  - If the user chose A (new archetype): create `[Your Career Brain Trust folder]/Cover Letters/4.NN [Company].md` with the verbatim cover letter text plus a Distinctive Details note. Use the next available 4.NN number. ALSO add a new row to the Cover Letter Library table in `INDEX.md`.
  - If the user chose B (variant of existing): append a "Variant Framings" note inside the existing archetype file.
  - If the user chose C (skip): do nothing.
- **New reusable hooks:** append to `[Your Career Brain Trust folder]/Cover Letters/4.20 Reusable Hooks.md` under the appropriate hook category, formatted as bullet quotes.
- **New big numbers:** add new metrics to `[Your Career Brain Trust folder]/6 Achievements.md` under the appropriate role subsection.
- **INDEX timestamp:** update the **Last updated** date at the top of `INDEX.md` to today's date.

### Step 3.2 — Handle canonical-fact contradictions

For each contradiction the user resolved in Phase 2:

- If A (update tailored draft): re-save the `Past Resumes/` copy with the canonical version of the framing.
- If B (quarantine): append to a `## Needs Review` section at the bottom of `[Your Career Brain Trust folder]/2 Chronology.md` with the date, the contradiction, and the deferred decision.
- If C (update canonical): update the Data Discrepancies block in `2 Chronology.md`, AND update the related canonical fact wherever it appears in the brain trust child files, AND update the canonical facts cheat sheet in this SKILL.md to reflect the new locked fact.
- If D (ignore): note it in the Needs Review section anyway, for trail.

### Step 3.3 — Save corpus copies to the Past Resumes folder

Save two separate files to `[Your Past Resumes folder]/`:

- `Resume - [Company].docx`: resume section only
- `Cover - [Company].docx`: cover letter section only

If the source was a combined `.docx`, split it. Use `python-docx` to:

1. Open the source `.docx`.
2. Find the page break paragraph.
3. Create two new documents: one containing all paragraphs up to and including the cover letter content (before the page break), one containing all paragraphs after the page break (the resume).
4. Preserve formatting (font, size, indentation, numbering) using `copy.deepcopy` on the underlying XML elements.
5. Save both.

If a file with that name already exists in Past Resumes (for example, the user applied to the same company before), append a version suffix: `Resume - [Company] (v2).docx`.

### Step 3.4 — Append to Application Log

Open or create `[Your Application Log path]/Application Log.md`.

**Schema.** The file has two parts.

**Part A: Quick Reference Table** at the top:

```markdown
# Application Log

| # | Date | Company | Role | Top Angles | Outcome | Detail |
|---|------|---------|------|------------|---------|--------|
| 001 | YYYY-MM-DD | [Company] | [Role title] | [tag1], [tag2], [tag3] | TBD | [#001](#001) |
```

**Part B: Detailed Entries** below the table, one per application:

```markdown
---

## #001 [Company] — [Role]

**Date applied:** YYYY-MM-DD
**Company:** [name]
**Role title:** [title]
**Source:** [LinkedIn job post, referral, recruiter, direct, etc.]
**JD URL or summary:** [paste URL or first 200 characters of JD]
**Salary range (if known):** [or "not specified"]
**Resume file:** `Past Resumes/Resume - [Company].docx`
**Cover letter file:** `Past Resumes/Cover - [Company].docx`
**Combined source file:** `Applications/[Company] - [Role].docx`

**Positioning angle used:** [the angle Mark chose in resume-builder Step 6]
**Top 5 framings/angles:** [tag1], [tag2], [tag3], [tag4], [tag5]
**Key metrics emphasized:** [which big numbers led]
**Distinctive hooks used:**
- [hook 1]
- [hook 2]
- [hook 3]

**JD fingerprint (keywords flagged for future similar JDs):**
- [keyword 1]
- [keyword 2]
- [keyword 3]

**Response date:** TBD
**Outcome stage:** Applied
**Notes / lessons learned:** [free-text from the user; can be filled in later]
```

When appending a new entry:

1. Add a row to the quick reference table.
2. Add a detailed entry below.
3. Increment the `#NNN` counter so the next entry will be one higher than the highest existing.

The intent of this log is so future-you (or future-Claude in a different thread) can search for "applied AI + 0-to-1" tags and pull up every past application in that space, see which framings, metrics, and hooks were used, and reuse what worked.

### Step 3.5 — Report summary to the user

End the thread with a concise summary:

```
Brain trust updated.

What I did:
- Added [N] new variant framings under [roles] (specific files: `Experience/3.X [Role].md`)
- Added [N] new big numbers to `6 Achievements.md`
- [Created new cover letter archetype `Cover Letters/4.NN [Company].md` | Appended cover letter variant to `Cover Letters/4.X [Existing].md`]
- Added [N] new cover letter hooks to `Cover Letters/4.20 Reusable Hooks.md`
- Refreshed `INDEX.md` Last updated and added row for any new cover letter file
- Logged application #NNN in Application Log.md

Files saved:
- [computer://...resume]
- [computer://...cover letter]
- [computer://...Application Log.md]
- [computer://...INDEX.md]

Flagged but not auto-applied:
- [N] contradictions resolved per your choices in Phase 2
- [N] items quarantined to Needs Review section
```

---

## Application Log fields reference

Every detailed entry must include:

- `#NNN` counter (zero-padded)
- Date applied (ISO format YYYY-MM-DD)
- Company name
- Role title
- Source (LinkedIn, referral, recruiter, direct, etc.)
- JD URL or summary
- Salary range or "not specified"
- Resume file path
- Cover letter file path
- Combined source file path if used
- Positioning angle used
- Top 5 framings / angles (tagged for searchability)
- Key metrics emphasized (which big numbers led)
- Distinctive hooks used
- JD fingerprint (keywords for future similar JD matching)
- Response date (TBD until updated)
- Outcome stage (Applied, Phone screen, Onsite, Offer, Rejected, Ghosted)
- Notes and lessons learned (free-text, often filled in later)

---

## Canonical facts cheat sheet

These are the locked facts the skill checks every tailored draft against. If the new draft contradicts any of these, flag in Phase 2. Do NOT silently update or ignore.

**How to maintain this list.** Start empty. Every time you notice a contradiction between two of your own applications (different numbers for the same metric, different spellings of a company or product name, a role timeline mismatch), add a row here. The cheat sheet grows over time. It is the most valuable piece of meta-knowledge in the whole workflow because it is the one thing that prevents you from re-introducing yesterday's mistakes.

| Fact | Canonical | Outdated framings to flag |
|------|-----------|---------------------------|
| [Your most recent role lifetime impact] | [canonical metric, for example: $80M+ processed lifetime] | [outdated variant 1], [outdated variant 2] |
| [Earlier role specific metric] | [canonical metric, for example: 64% improvement] | [outdated variant] |
| [Company or product name spelling] | [canonical spelling] | [misspelling 1], [misspelling 2] |
| [Role title at a past employer] | [canonical title and date] | [outdated title or date] |
| [Engagement-style framing for a past project] | [canonical verb, for example: "contributed to"] | [overclaim verb, for example: "built"] |

Replace the rows above with your own facts as you discover them. Keep the list short. The goal is not to track every number you have ever used, only the ones you have caught yourself contradicting.

---

## Locked preferences for this skill (apply throughout)

- Always ask clarifying questions in **multi-choice format** with **copy-paste answer sheet** at the bottom (Q1: A, Q2: B, etc.).
- **Never write final updates without explicit approval.** The skill itself is the user's approval to start, but within Phase 2 the user must approve specific additions before Phase 3 writes anything to disk.
- **No em dashes** in any output, anywhere. Use "to" or commas or colons or parentheses instead.
- **No en dashes** either.
- **Pipe separator with double spaces** ("  |  ") when separating items inline.
- Acronyms defined in full on first use within any deliverable, shorthand thereafter.
- Outputs the user will copy elsewhere should be saved as `.md` and shared with a `computer://` link.

---

## Reference files

- Career Brain Trust folder root (read first): `[Your Career Brain Trust folder]/INDEX.md`
- Career Brain Trust folder: `[Your Career Brain Trust folder]/`
- Application log: `[Your Application Log path]/Application Log.md` (the skill creates this if missing)
- Past Resumes corpus: `[Your Past Resumes folder]/`
- Resume-builder skill output: `[Your Applications folder]/`

---

## When NOT to use this skill

- When the user is tailoring a NEW resume from scratch (that is the `resume-builder` skill).
- When the user just wants to edit an existing resume without folding learnings back into the brain trust.
- When the thread has no actual tailored material to ingest.
- When the user is asking general career questions or LinkedIn-related questions (those are separate workflows).
