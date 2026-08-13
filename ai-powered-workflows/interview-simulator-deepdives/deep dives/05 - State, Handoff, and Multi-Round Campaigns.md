>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# State, Handoff, and Multi-Round Campaigns

This deep dive expands Steps 3 and 10 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which told you to create an anchor file at the start and write a handoff file at the end, in about a dozen lines each. This is the longer version: why state belongs in files rather than chat threads, the anatomy of the anchor file and why the mutable banner at the top overrides everything below it, locked decisions as the anti relitigation section, accuracy guards, the read order as a version controlled artifact, the update contract that ends every session, when to write a handoff file and what the load bearing section in it is, the debrief and why the interviewer's answers to your questions are the most valuable intelligence in the process, how one round seeds the next, and when to stop maintaining any of it.

Read the main guide first, at minimum Steps 1 through 3. This chapter assumes you have a folder for the round and at least a partly filled anchor file, because everything here is about keeping a system alive across many sessions rather than starting one.

---

# Why State Lives in Files

Chat threads die. They run out of context, the window closes, the application restarts, or you come back on Thursday and the thread that knew everything about your round has been pushed off the bottom of the list. Everything the assistant learned evaporates: the panel composition you confirmed with the recruiter, the four framings you rejected and why, the number you corrected downward because you could not defend the original, the three probes you already drilled.

The usual reaction is to rebuild it by talking. That is the expensive part. Reconstructing context in conversation takes twenty to forty minutes and comes back subtly wrong, because you are recalling under time pressure rather than reading. You will forget one of the rejected framings and cheerfully adopt it again. You will remember a locked decision backwards.

Files fix this for a boring reason: a file is the same on Thursday as on Monday, and a fresh thread reads it in seconds. The design principle of this kit follows from that one property. The assistant is a process. The folder is the memory. Anything that matters after the window closes must be written down before it closes, and the anchor file is where those things live.

There is a second benefit that shows up later. A file can be read by a different tool, model, or person. A chat thread cannot. If you switch assistants mid loop, or hand the folder to a friend helping you prepare, the folder transfers and the conversation does not.

---

# Anatomy of the Anchor File

The anchor file is named `_STATE.md` so it sorts to the top of the folder. It is the first file every thread reads and the last file every thread updates. It holds twelve things: the mutable banner, the round facts, locked decisions, accuracy guards, the short do not assert list, story coverage, question bank coverage, recurring fixes, artifact versions, the file inventory, the run log, and the read order for the next thread.

## The banner at the top

The first line under the title is a banner saying where this is: what just happened, what happens next, and what a fresh thread must not do yet. One line, rewritten after every milestone, and it explicitly overrides anything stale below it.

The banner exists because of a specific failure. Everything below it accumulates. Sections written on Monday sit next to sections written on Friday, and nothing in the formatting tells a reader which is current. A fresh thread reading the whole file treats a Monday section as live and helpfully offers to do work you finished on Wednesday. The banner is the one place guaranteed current, and the rule that it wins over anything below makes the rest of the file safe to let go stale.

Write it concretely. Not "in progress." Something like: "Two mocks run, cheat sheet at version two. Next is one more mock focused on the failure story. Do not rebuild the question bank." The third clause saves the most time, because the most expensive thing a fresh thread does is enthusiastically redo a finished artifact.

## Locked decisions

A table of things you have already settled, each with a date. The lead story for scope questions is Card 3, not Card 1. The opening is thirty seconds, not ninety. The compensation question gets deflected once and then answered with a range.

This is the anti relitigation section, and it saves more time than anything else in the file. Every fresh thread, being helpful and having no history, proposes alternatives to decisions you made two days ago after twenty minutes of thought. Without this table you re argue each one, sometimes reversing a decision you already reversed in the other direction. A decision with a date next to it is closed, and closed is the point.

Lock things when they stop changing, not when you first decide them. A decision logged during the first thread and reversed in the second was never locked, it was a preference. The good ones tend to arrive after a mock, because a mock produces evidence and evidence is what ends an argument.

## Accuracy guards

A short list of facts you have to keep straight under pressure. Two categories matter most.

Numbers that belong to one role and not another. If you have two roles where you reduced something by a large percentage, your brain will cross them under pressure and attach the bigger number to the more impressive employer. Write the guard: this figure belongs to the second role, never the first. Getting this wrong in a room is unrecoverable, because the interviewer cannot tell whether you misspoke or inflated, and has to assume the worse one.

Credentials that are past tense. A certification that lapsed two years ago is still a real credential and still worth mentioning, in the past tense, with the dates. Present tense turns a true statement into a false one, and the check is trivial for anyone who cares to run it. Write the guard as the exact phrasing: "was certified from this year to that year," never "I am certified."

Every entry in this section exists because you nearly got it wrong once. That is the qualification for inclusion. Do not populate it with hypotheticals.

## The read order

The last section tells the next thread what to read, in what order, and what to do first. It is a small thing that behaves like a version controlled artifact: it changes as the round progresses, and the change is meaningful. Early in the build, the read order points at the research brief and the Story Bank. The night before, it points at the cheat sheet and nothing else, because reading the fifteen page brief then is the wrong activity, and a fresh thread does not know that unless you tell it.

---

# The Update Contract

Every session ends by updating state. Not most sessions. Every one.

This is a habit rather than a technique, and it is the difference between a system and a pile of chats. The instruction is one sentence at the end of a session: update the anchor file. What gets updated is small and specific: the banner, because something changed; any decision that hardened into a lock; any new accuracy guard you nearly tripped over; the coverage counts if you ran a mock; the artifact version table if you edited a document; and the read order for the next thread.

The run log is the exception to the rule that you write the file. The bot appends after every mock and you do not touch it, because a log you edit is a log you have started curating, and its value is that it contains the runs you would rather forget.

Two failure modes are worth naming. The first is updating at the start of the next session instead of the end of the last, which does not work, because the information you needed was in the previous context window and it is gone. The second is updating with summaries instead of specifics. "Made good progress on the Story Bank" is not state. "Cards 1 through 4 have hardened numbers, Card 5 has no result metric yet and is the blocker" is state, because the next thread can act on it.

---

# Handoff Files

A handoff file is different from the anchor file. The anchor holds the durable state of a round. A handoff is written when a working thread is running out of context and holds unfinished work that has not made it into files.

Write one when the thread is running out of room, not on a schedule. A handoff written every session is a chore producing near duplicate documents nobody reads. One written when a long build thread is about to die saves the four hours you just spent.

The load bearing section is the full record of questions asked and answers given inside that thread. When you build a Story Bank properly, the assistant interrogates you, and you answer dozens of focused questions about numbers, roles, decisions, and what happened. Those answers are the raw material and most never appear verbatim in any output file. If the thread dies without recording them, the next thread asks the same questions again, and you answer slightly differently the second time because you are tired, which introduces inconsistency into material that has to be consistent.

So the handoff carries: the question and answer record in full, the decisions made and the reasoning behind them, the alternatives considered and rejected with the reason, anything the user corrected the assistant about, and the exact next action. The rejected alternatives matter more than they look, because without them the next thread proposes the rejected option within ten minutes.

Everything else in a handoff is compressible. The question and answer record is not. When in doubt about length, cut the narrative summary and keep the transcript of what you actually said about your own history.

---

# The Debrief

The interview ends, you get a wash of relief or dread, and the most valuable intelligence you will ever have starts decaying at a rate most people badly underestimate. By tomorrow morning the exact phrasing is gone. By the weekend, half the sequence.

**Do it within a few hours.** Not the same week. The same evening. Write the questions in the order they were asked, as close to verbatim as you can manage, including the follow ups, because the follow up is where the interviewer told you what your first answer was missing.

**Log what was not asked.** This is signal and almost nobody records it. If you prepared four competencies and one never came up across a full hour, that means one of two things: it is not weighted in this round, or it is saved for the next. Both change what you build next. A silent competency in a hiring manager round very often means the peer round owns it.

**Mine their answers to your questions.** This is the highest value material in the process, better than the job posting, better than two passes of deep research, better than anything the recruiter told you. When you asked what the hardest problem on the team is right now, they answered honestly, in their own vocabulary, unrehearsed. Write down how they described the team, what they said was hard, which words they repeated, what they sounded tired of, and what they got animated about. That is next round's build specification and it has a shelf life measured in hours.

**Send yourself a recall questionnaire a day later.** Have the assistant produce eight to ten short prompts and answer them cold the following day: what was the second question, what did you say that you wish you had not, what did they push back on twice, what did they write down. Roughly a third of the round comes back once you stop trying to retrieve it. This is the cheapest intelligence in the kit and it takes six minutes.

**Promote what worked.** Any answer that landed gets marked as locked in the anchor file, with the phrasing. Otherwise a future thread, trying to be helpful, rewrites your best answer into something more polished and less yours, and you will not notice because the new version reads well on the page.

---

# Multi Round Campaigns

One folder per round, not per company. This is the structural decision that makes the rest work.

The instinct is to keep one folder per company and add files as the loop progresses, and it fails within two rounds. The panel changes, the format changes, the cheat sheet changes, and you end up with three simulators, two cheat sheets, and one anchor file describing whichever round is most recent, all in one place, and no thread can tell which is live. Separate folders make the round the unit of state, which is what it is.

**Round one's transcript is round two's build specification.** Everything in the debrief converts directly. The questions asked tell you the house style, worth more than any general guess about the company's interview philosophy. The competencies not asked tell you what is still coming. Their answers to your questions tell you the vocabulary and the current pain. Their pushbacks tell you which claims do not survive contact. Build round two's simulator from that file first and the research second, because the transcript is primary evidence and the research is inference about the same thing.

**Carry an already drilled list forward.** Copy the probe identifiers and the stories you used in round one into the new folder as a do not reuse list. Two things happen without it. Your simulator asks the same questions again, which feels productive and teaches nothing, and more importantly, you walk into round two with the same three stories, in front of a panel that has read the round one notes. Repeating a story to a second interviewer is fine and often correct. Having only the same three available is a visible ceiling. The already drilled list forces the next reps onto fresh ground, usually the fourth and fifth cards you have been avoiding.

**Create the next round's stub before you know who is in it.** The moment round one ends, make the folder for round two with a stub anchor file holding what you already know: the loop structure the recruiter described, the competencies that did not come up, the vocabulary you harvested, and the questions you plan to ask next time. All of it is knowable before the interviewers are named. Ten minutes on the evening of round one, while the material is fresh, and the day round two gets scheduled you are half built rather than starting from a blank folder under time pressure.

**Keep artifact version history and never edit version one.** When the cheat sheet changes, copy it to version two rather than editing in place, and record in the version table what changed and which run caused it. A few seconds, and it buys two things. You can see the shape of your own improvement, which is motivating in a week where the runs feel flat. And when a change turns out to be wrong, and some will, you can go back to the version before it rather than reconstructing from memory what the card used to say.

---

# When to Stop Maintaining State

State maintenance has a real cost, and past a point it becomes another form of the same avoidance that produces overbuilt simulators. Three stopping rules.

**Stop maintaining a file nobody reads.** If the coverage tracker has not changed the mode of a single run, it is steering nothing and you are updating a table out of tidiness. Either let it choose your mode or delete it. Every section in the anchor file should point at a decision it changed.

**Stop when the round is over and the outcome is known.** The day you get the offer or the rejection, the folder stops being a working system and becomes an archive. Do one final pass, then close it.

**Stop updating in the last twenty four hours.** The night before the round, the only file that should change is the cheat sheet, and only if a rep exposed a hole in it. Updating the anchor file at eleven at night the day before is not preparation, it is anxiety with a text editor.

What to throw away when the process ends, and what to keep, is worth deciding deliberately rather than by neglect. Throw away the round specific simulator, the question bank tuned to one panel, the research brief about a company you are no longer talking to, and the run logs, once you have extracted the pattern. Keep four things: the Story Bank cards, updated with anything the round taught you about how they land out loud; the recurring fixes list, a catalogue of how you specifically fail and the most transferable thing you own; the harvested vocabulary and the questions that worked, because both generalize across companies in the same space; and the debrief itself, because if this company comes back in eighteen months you will want the record of what they asked.

Then fold what you learned back into the layer underneath, your Career Brain Trust, and delete the rest without ceremony. The folder was scaffolding for one event. The stories, and the honest list of how you fail, are the part that was ever going to compound.

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

Based on "State, Handoff, and Multi-Round Campaigns," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
