>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# What I Learned, Expanded

This deep dive expands the What I Learned chapter of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which stated fifteen lessons in one or two lines each. A lesson stated in one line is a slogan, and slogans do not transfer, because the reader cannot tell whether it came from a real failure or a writing session. The longer version: each of the fifteen with the run or the round that produced it, what it cost, and the edit to a file that came out of it. It closes with the one that has not resolved.

Read the main guide first. Everything here is a footnote to a decision made there. Companies, people, and rounds are anonymized throughout, because none of them agreed to appear in a guide.

---

# The Mock Is a Test Harness, Not a Performance

**The mock is a test harness, not a performance.**

For the first three simulators I graded myself. A bad run meant I was not ready, which produced an evening of feeling behind and zero changes to any file. Twice I stopped a run early because it was going badly, the worst possible response to the only useful information available.

The shift came from a run that fell apart on a question about a stalled dependency. Afterwards I expected to conclude I needed to be better at that kind of question. The duller truth was that my cheat sheet had no card for it. The story existed. There was no line on the sheet that would have found it in four seconds.

So I added one mandatory line to the grading output: which artifact failed you. Not what did you do wrong. Which artifact. From that point a bad run produced an edit with a file name attached, and once a bad run had somewhere to go, I stopped avoiding bad runs.

---

# One Fix Per Run, Not a List

**One fix per run. Not a list.**

My early graded runs produced six to eight corrections each. They were all correct. I saved them, agreed with them, and implemented none. I counted later: more than twenty corrections across four runs, zero closed, delivery unchanged.

This is not a discipline problem. A person can hold one repair in working memory while also constructing an answer under time pressure. Two is already hard. Six is a way of ignoring all six politely while feeling well coached.

So the rubric emits exactly one highest leverage fix, and it is structural rather than advisory: it goes at the top of the next run's prompt, the run opens by naming it, and the bot watches for it.

The second half was a lifecycle. Every fix is open, drilled, or closed, and any fix still open after three runs becomes a document edit instead, on the theory that something I cannot hold in my head after three attempts is a missing line on the sheet rather than a behaviour problem.

---

# One Question at a Time

**One question at a time was the highest leverage rule I ever added.**

My first simulator stacked two questions per turn. That was an accident of how I had written the question bank, in clusters by topic, which the bot read as a single turn. For four runs it asked two things at once and I answered the easier one every time without noticing.

I found it by accident. I put a mock transcript beside one from a real round to compare pacing. The real interviewer asked one thing, waited through a genuinely uncomfortable silence, then followed up on the exact part of the answer I had rushed. My bot had never once made me sit in a silence, because there was always a second question to escape into.

The fix was one line at the top of the run modes: one question per turn, then stop and wait. Nothing else changed. My scores dropped about a point on two dimensions and stayed there, which is the clearest evidence I have that the earlier scores were measuring nothing.

---

# Do Not Grade After Each Answer

**Do not let it grade you after each answer.**

Grading after every answer felt obviously right. Faster feedback, tighter loop, more corrections per hour. I ran it that way for a week.

What happened is that answer two got written for the grader rather than the interviewer. I started announcing structure out loud, saying things like "there are three things here," not because the answer had three things but because the rubric rewarded structure and I knew it was watching. That is visible to a real human and it reads as rehearsed.

The second cost was subtler. Part of what a real round trains is tolerance for not knowing how it is going, and feedback after every answer removes exactly that discomfort.

The repair was two sided. Grade at the end only, and give the useful behaviour a home by adding a coaching mode where breaking character is allowed. Once coaching had its own mode, it stopped leaking into the realistic ones.

---

# Endings, Not Openings

**Endings, not openings.**

I could open any of my five stories cleanly, because the first sentence is the part you rehearse without meaning to. You say it in your head in the shower. It is polished for free.

Around the sixth run the same note appeared for the third time: ran long, headline late, trailed off, interviewer had to reclaim the floor. I went into the files expecting a length problem and found something more specific. Three of the five stories had no last sentence written anywhere. Not a weak one. None. I had improvised the exit every time, and an improvised exit sprawls, because you keep adding qualifications while you look for somewhere to stop.

Every card got a verbatim closing line, shown on the cheat sheet in the same green box as the opener. Then I drilled endings cold: name story four, say its last two sentences, nothing else.

The length problem disappeared within two runs. It had been a landing issue the whole time.

---

# Their Answers Are the Best Intelligence

**The interviewer's answers to your questions are the best intelligence in the entire process.**

After one early round I wrote a careful debrief of what I had been asked and recorded nothing about what they had said. Two days later I built the next round off the job posting, weighted it toward the wrong competency, and walked into a conversation about something else.

In a later loop I did the opposite. Within an hour I wrote down that the interviewer had used the same word for their core problem four separate times, and that their tone flattened when describing a kind of escalation they clearly dealt with too often.

Both went into the next build. The word went into the persona and the brief. The escalation became a question I asked in the following round, which was noticeably easier, not because I performed better but because I was talking about the thing they were living inside.

The debrief template changed as a result. Their answers now come before their questions, because whichever section comes second is the one written badly when you are tired.

---

# Forbid the Bot From Knowing Things You Have Not Told It

**Forbid the bot from knowing things you have not told it.**

My early simulators had my full history in context, and the persona had implicitly read all of it. The bot would ask me to say more about a migration I led, I would answer the follow up fluently, and the run would score well.

The problem showed up live. In a real round nobody knew that project existed, and I discovered at the worst possible moment that I had never rehearsed the thirty seconds of setup that makes it legible to a stranger. In practice I had always started at minute two of that story, because the bot granted me minute one for free.

The constraint block that fixed it is short. This interviewer glanced at your resume for ninety seconds and remembers your current title. Nothing else. If you reference a project you have not introduced, they will interrupt and ask what you are talking about.

Introducing your own background unprompted, briefly, without sounding like a resume recital, is a real skill, and my simulator had been removing every chance to practise it.

---

# Two Research Passes, or None

**Two research passes, or none.**

I carried a claim about an interviewer's previous employer into a room once. It came from a single clean research output, well written, with citations. It was wrong. The pass had merged two people with the same name into one biography, and the version I believed was mostly the other person.

It surfaced in the first three minutes, in the friendliest possible way, and it still cost me the hour. My planned opening was void, and I hedged everything I said about their world afterwards, because I no longer trusted my own preparation and it showed.

Deep Dive 1 has the repair in full. The number that changed my behaviour was this: once I ran a second pass in a different vendor and sorted claims into agreed, contradicted, and unverified, the agreed bucket came out at roughly half of what the first pass had asserted with a straight face. Not half wrong. Half uncorroborated, which is exactly the set I would previously have said out loud.

---

# Write Down What You Are Not Allowed to Say

**Write down what you are not allowed to say.**

I struck an unverified claim out of a dossier and considered the matter handled. Forty minutes into a mock, under mild pressure, I said it anyway, in a sentence I had not planned. The bot did not catch it. I caught it on the transcript afterwards.

Deleting a claim removes it from the document and leaves it in your head. Under pressure you reach for whatever is available, and what is available is what you read four times last Tuesday, not what you deleted on Wednesday.

So the do not assert section exists, with each struck claim written out and a rehearsed substitute beside it. The substitution always runs the same direction, turning the claim into a question. "I read that your team owns the risk platform" becomes "I could not work out from the outside where ownership splits, is that on your side."

It has stopped three confident errors about people I had never met, and two of the substitutes produced a better conversation than the fact would have.

---

# Written Permission to Say I Do Not Know

**Give yourself written permission to say "I do not know."**

I was asked a regulatory detail I did not know. I produced something directionally reasonable, delivered with confidence, and the follow up took about eight seconds to expose it. The temperature of the room changed and did not change back.

The instructive part is that I had not decided to bluff. Nobody decides to bluff. I hit a gap, felt the silence, and improvisation filled it, because improvisation is what happens when there is no prepared alternative.

So the alternative got prepared. On the cheat sheet, in the same green box as the opening lines, sits a verbatim sentence: I do not know that, and I do not believe it is public. Here is how I would find out, and here is what I would do while I waited.

It has to be written down, because the failure mode is improvisation under silence and only a written line competes at that moment. It also reads as senior. Bluffing has never once survived a follow up.

---

# Watch for Overcorrection

**Watch for overcorrection.**

I drilled lead with the outcome for four consecutive runs. It worked. My answers got faster to the point and the scores moved.

On run five I was asked an open question about how I think about a category of problem, and I opened with a number. It landed badly, and correctly so, because the question wanted a way of thinking and I answered with a result. The grading note said, in effect, do that less, which is the least useful instruction in coaching, because it gives you no way to tell when to do it.

That was when I understood that every drilled behaviour eventually fires on the wrong trigger, and more repetition makes it worse, because repetition built the reflex.

The repair is a discriminator. Lead with the number when the question contains tell me about a time, or asks about impact. Lead with the frame when it contains how do you think about. Any fix still live after three runs now gets one written for it.

---

# Say It Out Loud

**Say it out loud.**

For the first two weeks I typed my mock answers. The scores were good.

Then I did a real round and ran long, buried the headline three sentences deep, and trailed off without landing. All three failures were invisible in every typed run, for a mechanical reason. Typing lets you edit. You delete the false start, reorder the middle once you see how it reads, and add the number you forgot. What you produce is a written answer, you grade the written answer, and then you walk into a room where none of those repairs exist.

I switched to dictation only. The first spoken run scored a full point lower on communication and presence, and that was the first honest reading the system had ever given me.

One companion change was necessary. Dictation produces garbled words and wrong homophones, and left alone the bot spends its feedback budget on your microphone. The rule is explicit: grade substance and intent, never flag a transcription artifact.

---

# Space the Reps

**Space the reps.**

The night before an early round I ran five mocks in one evening. By run four the answers came out smoothly and I went to bed feeling ready.

The next day, under real pressure, retrieval was worse than it had been at eleven the previous night. Pauses where I had been fluent, and one story where I could not find the number. What I had measured the night before was recognition, not recall. I had been reading the sheet immediately before each run, so every answer was a lookup rather than a retrieval, and lookups feel identical to knowing.

The rule now is three runs across three days, one per evening, each one cold. The sheet gets read after the run, when it is being edited, never before, when it is being used as a crutch.

The runs feel worse this way, especially the first one after a day off, and that is the point. The gap is where the work happens.

---

# Building It for Someone Else Exposed Everything

**Building it for someone else exposed everything I was getting away with.**

Engineer Alex asked me to build a simulator for a round of theirs. I said yes expecting to spend an hour, because I had built seven and the process was routine.

Alex got stuck in three places inside twenty minutes. My boot prompt was four lines, because I already knew the read order and had never written it down. My rubric had no instruction for an answer that was strong but slightly off the question, because I had resolved that case by judgment every time without noticing. And the Story Bank template silently assumed the reader had their raw material in front of them, which was true for me and for nobody else alive.

None of those were findable by rereading my own files. They were invisible precisely because my head was patching them.

The result is Deep Dive 9: an onboarding file under two pages, placeholders written as instructions to the assistant, and a boot prompt written for someone who has never read the guide.

If you want to know whether your system is real, hand it to someone and watch where they stop.

---

# The Stories Are the Asset

**The stories are the asset.**

By the fourth build, setup was under an hour and the only part that still took real time was the story work. That should have told me something sooner.

Everything else churned. Companies changed. Personas changed completely between rounds. The rubric had two dimensions renamed and one replaced. Question banks were rebuilt per round type. The cheat sheet went through five versions in a single loop.

Seven stories stayed. Two of them I have now told in five different rounds, and they are substantially better, not because I polished the wording but because five interviewers pushed on five different weak points and each push produced one edit. A missing decision. A number that could not survive a follow up. An ending. You cannot get that from writing. It only comes from being asked.

So the Story Bank moved out of the round folder to the top level, with each round folder linking to it rather than copying it. Copies fork, and a forked Story Bank means the improvement from round three never reaches round four.

---

# The One That Has Not Resolved

Two, honestly, and a lessons chapter claiming everything was solved would not be worth reading.

**Calibration.** My simulator's scores are internally consistent. A 4 in run six means roughly what a 4 meant in run three, and I got that far by writing anchor examples of a 2 and a 4 for each dimension into the rubric. What I do not know is whether a 4 from my simulator corresponds to anything a real panel would call a 4. The only ground truth is outcomes, and outcomes are sparse, delayed by weeks, confounded by everything from headcount to whoever else applied, and delivered without detail. I have no honest mapping from my scores to reality and I am not sure one is available at an individual scale, so I treat them as a within system signal only: useful for direction and trend, useless as an absolute reading of readiness. That is a workaround, not a solution.

**Rapport.** Every round I have lost that I could diagnose was lost on connection rather than content. The answers were fine. The room did not warm up. A bot playing a sceptical peer reproduces the questions, the interruptions, and the pressure, and it cannot reproduce whether a stranger finished the hour wanting to work with me. So I use human mocks for that, rarely, with people who will tell me the truth, and I accept that the system covers content and delivery and not chemistry.

If you solve either one, I would genuinely like to know.

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

Based on "What I Learned, Expanded," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
