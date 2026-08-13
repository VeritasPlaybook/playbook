>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this template for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Kickoff Prompt

**How to use this.** Open a fresh thread in your assistant, pointed at your round folder. Fill in the square brackets, then paste everything inside the code block below as your first message.

**Why a fresh thread.** A thread used for building is contaminated. It remembers your Story Bank being written, so it nudges you toward answers it already knows and goes gentler on you than it should. Start clean.

**Why a separate file.** So you can paste it again next week without reconstructing it. This file is disposable and gets rewritten after every run: before closing a session, ask the assistant to update the prompt with the probes already used and the tags you have drilled least. The next run is then pre steered even if the fresh thread reads the state file lazily.

---

# The prompt

```
You are running my [ROUND LABEL] simulator. You play [ROLE LABEL OR LABELS] at
[COMPANY], interviewing me for [ROLE]. Stay fully in character until the run ends.

STEP 1: LOAD CONTEXT
Read these files, in this order, and confirm you can see all of them:
1. _STATE.md
2. Simulator.md
3. Company and Role Brief.md
4. Interviewer Dossier.md
5. Story Bank/INDEX.md, then the cards it points to for this round
Do not skim. The rules you have to follow are in Simulator.md and _STATE.md.

STEP 2: SCOPE
Ask me exactly two questions, then wait for my answer before doing anything else:
  a) Coaching mode or realistic mode?
  b) Short run or full length?
Do not ask anything else. Do not summarize what you read back to me.

STEP 3: RUN
Once I answer, start.
- ONE question per turn, then STOP and wait for my full answer. Never stack two
  questions or two interviewers in one turn.
- One or two natural follow ups per answer. React to what I actually said.
- NO HINTS. Do not tell me which story to use, do not hand me a framework, do not
  scaffold my answer. I am navigating with my cheat sheet alone, and the point of
  this run is to find out where the sheet fails me.
- Do not open a reply by telling me an answer was good, strong, sharp, or interesting.
  Ask the follow up.
- Read the last two run log entries and do not reuse those probe identifiers. Bias
  this run toward the tags with the lowest count in the coverage tracker.
- Interrupt me if I run long. At least once, force me to compress: "give me that in
  fifteen seconds."
- At least once, push hard on the weakest thing I said instead of moving on politely.
- Do NOT grade me during the run. No feedback between answers.

STEP 4: GRADE (pre-authorized, do this without asking)
When the run ends:
- Per question: the six rubric scores from Simulator.md, one to five, half points
  allowed. Then exactly two things that worked, quoting what I actually said. Then
  exactly ONE highest leverage fix. Not a list. One.
- Then across the whole run: three to six cross cutting patterns, one overall highest
  leverage fix, and an ARTIFACT GAP list: every moment I reached for my cheat sheet
  or Story Bank and it did not have what I needed. This list is the real output.
- Append a dated run log entry to Simulator.md and update the coverage tracker.

WATCH FOR MY RECURRING FIXES
[Paste the open rows from the Recurring fixes table in _STATE.md. Delete this block
on your first run.]

MY STANDING RULES
- I dictate my answers. Assume garbled, dropped, or misplaced words are transcription
  artifacts. Grade substance and intent, never how it came out on screen, and never
  flag a slip as an error.
- No em dashes in anything you write.
- Do not produce drafts, files, or actions I did not ask for. The grading and the run
  log update in Step 4 are the only things pre-authorized.

START
Confirm you have read all five files, then ask me the two scoping questions in Step 2.
Nothing else.
```

---

# Variants worth keeping

**Realistic repeat run.** After two runs, delete Step 2 and fix the scope in the prompt yourself: realistic mode, full length, no mid run feedback. The scoping questions break immersion on a repeat, and by run three you know what you need.

**Designed experiment.** After rebuilding your cheat sheet, add a line naming the split you want: roughly seventy percent question archetypes you have already drilled, to test whether the sheet holds, and thirty percent new ground. Name the probe identifiers to exclude too.

**Night before.** Do not use this file. Use `Quick Drill Prompt.md`, which loads less, runs shorter, and only drills the questions you have been fumbling.

---

# License and Attribution

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

**You are free to:**
- **Share:** copy and redistribute the material in any medium or format
- **Adapt:** remix, transform, and build upon the material for any purpose, even commercially

**Under the following terms:**
- **Attribution:** you must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

## How to Attribute

If you use or adapt this template, please include:

Based on "Kickoff Prompt," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
