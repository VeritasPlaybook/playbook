>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Scoring and the Feedback Loop

This deep dive expands Step 8 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which told you to run mocks out loud and take one fix from each, in six bullets. This is the longer version: the reframe that makes the mock a test harness and your artifacts the thing under test, the six dimension rubric and how to tune it, the threshold that counts as ready, why one fix beats six, grading with quoted evidence, why feedback between answers contaminates the run, the five stage fix lifecycle, overcorrection detection and why the repair is a discriminator rather than more drilling, spacing, why typing produces false positives, card read mode, and when the scores stop telling you anything.

Read the main guide first, and have a simulator that contains a rubric, a question bank, and a run log. This chapter is about what to do with the output of a run, which means you need to have run one.

---

# The Mock Is the Test Harness

The reframe that changes everything: the mock is not the product. It is a test harness, and the thing under test is your artifacts: the cheat sheet, the Story Bank cards, the trigger table. Your performance during the run is the instrument reading, not the subject.

This is not a motivational reframe designed to make failure feel better. It is a mechanical one, and it changes what you do next. If your performance is the subject, a bad run produces a resolution: remember to do better. Resolutions do not survive minute forty of a real interview, because under pressure you have access to what is written in front of you and what is genuinely automatic, and nothing else.

If the artifacts are the subject, a bad run produces a defect with an owner and a version number. You reached for the number on the fraud story and the sheet did not have it, so the sheet gets the number. You could not tell which story the question wanted, so the trigger table gets a row. You could not stop talking, so the card gets a written last sentence.

The mechanism is a required output. Every run ends with at least one artifact gap note: "the sheet did not have what I needed here," specific about which artifact and which line. If a run produces no artifact gap, either it was too easy or the bot got polite.

Then convert the note into an edit, immediately, before the next run. Skipping this turns a run log into a diary rather than a build history, and the version number proves you did not skip it. A cheat sheet at version four after five runs has survived contact. One still at version one means five runs told you things and you listened to none.

---

# Six Dimensions, One to Five

Six dimensions, one to five, half points allowed. Six separates distinct failure modes and still fits in your head. Half points matter more than they sound, because most movement between run two and run five is half a point at a time, and a scale that cannot express it reports you as flat when you are improving.

Dimension one is always structure: ran a visible framework, clarified before solving, did not wander. Dimension six is always communication and presence: concise, calm, quantified, landed the point, then stopped. Those two are constant because they are round invariant, and they most reliably separate a good candidate from an offer.

Dimensions two through five tune to the round type. A behavioural round wants depth, judgment, ownership, and fit. A case round wants problem framing, user insight, tradeoffs, and metrics. A technical deep dive wants technical depth, system thinking, risk awareness, and explaining something complicated to a non specialist. An executive panel wants scope, strategic framing, stakeholder handling, and decisiveness under incomplete information. Pick four matching what the round scores, then write what a five looks like on each, in one line, before you run anything. Ungrounded dimensions drift, because the model invents the standard fresh every run.

## Rename anything you cannot operationalize

If a dimension comes back scored and you cannot say what you would do differently to raise it, rename it. "Executive presence" is the usual offender: real, and useless as a scoring dimension, because a three tells you nothing you can act on. Rename it to what it measures in your round, such as "answers the question asked in the first sentence, then supports it." Now a three is a specific behaviour with a specific repair.

Do this every time a dimension produces a shrug. A term inherited from a job posting is not sacred, and one you cannot operationalize quietly consumes one sixth of your feedback every run.

## The threshold

Strong is four or better across the board, with no twos on the two dimensions this round cannot forgive. Name those two when you build the file, before you have scores, so you cannot retroactively decide your weakest dimension was the forgiving one.

It is an every dimension bar rather than an average, because a five and a two average to a pass and interview outcomes do not work that way. One dimension scored two is usually the whole story of a rejection. And the unforgiving pair is named per round, because a two on metrics is survivable in a peer culture round and fatal in a case.

---

# One Fix, Not Six

Every graded run produces six scores, exactly two things that worked, and exactly one highest leverage fix. Not a list. One.

A list of six corrections produces zero corrections. This is not a discipline failure, it is a working memory limit. Under load you can hold one deliberate behavioural change while also listening, structuring, and talking. You cannot hold six. Given six, your attention spreads across all of them, none reaches the threshold where it changes what comes out of your mouth, and the next run reproduces all six. The feeling of having received thorough feedback is what prevents the feedback from working.

The two things that worked are not a kindness, they are protection. Without them, run after run of pure correction erodes the behaviours that were already good, because you start suspecting everything you do. Naming two things to keep doing tells you what not to touch.

Insist the single fix be specific enough to execute. "Be more concise" is a category, not a fix. "On the migration story, delete the two sentences of background and open with the decision" is a fix, because you can do it now and it will be visibly done or not next run. If the bot hands you a category, ask for the sentence.

The one fix rule is why grading is deferred, why the fix lifecycle exists, and why overcorrection is predictable rather than surprising. Concentrating all your attention on one behaviour is powerful because it is narrow, and narrow interventions overshoot.

---

# Grading With Quoted Evidence

Instruct the bot to quote back what you actually said. Not a characterization of it, the words.

Feedback of the form "your answer was unfocused and did not land" is unfalsifiable and unmemorable. Feedback of the form: you said "so there were a bunch of stakeholders and it was kind of a mess for a while and eventually we got alignment," and that sentence contains no decision, no actor, no timeline, is a different object. You recognize it. You wince. You can hear yourself saying it, which means you will hear yourself starting to say it again.

The quote also protects you from a grader that has drifted. A model that calls an answer rambling and cannot produce the rambling part is generating plausible interview feedback rather than assessing your answer. Requiring evidence is a cheap check on whether the grading is real.

Ask for the quote behind each of the two things that worked, too. It teaches you what your own good work sounds like, which is harder to recognize than the bad.

## Defer grading until the run is over

No feedback between answers. The realism argument is obvious: no real interviewer tells you how you are doing after each answer, and rehearsing in a loop where someone does removes the discomfort of not knowing, which is a large part of what makes real rounds hard.

The data argument matters more. An answer given after feedback is not an independent observation. If the bot tells PM Jordan after question two that the answer ran ninety seconds long, question three will be short. That is not evidence Jordan can be concise in an interview, only that Jordan can be concise eleven seconds after being told to be, and in the real round nobody gives that instruction. The correction usually overshoots too, question three comes out thin, and the run log records a length problem in the opposite direction that never existed.

One exception, the bounded coaching mode from the simulator architecture chapter: the bot may break character for at most two lines and then resume. Use it when learning a structure for the first time, never on a run you intend to read as a measurement.

---

# The Fix Lifecycle

A fix has five states, and tracking them turns a pile of run notes into a picture of what is happening to you.

**NEW.** Seen once. It might be a real pattern or one bad answer on a topic that caught you cold. Do not escalate on the first sighting.

**RECURRING, two runs.** The same failure on two separate runs, ideally on different questions. A real pattern, and the state where the fix becomes the highest leverage one by default. Two runs is the threshold rather than three, because waiting for three is a week you did not have.

**PARTIAL WIN.** The failure is smaller. You landed three of five stories instead of one. Name these explicitly, because they look like failure if you only check whether the fix appeared, and calling a partial win a failure is how people conclude the loop is broken and stop.

**CONFIRMED CLOSED.** Absent across two consecutive runs that gave it a real opportunity to appear. The opportunity clause matters: a closing problem is not closed because the last two runs were rapid fire probes with no stories in them.

**OVERCORRECTED.** The fix is now firing where it should not. A distinct state rather than a return to open, and it needs a different repair, described next.

Keep closed fixes in the table, marked closed, rather than deleting them, because a closed fix is the most likely thing to reopen as an overcorrection.

Then carry the open ones forward. Every run's kickoff includes a watch block listing the fixes in NEW, RECURRING, or OVERCORRECTED, with an instruction to watch for them actively rather than wait to notice. That turns the bot from a passive observer into one that engineers opportunities. If your open fix is a landing problem, the run contains three questions requiring a story with an ending, which is the difference between a run that might surface your issue and a run designed to.

---

# Overcorrection, and Why the Repair Is a Discriminator

Anything you drill four times will start firing on the wrong trigger. This is not a personal failing, it is what concentrated practice does, and this loop produces it reliably enough to expect rather than be surprised by.

The worked example. Engineer Alex, preparing for a technical round at Northwind Payments, gets the same fix three runs running: lead with the outcome, do not narrate the investigation chronologically. Alex drills it. Run four is the best yet, four and a half or better across the board. In run five the bot asks how Alex would approach evaluating a new fraud model before rollout, and Alex opens with "we cut false positives by thirty one percent," a number from a previous project attached to a question that did not ask for a result. It asked for an approach. Alex answered a question about method with a headline about outcome, and structure drops to a three.

Read naively this looks like a structure problem, and the loop will hand Alex a structure fix, which makes it worse, because more drilling on leading with the outcome is the wrong medicine.

The detection signal is specific: a dimension you were not working on drops, on a new question type, while the dimension you were drilling stays high. That combination almost always means the drilled behaviour has escaped its context. The other tell is a comment of the form "you answered a question that was not asked."

The repair is never more repetition. It is a discriminator: one written rule saying when the move applies and when it does not. For Alex, a single line on the cheat sheet: *outcome first when the question asks what happened, method first when the question asks how you would approach it.* One line, one card, one rep to install. The state becomes OVERCORRECTED, RESOLVED, and the log records both the drill and the boundary, so a future thread does not reopen the original fix.

Write discriminators as if then pairs, keep them on the cheat sheet rather than in the simulator, and expect three or four across a preparation cycle. They are among the most durable things you will produce, because they transfer to every future round while the stories keep changing.

---

# Out Loud, and Spaced

**Say the answers out loud.** Every typed practice answer is a false positive, and the mechanism is simple: typing lets you edit. You backspace over the false start, reorder the two clauses, quietly delete the forty seconds of preamble before committing to it. What you produce is a written answer of a quality you cannot reach in speech, the bot grades that, and the score measures your writing.

Meanwhile the failure modes you need to find are delivery failures. Running long. Burying the headline in sentence nine. Trailing off without landing. Answering the neighbour of the question that was asked, because you heard the first six words and started talking. None is visible in typed text, because typing repairs them silently before the grader sees anything.

Use dictation, or record and paste the transcript. The rule is that the words leave your mouth before they reach the page. Then tell the bot to ignore transcription artifacts, so dropped words and homophones do not consume the one fix you get.

**Space the reps.** Three runs over three days beats five in one evening by a wide margin. This is not a productivity preference, it is how memory consolidates: retrieval practice spaced across days produces more durable recall than the same retrievals crammed together.

Cramming also corrupts the measurement. Run four on the same evening as runs one through three is answered by someone who has said adjacent versions of these answers three times in ninety minutes. The scores go up. The improvement is short term availability rather than learning, and it will not be there on Thursday. If you have one evening, run twice and stop. The third run that night is worth less than sleep.

---

# Card Read Mode

There is a second mode worth building that most people never think of, separating two failures that otherwise look identical.

In card read mode you do not answer the question. The bot asks, and you name which cheat sheet card you would use and read it aloud, verbatim. Then the bot grades two things separately: whether you selected the right card, and whether the card contained what the answer needed.

This is worth its own mode because a bad answer has two independent causes and a normal run cannot tell them apart. Either you reached for the wrong material, or you reached for the right material and it was not good enough. Wrong selection is a trigger table problem, repaired by a row mapping the phrase you heard to the card you should have picked. Weak card is a content problem, repaired by a rewrite. Confusing them wastes runs: you can rewrite a perfectly good card three times while the real failure is that you never open it.

It is also fast. Fifteen probes takes twelve minutes because you are not composing anything, which makes it the right thing to run the morning of the round, when a full spoken run is too expensive and too destabilizing.

Score two axes. Selection, one to five, on whether the card you named was the best available and how long it took. Card quality, one to five, on whether reading it aloud constituted a usable answer. High selection and low quality means the sheet is thin. Low selection and high quality means the sheet is good and your index into it is not, the more common result and the cheaper to fix.

---

# When the Scores Stop Being Informative

Scores are useful while they are moving. When they stop moving, they stop being feedback and start being reassurance, and reassurance is not what you came for.

Three signals that the loop has run out.

**Flat scores across three runs, and the fixes are getting smaller.** When the highest leverage fix drops from "you never state the decision you made" to "consider tightening the second clause of your opening," the loop has found everything at its resolution. Further runs keep producing notes, the notes keep getting less consequential, and you keep feeling productive.

**The same score arrives regardless of how the run felt.** If a run you experienced as excellent and one you experienced as a disaster both come back at four point two, the grading has converged on your average rather than assessing the run.

**Every fix is now a preference.** When you disagree on grounds of taste rather than accuracy, the remaining variance is style, and style is not what the round rejects people for.

Plateauing is not the same as failing and not the same as being ready. It usually means one of three things. You have exhausted the question bank and are drilling recall rather than judgment, and the repair is breadth, not more reps. Or the remaining gap is material rather than delivery, and no number of runs fixes a story with no result in it, because that is a Story Bank problem wearing a delivery costume. Or you are ready and running mocks for the feeling of running mocks.

That third one has a specific shape. It is eleven at night, the round is tomorrow, the last three runs came back strong, and you are about to start a fourth. Nothing good is in that run. Scores at that hour measure fatigue, not preparation, and a bad one does real damage to how you walk into the room while teaching you nothing you can act on in twelve hours.

The stopping rule: when the last two runs produced no artifact gap and no new fix, you are done. Do one card read pass, close the folder, and go to bed. Tomorrow is not won by the seventh rep. It is won by the six you already ran, and by being rested enough to use them.

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

If you use or adapt this guide, please include:

Based on "Scoring and the Feedback Loop," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
