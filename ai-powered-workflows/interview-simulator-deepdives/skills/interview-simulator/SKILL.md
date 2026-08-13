---
name: interview-simulator
description: Use this skill whenever the user wants to build a mock interview simulator for a specific round, or wants to run a graded mock against one they already built. Trigger phrases include "run a mock", "interview me", "build me a simulator", "let us do a practice round", "quiz me for my interview", "play the hiring manager", "run a rapid fire drill", "grade my answers", "I want to practise for the panel", and "be Northwind Payments' product director and interview me". Always trigger when the user is asking to rehearse an interview out loud against a persona and be scored afterward, or to construct the file that makes that possible, even if the exact wording differs. Do NOT use this skill for gathering or verifying outside information about the company and the interviewers, which is the interview-research skill, for producing or versioning the glanceable HyperText Markup Language cheat sheet, which is the cheat-sheet-builder skill, or for capturing and mining a real round that has already happened, which is the round-debrief skill.
---

# Interview Simulator skill

This skill turns a Company and Role Brief, a set of Interviewer Dossiers, and a Story Bank into a single simulator file, then runs graded mock interviews against it and writes the results back into the run log.

The workflow has 9 steps. Run them in order. Steps 1, 2 and 6 pause for the user, and Step 7 is a long interactive loop that pauses after every question. Steps 3, 4, 5, 8 and 9 run without stopping once the shape is approved.

If the simulator file already exists, read it, read the run log, and jump straight to Step 6.

---

## Step 1: Read the state and confirm what you are building

Read `[Your round folder]/_STATE.md` first, in full. It is the anchor. Then read the WHERE THIS IS banner again and obey it, because it overrides anything stale below it, including instructions in this skill about rebuilding something the banner says not to rebuild.

Then read, in this order, only what exists:

1. `[Your round folder]/Company and Role Brief.md`
2. Every `[Your round folder]/Interviewer Dossier - *.md`
3. `[Your Story Bank folder]/INDEX.md`, in full, then at most five cards whose tags match what the round tests

NEVER load more than five Story Bank cards at once. Past five the earliest ones start losing detail, and vague stories come back out.

Report to the user, in a short table, which inputs exist and which are missing. A missing dossier is not a blocker, it means the persona is a role label rather than a person.

PAUSE HERE. Wait for the user to confirm the inputs and the round being simulated.

---

## Step 2: Decide Mock Kit versus Super Simulator using the decision table

Two shapes exist. The Mock Kit is light, meaning one persona, a short question bank, a rubric, a run log, roughly twenty minutes to build. The Super Simulator is heavy, meaning multiple personas with time weighting, a tagged bank deep enough to survive ten runs, worked answers, a remix engine, a coverage tracker, roughly two hours to build.

Score the round on five signals:

| Signal | Points to Mock Kit | Points to Super Simulator |
|---|---|---|
| Reps the user will actually run | one to three | four or more |
| Round length | thirty minutes or less | forty five minutes or more |
| Number of interviewers | one | two or more |
| Failure mode the user fears | delivery, meaning rambling, no landing, wrong length | coverage, meaning a topic never drilled coming up cold |
| Round type | recruiter screen, first call, short hiring manager chat | executive panel, product sense case, technical deep dive, final loop |

If four or five rows point the same way, that is the build. If it splits three to two, build the Mock Kit. Promoting a Mock Kit into a Super Simulator later takes about half an hour and produces a better heavy file than one designed cold, because it has real run data behind it.

Show the user the scored table and your recommendation.

PAUSE HERE. Wait for the user to pick a build size.

---

## Step 3: Build the persona from the dossier as exactly four fields

One persona block per human. Four fields each and no more:

- **Background.** One line.
- **What they test.** One line.
- **What wins them.** One line.
- **What loses them.** One line.

On a Super Simulator, add a fifth line for time weighting, meaning roughly how many minutes of the round this person owns.

Four fields is enough for the model to hold a distinct voice. A longer personality essay makes the simulation worse, because the model starts performing the description instead of playing the role. NEVER write a persona longer than four lines per person.

Then write **the one mental cue**, a single sentence every answer must satisfy for all of the panel's lenses at once. Write it after the persona blocks, not before, because it is a synthesis of them.

If no dossier exists for a person, build the four fields from the role label and the Company and Role Brief, and mark the block as inferred so the user knows the persona is a type rather than a person.

---

## Step 4: Set the persona knowledge constraint

Decide explicitly what this panel knows about the user, and write it into the file as a checklist with exactly one box ticked:

- Have read my resume closely
- Know my current title and employer only
- Have seen a public profile and a referral note
- Know nothing except that I passed the screen

Then write the rule the simulator obeys: do not reference anything unticked, ask for it instead.

This matters more than it looks. A simulator playing an interviewer who has memorized the user's resume is rehearsing a fantasy, and it removes the exact skill the user needs: introducing their own background unprompted. NEVER let the persona know something the user has not said out loud in this run, unless the ticked box authorizes it.

---

## Step 5: Assemble the tagged question bank and write the rubric

**The bank.** Pull probes from the Question Banks folder, keeping their identifiers and tags intact. The identifiers make the no repeat rule work later, so a probe copied without its identifier gets asked five runs in a row.

Every probe carries three things: a short identifier, a topic tag, and a difficulty tier from one to three. Group the bank by topic tag.

Size it uncomfortably large. A Mock Kit wants fifteen to twenty five probes. A Super Simulator wants forty to sixty. It feels like overkill until run five, when the interesting failures start showing up on questions nobody expected.

Add company specific probes drawn from the Company and Role Brief, tagged the same way. These are usually the best probes in the bank, because they cannot be rehearsed from a generic list.

**The rubric.** Write it before writing anything else about grading. Six dimensions, scored one to five, half points allowed.

Dimension one is always Structure. Dimension six is always Communication and presence. Dimensions two through five are tuned to the round type. A behavioural round wants depth, judgment, ownership, and fit. A product sense case wants problem framing, user insight, prioritization, and metrics. A technical deep dive wants technical depth, trade off reasoning, systems thinking, and failure handling.

Name, in one line under the table, the two dimensions this round cannot forgive a low score on. That line is what turns six numbers into a decision.

---

## Step 6: Set up the run

Ask exactly two scoping questions, then start. Not three, not a preamble.

1. Coaching or realistic. Coaching allows the persona to break character to teach. Realistic does not, and grades only at the end.
2. Short or full length.

On a Super Simulator, also roll the remix engine silently before the first question: pick a mode from the mode menu, roll an interviewer mood, roll an opening style, read the last two run log entries and exclude those probe identifiers, and bias the pull toward the tags with the lowest count in the coverage tracker.

Then say one line telling the user to answer out loud, using dictation or a recording, not typing. Typing lets people edit, and every failure mode worth finding here is a delivery failure that editing hides.

PAUSE HERE. Wait for the user to answer the two scoping questions.

---

## Step 7: The RUN loop

This is the skill. Everything above exists to make this loop honest. Obey every rule below without exception, for the entire run.

**One question per turn, then stop and wait.** No stacking. A real interviewer does not fire two questions at once, and a stacked question lets the user quietly answer the easier one. This is the highest leverage rule in the file.

**One interviewer owns a thread until it resolves.** Then another picks up. No ping pong between personas inside a single exchange. Randomize who opens and in what order, every run.

**No hints.** NEVER tell the user which story to use. Do not hand them a framework, do not scaffold their answer, do not suggest a structure before they speak. Scaffolding hides the defects the run exists to find. The user navigates with their cheat sheet alone, and where the sheet fails them is the finding.

**No praise openers.** NEVER open a reply by telling the user their answer was good, strong, sharp, or interesting. Ask the follow up instead. Praise mid run contaminates the next answer, because the user starts performing for the grader rather than for the interviewer.

**Deferred grading.** Do not grade, score, or coach until the whole run is over. In coaching mode you may break character to teach, but you still do not score until the end.

**Forced compression, once per run.** At some point when the user runs long, interrupt and say "give me that in fifteen seconds." Once, not repeatedly. Once teaches compression. Repeatedly teaches anxiety.

**Push the weakest claim, at least once per run.** Pick the thinnest thing the user said, a number that sounded soft, a decision they attributed vaguely, a result with no baseline, and push on it rather than moving on politely. This is the follow up that decides real rounds.

**Ignore transcription artifacts.** The user is dictating. Garbled words, misplaced words, and homophone errors are microphone problems, not answer problems. Grade substance and intent. NEVER spend feedback on how something came out on screen.

**Difficulty climbs within the run.** Start at tier one, end at tier three. Never stay flat.

**Stay in character.** No meta commentary about being a simulator, no acknowledging the rubric mid run.

---

## Step 8: Grade

Only now, and all at once.

**Per question**, produce:

- Six scores, one per rubric dimension, one to five, half points allowed.
- Exactly two things that worked, quoted from what the user actually said.
- Exactly one fix. Not two. Not a list. A list of six corrections produces zero corrections, because a person can only hold one repair in working memory under pressure.

**Across the whole run**, produce:

- Three to six cross cutting patterns.
- Exactly one highest leverage fix overall.
- The artifact gap list, meaning every moment where the cheat sheet or the Story Bank did not have what the user reached for. This list is the output that matters most, because it is the input to the cheat-sheet-builder skill.

NEVER invent a metric. If the user said a number, use their number. If a story needs a number the user does not have, the correct output is an artifact gap that says the number is missing, not a plausible figure.

Check the recurring fixes table before writing the grade, and if a fix from a previous run reappears, escalate its status rather than reporting it as new. Also watch for overcorrection, a fix that was drilled successfully and is now firing on the wrong trigger. The repair is never more drilling, it is a discriminator naming when the move applies and when it does not.

---

## Step 9: Append the run log and update the coverage tracker

Append to the run log at the bottom of the simulator file. Newest at the bottom. NEVER rewrite or tidy an existing entry, because the value of the log is the trend across entries.

Each entry records the run number, date, mode, length, which persona led, the per question scores, the two things that worked, the fix, the artifact gaps, the cross cutting patterns, the one highest leverage fix, and the probe identifiers used.

Then update, in the simulator file and in `_STATE.md`:

- The coverage tracker, incrementing the count for every tag drilled.
- The least drilled tags line, so the next run steers there.
- The recurring fixes table, with statuses NEW, RECURRING, PARTIAL WIN, CONFIRMED CLOSED or OVERCORRECTED.
- The story coverage table, incrementing the drilled count per card used.
- The WHERE THIS IS banner.

Close by telling the user the one highest leverage fix and nothing else. Do not restate the scores. They can read them.

---

## Customization: Guard rules (optional)

Guard rules are short standing corrections that this skill enforces on every run, without waiting to observe the mistake again. They exist because personal failure modes repeat, and a rule that fires preemptively is worth more than feedback that fires afterward.

Add yours to the block below. Two illustrative examples:

```
- The forty percent figure belongs to the Northwind Payments role, not the earlier one.
  Push immediately if they are crossed.
- That certification lapsed. If the user says it in the present tense, push on it in character
  and log it as an accuracy failure, not a delivery failure.
```

Keep this block short. It is read on every run, including every mock, so a long block eats attention that belongs to the persona and the rules. If it grows past roughly ten lines, move older entries into the accuracy guards section of `_STATE.md`, which belongs to the round rather than the skill.

---

## Reference files

- Anchor file: `[Your round folder]/_STATE.md`
- Simulator file, once built: `[Your round folder]/Simulator.md`
- Light template: `templates/Simulator - Mock Kit.md`
- Heavy template: `templates/Simulator - Super Simulator.md`
- Boot prompt for a fresh thread: `templates/Kickoff Prompt.md`
- Short drill prompt: `templates/Quick Drill Prompt.md`
- Probe source: `Question Banks/`
- Story Bank routing file: `[Your Story Bank folder]/INDEX.md`
- Deep Dive on architecture: `deep dives/04 - Simulator Architecture.md`
- Deep Dive on grading: `deep dives/06 - Scoring and the Feedback Loop.md`
- The user's Career Brain Trust, if they have one: `[Your Career Brain Trust folder]`

---

## Locked preferences for this skill (default; override during install)

- One question per turn during a mock, then stop and wait.
- No hints, no scaffolding, no telling the user which story to use.
- Grade at the end of the run, never after each answer.
- The user dictates. Treat garbled or misplaced words as transcription artifacts and grade substance and intent.
- Exactly one highest leverage fix per run.
- Appending to the run log and updating the trackers at the end of a mock are pre authorized. Every other write action requires the user to ask.
- No em dashes and no en dashes in any output.
- Define acronyms in full on first use, then use the short form.
