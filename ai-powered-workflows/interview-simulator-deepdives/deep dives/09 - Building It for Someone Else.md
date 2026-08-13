>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Building It for Someone Else

This deep dive expands the whole of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md) for a different reader: the person building a simulator they will never run. Every step in the main guide assumes the builder and the candidate are the same human. When they are not, several things quietly stop working. This covers which ones. Why story mining moves from build time to run time, the onboarding file and the four setup frictions, placeholders written as machine readable instructions, the constraints the bot has to enforce, the boot prompt in their voice, the refusal contract stated twice, the authorship handoff, and what the exercise teaches you about your own system.

Read the main guide first, and ideally build one for yourself too. This chapter is about the differences, and they only make sense against the version you have run.

---

# Their Stories Live in Their Head, Not in Your Files

This is the whole problem, and everything else follows from it.

When you build for yourself, the Story Bank is the slow part but a build time activity. You sit down with your own material, your own numbers, your own memory of what you decided, and write it. The simulator arrives complete.

When PM Jordan builds a simulator for Engineer Alex, the intelligence layer transfers perfectly and the Story Bank not at all. Jordan can research Northwind Payments, read the interviewer's public work, reconstruct the competency model, and build a persona, none of which needs Alex present. Jordan cannot write Alex's stories, because Jordan does not know what was broken, what Alex decided, who pushed back, or what the number was before. A resume gives you the shape of a story and none of its load bearing parts.

The naive response is to interview them for two hours and then build. That fails because the detail is not retrievable on demand. Ask Engineer Alex what they are proud of and you get a summary. Ask what the queue depth was before the change and the answer surfaces, but only when the question is that precise, and you cannot ask two hundred precise questions in advance because most come out of earlier answers.

So relocate story mining from build time to run time. Ship a simulator whose first behaviour is to interview them. Not as a warm up, as the actual first task. The Story Bank arrives as scaffolds with the unknown parts marked and questioned, and the bot fills them by asking in small batches.

Two consequences follow. Quality now depends on a conversation you will not be in the room for, which makes the instructions governing it the most important thing you write. And the artifact is deliberately incomplete, which you have to explain, or it reads as unfinished.

---

# The Onboarding File Is the Only Thing You Can Assume They Will Read

You will write ten files. They will read one, standing up, on a phone, about nine minutes before they intended to start. Design for that.

The onboarding file, called `00_START_HERE.md` in this kit, has three non negotiable properties.

**Under two pages.** Not two pages of dense reference, two pages of instructions. Longer and the reader does not read the last part, they read none of it, because length signals a project rather than a task. Anything you are tempted to add belongs in a file they consult later, or nowhere.

**It contains the literal paste string.** Not a description of what to tell the assistant. The actual text, in a block, that they select and copy. Every instruction requiring the reader to compose something is a place they can stall, and stalling at step three means the build is never used.

**It promises a time to value.** Say "setup takes about three minutes" at the top, then make it true. That is a scoping statement, not a motivational flourish. Someone who does not know whether this is a three minute task or a three hour one will not start it on a Tuesday evening, and Tuesday evening is when they have time.

Then write it in their name, for their round, order it by what they do rather than what things are, and put the table of contents last, because reference at the top reads as homework.

---

# The Four Setup Frictions

Four things go wrong, every time, with every person. Solve all four explicitly. Assume nothing.

**Where to put the folder.** Left unaddressed, it stays in the downloads directory or, worse, zipped and opened in a preview window showing one file at a time. Say it plainly: move the whole folder somewhere you can find it again, your documents folder is fine. Naming an acceptable location removes a decision, and removing decisions is what this file does.

**Keeping the files together.** People open a zip, see a markdown file they recognize, and drag that one out. The system then fails confusingly: the assistant reads a simulator referencing a state file that is not there. One sentence prevents it: keep all the files together, they reference each other by name.

**Connecting the folder rather than uploading it.** This breaks the most builds and is the least obvious. Uploading gives the assistant a snapshot. Connecting gives it read and write access to a living directory, and the memory design depends on write access. Someone who uploads gets a bot that works for one session then forgets everything, and blames the system rather than a setup choice. Say it in the imperative and say why: connect this folder so the assistant can read and write here. Connected, not uploaded.

**Exactly what to paste.** One line, in a quoted block, unchanged. Then tell them the thing they will not guess: they paste it again at the start of every new session, because a new chat has no memory of the last one, and the files are the memory.

None of these four are interesting, and none appeared in the version you built for yourself, because you already knew them.

---

# Placeholders as Machine Readable Instructions

Here is the design idea that makes a third party build work at all.

An incomplete artifact is usually a liability. A Story Bank card with a blank where a number should be looks unfinished, and the reader cannot tell whether it is an oversight or a question. But a blank with a marker and a specific question beside it becomes an instruction.

The convention in this kit is a `NEEDS REAL DETAIL` marker, and it never appears alone. It always carries the exact question that would fill it.

`NEEDS REAL DETAIL: what was the queue depth before you changed anything, and how did you measure it`

`NEEDS REAL DETAIL: who disagreed with this call, what was their argument, and what happened`

That reads as a question to the human and parses as a task to the model, which makes the incomplete Story Bank the bot's first task list. You do not need a separate script telling the assistant what to ask, because the questions already sit in the artifact.

The instruction you do write is short and goes in the simulator file: before running any mock, collect every `NEEDS REAL DETAIL` marker and work through them in batches of two to four questions, one card at a time. Do not proceed until the top three cards are complete. Batching matters, because twenty questions at once is a form, and forms get filled in with summaries.

Tell the person receiving it that the kit ships deliberately unfinished and completes itself through conversation. Say exactly that. Otherwise the first thing they see is a document full of gaps with their name on it, and the reasonable conclusion is that you did not finish it.

## Never invent their numbers or their decisions, and say so in the file

The temptation, when their resume says they reduced processing time, is to write a plausible number. It takes four seconds, and it is the most damaging thing you can do to this build.

The first reason is direct. An invented number gets said out loud in a real interview by someone who cannot defend it, and it will not survive the follow up, which is always about how it was measured. They will not remember it came from you. They will experience it as their own memory failing.

The second is underrated. If any part of what you hand over might be invented, all of it has to be checked, and none of it can be relied on under pressure. The value of a `NEEDS REAL DETAIL` marker depends on the reader believing everything unmarked is real.

So state the guarantee explicitly, in one sentence they will read: nothing in your Story Bank was invented, so if a line says `NEEDS REAL DETAIL`, that is a question, not a claim. That is what lets them use the thing at speed.

---

# Constraints the Bot Has to Enforce on Them

A self build assumes self discipline. You wrote the rules, so when you break one you notice. A third party build outsources that discipline to the bot, because the person running it did not write the rules and has no attachment to them.

So several things that live in your head have to become enforced behaviour in the file.

**Refuse to start mocks before intake.** The commonest failure of a handed over build is that the person says "run a mock" immediately and the bot obliges against a Story Bank full of markers. The mock is useless and teaches them the system is shallow. Write the refusal in: if the top three cards still contain `NEEDS REAL DETAIL`, say so, and offer to fill them first.

**Enforce out loud.** Nobody dictates unless told to, every time. Put it in the run opening as a question rather than a lecture: are you saying this out loud or typing. If typing, say once what it costs, then run anyway, because a bot that refuses gets abandoned.

**Enforce one fix.** Left alone, a model produces a list, because a list looks thorough. Someone who built the system knows to take one item. Someone who did not will take zero. Write it as a hard output contract: six scores, two things that worked, one fix, nothing else.

**Ask for the state update rather than waiting to be asked.** You remember to say "update state" because you know the memory is in the files. They do not.

**Hold length.** Someone new to this will run eleven minutes on the first answer and not know that is a problem. Have the bot report answer length for the first two runs regardless of the rubric, because length is the fastest thing to fix and the least likely to be self detected.

The general principle: anything you do by habit has to become a line in a file.

---

# The Boot Prompt in Their First Person, and the Refusal Contract Stated Twice

## Write the boot prompt as though they wrote it

The kickoff prompt is the block they paste into a fresh thread. Write it in their voice, in the first person, so it can be pasted without a single edit.

The failing version reads like documentation: "the candidate should be asked whether they want coaching mode or realistic mode, and the assistant should then begin." That requires translation, and translation requires understanding the design, which they do not have and should not need.

The working version reads: "I am preparing for a technical deep dive at Northwind Payments. Read `_STATE.md`, then `Simulator.md`, then `Story Bank/INDEX.md`. Ask me the two scoping questions, then start. One question at a time, no hints, grade at the end."

Same content, zero friction. Use their round and their company by name rather than placeholders, because an unreplaced placeholder in a paste block is the likeliest single point of failure in the handover. Put it in its own file with nothing else in it.

## State the refusal twice, once to them and once to the model

The system has one rule that matters more than the rest, and it goes in two places, because the two audiences can each break it independently.

**To the model, in the simulator file.** The assistant must not write the candidate's stories, must not supply their thesis on why this company, must not propose numbers, and must not fill a `NEEDS REAL DETAIL` marker with anything the candidate did not say. If asked to draft a story, it declines and asks the questions instead. This has to be explicit, because a helpful model asked to help will help.

**To the person, in the onboarding file.** Tell them the bot will not write their material, tell them it is deliberate, and name the failure mode plainly rather than gesturing at it.

The plain version is this. A story someone else wrote for you survives about two follow up questions. It survives the first, because the summary is memorized. It does not survive the second, which is always some version of how did you measure that, or what was the alternative, or who disagreed. You will find this out in minute forty of a real interview, in front of people whose entire job is noticing exactly that, and there is no recovery inside the same hour.

Say it that concretely. A soft version, something about how it works better when the material is authentically theirs, gets read as encouragement and ignored. The image of minute forty is what makes someone answer the intake questions properly.

---

# The Authorship Handoff, and Offering Live Help

There is a moment, usually right after the intake conversation, where ownership has to move from you to them, and if it does not the whole thing quietly fails.

Before that moment they are receiving something. After it, they are running something. The line to give them is the one that closes the main guide: the research makes you fast and hard to rattle, the judgment has to be yours.

Underneath that sentence is a real division. You supplied who is in the room, what the round is scoring, a persona that behaves like the real thing, and a structure that turns their experience into spoken material. You did not supply the experience, the decisions, the numbers, or the opinion about why this company. Those cannot be transferred.

Make the transfer concrete rather than sentimental. After the intake conversation, tell them to sharpen the headline on their top card, in their own words, and say it out loud once. That converts them from a recipient into an author.

**Offer live help, and be specific about what kind.** The offer that works is narrow: sit in on one mock, listen, and say nothing until the end. Not to add feedback the bot already gives, but to do the one thing it cannot, which is tell them whether they sounded like themselves.

What not to offer: to fix the sheet for them, to rewrite a story after a bad mock, or to be on standby the night before. All three feel generous and all three take the artifact back off them at the moment they need to own it.

---

# What Handing It Over Teaches You About Your Own System

The reason to do this, beyond helping someone, is that it is the only reliable audit of your own build.

Every part of the system that lived in your head instead of in the files shows up within twenty minutes of watching someone else use it. Not as an insight, as a question in a message: where do I put this, do I have to paste that every time, is it supposed to have blanks in it. Each is a defect you have carried for months and could not see, because you were compensating for it automatically.

The pattern is consistent enough to expect. The things that break are never the clever parts. Nobody has ever struggled with the persona or the rubric. What breaks is the folder connection, the boot string, the assumption that "run a mock" means the same thing to a new reader as to you, and the absence of any statement about what to do first.

There is a sharper version of the lesson. When you build for yourself, you cannot tell a system from a habit, because both produce the same result. Handing it over separates them. Anything that survives the transfer was a system. Anything that does not was a habit you had mistaken for a design.

The practical move is to turn every question they ask during setup into a line in the template immediately, while you still have the exact wording of their confusion. Not a paraphrase, the sentence that would have prevented the question.

---

# When Not to Build One for Someone

Not every offer to help should turn into a folder, and the restraint here matters more than anywhere else in this kit, because this is the one where the failure lands on somebody else.

**When they have not asked.** The main one. An unrequested simulator arrives as a comment on how their preparation is going, however it is framed, and it lands on someone already anxious and probably already behind. It also creates an obligation: now they have to use it, or explain why they did not. Offer, describe it in two sentences, and let them ask. If they do not ask, they have answered.

**When the interview is in two days and they have not started.** Two hours of you asking precise questions about their three best stories, plus one page of headlines and closing lines, will do more than a folder they have to learn to operate.

**When they want the outcome rather than the practice.** Some people asking for help with an interview are asking for reassurance, or for material, or for someone to tell them they will be fine. The system does none of those and will feel like homework. Find out which you are being asked for before you build.

**When you cannot be neutral about the outcome.** If you referred them, if you would be their manager, if you want this more than they seem to, you will over build and start writing the parts they should write. Notice the impulse and hand them the public kit instead.

**When their round is one you do not understand.** You cannot build a credible persona for a function whose failure modes you have never seen. Build the scaffolding, load the matching question bank, and say plainly which parts you were guessing at.

Then the distinction underneath all of these. Helping is supplying the parts they cannot make quickly: the research, the format, the persona, the structure, the enforcement. Taking over is supplying the parts only they can make: the stories, the numbers, the reason they want this job. The first makes them faster. The second makes them fluent in material they cannot hold, which is worse than being slow, because slow is survivable in an interview and hollow is not.

The clean test is what happens if you disappear. If they can still run the system, still fill their own gaps, still tell their own stories under follow up, you helped. If the artifact stops working without you, you built something for yourself and put their name on it.

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

Based on "Building It for Someone Else," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
