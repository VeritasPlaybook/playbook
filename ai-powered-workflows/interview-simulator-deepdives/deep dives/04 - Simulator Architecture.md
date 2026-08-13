>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Simulator Architecture

This deep dive expands Step 7 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which gave you seven bullets for building the simulator file. This is the longer version: the decision table for Mock Kit versus Super Simulator and the diagnostic behind it, persona construction in four fields and why a longer one is worse, what the persona is allowed to know about you, the four rules that do more work than everything else combined, tagged question banks and the grading note that is never read aloud, the remix engine that stops run six repeating run two, the mode menu, panel simulation as a set of lenses rather than people, the adversarial moves worth instructing explicitly, and how to tell when you have crossed from building a simulator into avoiding one.

Read the main guide first, at minimum Steps 1 through 6. Everything here assumes you know the round format, have a Story Bank with defensible numbers, and have an Interviewer Dossier or at least an honest role label for each person in the room. A simulator built before those exist is a generic question bot wearing a costume.

---

# Which Build Size, and How to Tell Without Guessing

Two shapes in this kit. The Mock Kit is light: one persona, a short question bank, a rubric, a run log, twenty minutes. The Super Simulator is heavy: multiple personas with time weighting, a tagged bank deep enough to survive ten runs, worked answers, a remix engine, a coverage tracker, two hours.

Score the round on five signals.

| Signal | Points to Mock Kit | Points to Super Simulator |
|---|---|---|
| Reps you will actually run | one to three | four or more |
| Round length | thirty minutes or less | forty five minutes or more |
| Is the question set knowable in advance | mostly yes | no, they can go anywhere |
| Failure mode you fear | delivery: rambling, no landing, wrong length | coverage: a topic you never drilled coming up cold |
| Round type | recruiter screen, first call, short hiring manager chat | executive panel, product sense case, technical deep dive, final loop |

If four or five rows point the same way, that is your build. If it splits three to two, build the Mock Kit. Promoting a Mock Kit takes half an hour of adding tags and a second persona, and it happens with real run data behind it, which produces a better heavy simulator than one designed cold.

The fourth row carries the most weight, and works as a standalone diagnostic: the failure you fear tells you which file to build. Say the fear out loud and listen to its object. "I am going to ramble and they will lose the thread" is a delivery fear, cured by repetition against a small set of known questions, which a Mock Kit run four times will do. "They are going to ask about pricing and I have never said a sentence about pricing" is a coverage fear, and no amount of repetition on your five best stories touches it. That one needs breadth, tags, and a remix engine that steers you into the corners you avoid.

People get this wrong in one direction. They fear delivery, build the heavy file because it feels more serious, and run it once. Two hours of building bought one rep.

---

# The Persona, Four Fields and No More

Every interviewer gets exactly four fields, one line each: background, what they test, what wins them, what loses them. For a panel, add a fifth line for time weighting, which is mechanical rather than characterological.

Four fields is not a compromise for brevity. It produces a better performance than forty. A long persona essay, the kind describing someone as warm but exacting, intellectually restless, and allergic to hand waving, hands the model a character study, and a model handed a character study performs the study. You get an interviewer who demonstrates the adjectives at you, announcing it is being exacting rather than being it, staging its allergy to hand waving as a speech instead of a follow up question. The description leaks into the dialogue and the round starts feeling like a table read.

Four terse fields leave nothing to perform. There is no prose to reproduce, only a job to do, so the model does the job: asks, listens, and pushes where the field says to push.

The two fields that do the real work are what wins them and what loses them, the only two that change the model's behaviour turn by turn. Write them as observable moves rather than values. Not "values ownership," which is a poster. Write "wins by hearing the specific decision the candidate personally made and what they gave up to make it" and "loses when the candidate says we without ever saying I." Now the model has something to check each answer against, and its follow ups hunt for what is missing.

Write the four lines for the role, not the human. If a research director at Northwind Payments has published on evaluation methodology, that belongs in the dossier, and in the persona it becomes "tests whether claims about model quality come with a measurement behind them." The dossier holds the person. The persona holds the lens.

---

# What the Persona Is Allowed to Know

Decide in writing, in the file, what this interviewer knows about you. The template gives four checkboxes: read your resume closely, knows your title and employer only, has seen a public profile plus a referral note, or knows nothing except that you passed the screen. Tick one, then add the rule that makes it bite: do not reference anything unticked, ask for it instead.

This is the most common defect in a homemade simulator, and it is invisible because it feels like quality. You paste your Story Bank into the project so the bot has context, and it uses it. The interviewer opens with "I saw you led the fraud model rebuild, tell me about the threshold decision." Lovely question, and a fantasy. The real interviewer skimmed your resume eleven minutes ago and retained your employer and possibly your title.

The fantasy removes the skill the round tests. In a real interview you introduce your own material unprompted, without sounding rehearsed, answering a question that did not ask for it. Getting from a generic prompt to your strongest story in one clean sentence is a learnable skill with an obvious failure mode, and you cannot practise it against an interviewer who has already done that work. Rehearse in the fantasy for a week and you walk in having drilled the second half of every answer and none of the first.

The exception is a final round after four conversations, where the panel has read the file and the notes. Tick that box when it is true. It changes the posture: less introducing, more depth on one thread, and an interviewer allowed to say "your second interviewer flagged something about the migration, walk me through it."

---

# The Four Load Bearing Rules

Four rules do more work than every other line in the file. Each prevents a specific failure that is hard to see from inside the run.

**One question per turn, then stop and wait.** Prevents the dodge. Left alone, a model hands you a paragraph containing three questions, because that reads as thorough. In front of three questions you answer the one you have material for and let the others evaporate, and you will not notice. Suppose PM Jordan is asked "tell me about a time you influenced a partner team without authority, and how did you handle it when they pushed back on your timeline." Jordan tells the influence story, warmly and well, and never touches the pushback. In the real round the interviewer asks only the second half, alone, and waits. An early version of this kit stacked questions for four runs before anyone noticed, and the tell was a run log full of good scores while the real interviews kept going badly on follow ups.

**No hints.** Prevents scaffolding from hiding the defect you are testing for. A helpful bot says "you might use situation, action, result here" or "this sounds like a job for your migration story," and each of those deletes a data point. The mock exists to find out whether your cheat sheet, unaided, gets you to the right story in four seconds. If the bot routes you there, you learn nothing about the sheet, and the sheet is under test. Write the rule as a prohibition on naming stories, offering frameworks, and rephrasing the question more helpfully after a pause.

**Grade at the end, not after each answer.** Prevents contamination. Feedback between answers changes who you are performing for, and corrupts the data: your third answer was not an independent observation, it was a reaction to the note on your second.

**Ignore transcription artifacts.** Prevents the feedback budget from being spent on your microphone. If you dictate, and you should, the transcript will contain dropped words and homophones. A grader with no instruction will flag them, and since you get one fix per run, a fix about a garbled word is a wasted run. Write it plainly: grade substance and intent, never how it came out on screen.

---

# Tagged Question Banks

Every question in the bank gets four things.

An **identifier**, short and stable, such as B-07 or CASE-12. Identifiers let the run log record which probes were used, which makes the no repeat rule mechanically possible. Without them the bot has to compare question text across runs, and it will fail at that.

A **topic tag**, one or two words, drawn from the competency model rather than invented. Tags steer coverage, and a tag set that does not match what the round scores is decoration.

A **difficulty tier**, one to three. Tier one is the question as it appears on any list. Tier two adds a constraint or a hostile premise. Tier three is the follow up that arrives after you answer tier two well, usually about the thing you left out.

An **italic grading note**, one line, never read aloud. This is the piece people skip, and it turns a question list into a rubric with questions attached. The note says what a strong answer contains: *a named tradeoff, a number the candidate can defend, and an admission of what the decision cost.* The bot reads it, grades against it, and uses it to decide whether to push. You get consistent grading across runs on the same probe, which lets you compare run four to run one and say anything meaningful.

The bank should be uncomfortably large. A Super Simulator wants forty to sixty probes. It feels like overkill until run five, when the interesting failures start showing up on questions you never expected.

---

# The Remix Engine and the Mode Menu

Without a remix engine, run six is run two with different weather. Four instructions fix that.

**No repeat against the last two runs.** Read the last two run log entries and do not reuse those identifiers. Two runs is the right window rather than all history, because an all history rule eventually empties the pool and retires your best probes for no reason.

**Coverage steering.** Bias this run toward the tags with the lowest count in the tracker. Left random, a question bank hovers around the tags you enjoy, because your enjoyment shows up in how you built the bank. Steering forces the run into the tags you have been avoiding, and those are where the round will hurt you.

**Difficulty climbs within a run.** Start at tier one, end at tier three. Never stay flat. A flat run either warms you up and stops, or throws tier three at a cold candidate and produces a score measuring nothing but that you were cold. The climb also mirrors the real thing, where the hard question is the third in a thread, not the first.

**Roll two dice at the start of every run.** One for interviewer mood: warm and curious, neutral and efficient, distracted and checking the clock, skeptical and pushing on every claim, friendly but running late. One for the opening: straight into a question, two minutes of pleasantries, tell me about yourself, "let's start with your questions for me," or a comment on your background. Mood and opening are where realism lives, because your delivery is not mood invariant, and the skeptical roll is the one where your voice changes.

## Choosing a mode

Modes weight tags and set length. Surprise mix is the default and closest to an unknown round. Domain heavy is for the round the recruiter told you would be technical, or product, or fit. Rapid fire, twelve to fifteen short probes with no teaching, is the crispness trainer and the right mode when your last fix was about length. Curveball adds three tier three probes and a tougher mood, and trains composure rather than content, so do not read its scores as an ability signal. Deep dive on one tag repairs a coverage gap. Full rehearsal is the whole hour at real pacing, worth running once because its value is pacing calibration rather than learning.

---

# Simulating a Panel

The mistake is to build three characters. Build three lenses.

Map each interviewer to one dimension of the rubric. The hiring manager owns judgment, the peer owns collaboration and ways of working, the skip level owns scope and strategic framing. Now every question has a scoring home, and when the run ends you can say which lens you failed rather than which person seemed unimpressed.

Four mechanics make a panel feel like a panel.

**Thread ownership.** One interviewer holds a topic until it resolves, then another picks up. No ping pong. Real panels do this out of professional courtesy, and it matters to you because a thread three questions deep is where you get tested. Ping pong keeps every exchange at depth one, which is comfortable and useless.

**Randomized opener.** Roll who starts and in what order, every run. Otherwise you calibrate to a fixed sequence, and the real round opens with the person you had slotted third.

**Time weighting.** Give each persona a rough share of the minutes and make the bot respect it. If the skip level has fifteen minutes of a forty five minute round, you should feel the compression when they arrive, because that is how it feels when the most senior person in the room has the least time.

**One exception to one question per turn.** Two lenses may react at once when something you said pulls both in, and the bot must say why both are jumping in. It is rare and worth allowing, because it happens in real panels and it is a specific pressure: two people wanting different follow ups from one sentence you should not have said that way.

---

# Adversarial Moves Worth Instructing

A default model is agreeable. Agreeableness is the failure mode that makes homemade simulators useless, and the repair is to instruct the discomfort rather than hope for it.

**Interrupt when the answer runs long.** Not timed out silently at the end, interrupted mid sentence. Real interviewers do it, it is disorienting the first time, and after twice in practice you stop treating it as a verdict.

**Force one compression per run.** "Give me that in fifteen seconds." Fifteen, not thirty. This is the highest yield drill in the file, because it makes you discover what the point of your story was. Most people find out their headline was in sentence nine.

**Push on the weakest claim at least once.** Not the weakest answer, the weakest claim inside a decent answer. The unsourced number, the passive construction hiding who decided, the result that does not follow from the action. Instruct the bot to find it and press, once, rather than moving on politely. Politeness is what makes a mock feel good and teach nothing.

**Quote the candidate's own written material back at them, once per run.** Take a line from the resume or cover letter and ask them to defend it cold. "You wrote that you cut false positives by a third. A third from what baseline, over what window, and who measured it." This is the most predictive drill available, because it is what a real interviewer does with the one document they definitely read. Engineer Alex discovers in run two that a bullet written eight months ago describes a number Alex can no longer source. Better here.

Cap each at once per run. A run where every move fires becomes a hazing ritual, and you learn nothing from a round designed to be unsurvivable.

## Teach and resume

Coaching mode needs one bounded escape hatch: the bot may break character for at most two lines, then return to the interviewer voice without commentary. Two lines is enough to name a structural problem, short enough that it cannot turn into a lesson. The boundary matters more than the content, because an unbounded teaching mode drifts into a tutorial with occasional questions, and the reps disappear.

---

# When a Simulator Is Overbuilt

The simulator is the most enjoyable file in this kit to build. It has structure, it rewards cleverness, and every addition produces a visible improvement in the document. It is also, for those reasons, the best available hiding place from the thing you are avoiding: saying an answer badly out loud and being told why.

Three signs of overbuilding. The bank has grown past sixty probes and you have run three mocks. The persona blocks have grown past four fields because you kept thinking of nuances. You have added a fourth and fifth mode and used neither. In all three cases you are optimizing a test harness with almost no test data, which means optimizing against guesses about your weaknesses rather than measured ones.

The general sign is simpler. If the simulator has more sections than the run log has entries, you are building instead of practising. Nine sections and one run is a hobby. Five sections and six runs is a system.

The repair is not to delete anything. Run what you have, immediately, at whatever quality it is, and let the first two runs tell you which additions were needed. Almost every improvement worth making is one the run log asks for. The ones you invent in advance are, disproportionately, the ones that never fire.

There is a floor as well as a ceiling. Below a persona, a rubric, the four rules, and a dozen questions you have a chat, not a simulator. If you have twenty minutes, spend all twenty reaching that floor and none of them past it.

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

Based on "Simulator Architecture," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
