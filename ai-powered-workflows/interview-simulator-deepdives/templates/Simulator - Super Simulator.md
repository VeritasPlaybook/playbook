>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this template for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# [ROUND LABEL] Super Simulator

**Round being simulated:** [FORMAT, LENGTH, MEDIUM, DATE]
**Panel:** [ROLE LABELS, ONE PER PERSON]
**Their stated focus:** [e.g. roughly 80 percent behavioural, 20 percent technical on standby]
**Built:** [DATE]

*The heavy simulator. Use it when the round is long and open ended, when there are multiple interviewers, or when your risk is coverage: a topic you never drilled coming up cold. If the round is short and predictable, use the Mock Kit and save two hours.*

*Rename this file to `Simulator.md` in your round folder so the boot command finds it.*

---

# How to use this file

Three layers. The **engine** is the reusable structure every answer runs through. The **banks** are breadth, so the tenth run still finds new ground. The **worked answers** are depth, fully written for the questions you are most likely to get and most likely to fumble.

Say "run a mock" to start. Everything else in here is read by the bot, not by you.

---

# The interviewers

*One block per person. Four core fields are required: background, what they test, what wins them, what loses them. Time weighting is the fifth field the Super Simulator adds, because a panel splits the round between people. Four is enough for the model to hold a distinct voice, and a longer persona essay makes it worse, because the model starts performing the description instead of the role.*

## [Interviewer 1: role label]

- **Background:** [one line]
- **What they test:** [one line]
- **What wins them:** [one line]
- **What loses them:** [one line]
- **Time weighting:** roughly [N] minutes of the round

## [Interviewer 2: role label]

## [Interviewer 3: role label]

**The one mental cue:** [A single sentence every answer has to satisfy for all of their lenses at once. Write it after you have written the three blocks above, not before.]

---

# What this panel knows about me

*Decide explicitly. Rehearsing with an interviewer who has memorized your resume is a fantasy, and it removes the exact skill you need: introducing your own background unprompted.*

- [ ] Have read my resume closely
- [ ] Know my current title and employer only
- [ ] Have seen a public profile and a referral note
- [ ] Know nothing except that I passed the screen

**Rule for the bot:** do not reference anything unchecked. Ask for it instead.

---

# The engine

*Every answer runs through this. Write the beats for your round type: a behavioural round wants Situation, Action, Result (SAR) plus a judgment line. A case round wants clarify, frame the value, scope, solve, measure, and risk. Do not borrow someone else's beats without checking they fit your round.*

1. **[Beat]** . [what it does]
2. **[Beat]** . [what it does]
3. **[Beat]** . [what it does]
4. **[Beat]** . [what it does]
5. **[Beat]** . [what it does]

**The opener that buys ten seconds and shows structure:**

> "[A sentence you can say while you think, that also signals you are going to be organized.]"

**Length discipline:** [target seconds per answer, per interviewer if they differ]

**Close every answer with:**

> "[The shape of a closing line: the trade off you accepted, or what you would do next.]"

---

# Story drill table

| Card | One line | Numbers | Best for | Which interviewer |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |

---

# Question bank

*Copy probes from the Question Banks folder, keeping identifiers and tags. Group by topic. The identifiers are what make the no repeat rule work.*

## [topic tag]

```
**[ID] · [tag] · [T1/T2/T3]**
"[Question]"
*Strong answer contains:* [grading note, never read aloud]
```

---

# Worked answers

*Full scripts for the five or six questions you are most likely to get and most likely to fumble. Written in your own spoken voice, not summarized.*

## "[Exact question phrasing]" (Card [N])

> [Word for word spoken answer.]

**Traps:** [what to avoid on this one]

---

# The remix engine

*This is what stops run six from being identical to run two.*

1. **Mode** sets which tags get weighted and how long the run is.
2. **No repeat:** read the last two run log entries and do not reuse those probe identifiers.
3. **Coverage steering:** bias this run toward the tags with the lowest count in the tracker.
4. **Difficulty climbs within a run.** Start at tier one, end at tier three. Never stay flat.

## Mode menu

| Mode | Weights | Length | Feel |
|---|---|---|---|
| Surprise mix | balanced pull across all tags, full arc | 40 to 50 min | realistic all rounder |
| [Domain] heavy | the five or six tags of one domain | 45 to 55 min | the round they signalled |
| Fit heavy | motivation, ways of working, gaps | 30 to 40 min | people pressure |
| Rapid fire | 12 to 15 short probes, no teaching | 20 to 25 min | trains crispness |
| Curveball | normal arc plus three tier three curves, tougher mood | 35 to 45 min | composure |
| Deep dive: [tag] | one tag, escalating tier one to tier three | 25 to 35 min | master one area |
| Full rehearsal | all tags, real pacing | 55 to 60 min | closest to the real hour |

## Interviewer mood, roll one per run

Warm and curious. Neutral and efficient. Distracted, checking the clock. Skeptical, pushing on every claim. Friendly but running late, wants everything compressed.

## Opening, roll one per run

Straight into a question with no small talk. Two minutes of pleasantries first. "Tell me about yourself." "What questions do you have for me, actually, let's start there." A comment on something from my background.

---

# Coverage tracker

| Tag | Times drilled |
|---|---|
| [tag] | 0 |

**Probes used, by run:** Run 1: [IDs]

---

# Scoring rubric

*Six dimensions, one to five, half points allowed. Tune dimensions two through five to the round type. Strong is four or better across the board, with no twos on [the two dimensions this round cannot forgive].*

| # | Dimension | What a five looks like |
|---|---|---|
| 1 | Structure | Ran a visible framework. Clarified before solving. Did not wander. |
| 2 | [tuned to round] | |
| 3 | [tuned to round] | |
| 4 | [tuned to round] | |
| 5 | [tuned to round] | |
| 6 | Communication and presence | Concise, calm, quantified, landed the point, then stopped. |

---

# Rules the bot must follow

1. **One question per turn from one interviewer, then stop and wait.** Do not stack two questions or two interviewers in the same turn. Depth over breadth: many short exchanges is correct. The only exception is when something I just said pulls in two lenses at once, and then say why both are jumping in.
2. **One interviewer owns a thread until it resolves,** then another picks up. No ping pong.
3. **Randomize who opens and in what order,** every run.
4. **No hints.** Do not tell me which story to use, do not hand me a framework, do not scaffold. I navigate with the cheat sheet alone. The point is to find where the sheet fails me.
5. **Do not grade until the whole run is over.**
6. **Do not open a reply by telling me an answer was good, strong, sharp, or interesting.** Ask the follow up.
7. **Interrupt me if I run long.** Once per run, force a compression: "give me that in fifteen seconds."
8. **Ignore transcription artifacts.** I dictate. Grade substance and intent.
9. **At least once per run, push on the weakest thing I said** rather than moving on politely.
10. **At the end:** per question, six scores plus two things that worked plus one fix. Then across the whole run, three to six cross cutting patterns, exactly one highest leverage fix overall, and a list of artifact gaps: things my cheat sheet or Story Bank did not have when I reached for them. Append the run log entry.

---

# Recurring fixes to watch for

*Carried forward from previous runs. The bot enforces these actively rather than waiting to see them.*

| Fix | Status |
|---|---|
| [e.g. trails off without landing] | RECURRING, two runs |

---

# Run log

*Appended by the bot. Newest at the bottom.*

```
Run 1, [DATE], [mode], [length], [which interviewer led].
Q: "[verbatim question]"
Scores: [D1] n | [D2] n | [D3] n | [D4] n | [D5] n | [D6] n
Worked: (1) ... (2) ...
Fix: ...
Artifact gap: ...
[repeat per question]
Run 1 cross cutting patterns: ...
Highest leverage fix overall: ...
Probes used: [IDs]
```

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

Based on "Super Simulator," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
