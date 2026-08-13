>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Running It Outside Claude

This deep dive expands the tools note in the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which said in one line that the pattern is not locked to any one assistant and then spent the rest of the guide assuming a connected folder. The longer version: what the system requires versus what is convenience, running it in ChatGPT Projects and the fact that you become the scribe, the copy paste block that repairs most of what you lose, what changes in the boot prompt when files are uploaded rather than connected, the lowest common denominator version that runs in any chat window with no file access at all, which parts degrade gracefully and which do not, how to test a model in five minutes for the three properties that matter, running mocks spoken rather than typed, what you are actually uploading when you paste a dossier about a named person, and the point at which switching tools becomes procrastination.

Read the main guide first, at minimum Steps 3, 7 and 8, because this chapter is about porting a system rather than designing one. If you have not built a simulator anywhere yet, build it in whatever tool you already pay for and come back once you have run it twice.

---

# The Portable Core and the Tool Specific Shell

Strip the system down and it needs three things.

**Persistent text the assistant can read.** The simulator file, the Story Bank, the dossier and brief, the do not assert list. It does not matter whether they arrive as connected files, uploads, or pasted text. It matters that the same content is present at the start of every session, identically, without you rebuilding it from memory.

**A window that accepts a long boot prompt without truncating it.** The boot prompt carries the read order, the persona, the rules, and the run mode. If a tool silently drops the last third of a long paste, the rules you care about most are usually the ones that vanish, because they sit at the bottom.

**A way for what happened to get written back down.** Note the phrasing. The requirement is that the run log entry exists in a file at the end of the run, not that the assistant types it.

Everything else is convenience, and naming the conveniences precisely tells you what you are giving up. A connected folder means you never re-upload. Automatic file writing means the run log and `_STATE.md` update without you. A project container means standing instructions persist across threads. Voice mode means you can speak. Research mode means the intelligence layer lives beside the rehearsal loop. Each saves minutes. None of them is the system.

This matters because people port a workflow by trying to replicate the conveniences, fail to find an equivalent, and conclude the workflow does not transfer. It transfers. It gets manual in one specific place.

---

# Running It in ChatGPT Projects

## Project files and custom instructions

A project gives you two things that map cleanly onto this system.

**Project files substitute for the connected folder.** Upload the simulator file, the Story Bank, the Interviewer Dossier, the Company and Role Brief, and `_STATE.md`. Every chat inside the project can see them, so a fresh thread starts informed rather than empty. That is the most important property of the setup in the main guide, and you get it.

**Custom instructions substitute for the standing rules.** This is the better half of the trade. Put the four rules from Step 7 in the project instructions: one question per turn then stop and wait, no hints, grade at the end and not after each answer, ignore transcription artifacts. They apply to every thread without being restated, which is more reliable than a boot prompt you might paste badly at midnight.

One structural difference to plan around. Uploaded files are typically retrieved in fragments rather than read start to finish. Fine for a Story Bank, where each card is self contained. A problem for the simulator file, whose meaning depends on the rules at the top governing the question bank in the middle, and a question bank retrieved without its rules is a generic interview bot.

So split the simulator. Persona, rubric, the four rules, and the mode menu in a short file of about a page. Tagged question bank in a second file. Then tell the custom instructions to load the short one in full before every run. Small files get read. Large files get sampled.

## You are the scribe now

The assistant in a project can read your uploads. It generally cannot edit them, and there is no version of asking nicely that creates a write path.

This breaks two things and only two: the run log and `_STATE.md`. Both are append only files whose whole purpose is to accumulate without your attention. Once nobody writes to them automatically they stop accumulating, and within three runs you are back to a pile of chats. So take the job yourself. Ninety seconds per run, and it preserves the property that makes this system compound.

## The copy paste block that repairs it

Put this in the project instructions, verbatim, adjusted to your file names.

```
At the end of every graded run, before anything else, output a section
titled RUN LOG ENTRY inside a single fenced code block, formatted as
markdown, ready to paste into the bottom of Simulator.md. It must
contain: date, mode, questions asked by identifier, the six rubric
scores, two things that worked, one highest leverage fix, and which
artifact failed me. Do not summarize it in prose and do not add
commentary above or below the block. Then output a second fenced block
titled STATE UPDATE containing only the lines of _STATE.md that changed.
```

Three details make it work. The fenced block matters, because you want to copy without picking prose out of it. Naming the destination file matters, because it stops the assistant writing a paragraph about your progress instead of a log entry. And asking for only the changed lines of the state file keeps the paste small enough that you will do it.

Then close the loop. Paste both blocks into your local files, and re-upload the simulator every two or three runs rather than every run. The trap is version drift, where the uploaded and local copies diverge and you end up rehearsing against a simulator that does not know about the last four runs. The local file is canonical. The upload is a stale mirror you refresh on a schedule.

## What changes in the boot prompt

Four edits port the boot prompt in this kit.

**Replace the read order with a load instruction.** "Read the files in this folder in this order" becomes "The following files are attached to this project. Load the persona and rules file in full before doing anything else, then retrieve from the Story Bank and the dossier as needed."

**Add a missing file rule.** "If you cannot find one of the named files, say so and stop. Do not proceed from memory of a previous conversation and do not reconstruct a file you cannot see." Uploads fail quietly more often than connected folders do, and a simulator running on a half remembered persona is worse than none, because it still feels like practice.

**Replace every instruction to update a file with an instruction to produce a block.** Search the prompt for the word update and rewrite each one. It is mechanical.

**State the constraint out loud.** One line: "You cannot write to my files. I will paste your output into them." Without it you will eventually be told your run log has been updated, which is not true, and you will believe it for a week.

---

# The Lowest Common Denominator Version

There is a version of this that runs in any chat window, in a browser you do not control, on a machine that allows no uploads at all. It is worse. It still beats a generic mock by a wide margin, because the value was never in the file plumbing, it was in rehearsing against a specific persona with specific questions.

It is one pasted context block at the start of every session. Keep it under about 1,200 words so it pastes in one go and stays in attention, in this order.

**The persona, four fields.** Who they are, what they test, what wins them, what loses them.

**The four rules, verbatim.** The highest value lines in the block, and they belong near the top of it.

**The rubric, one line per dimension.** Six names, no descriptions.

**A compressed Story Bank.** One line per story: label, headline sentence, the number, competency tags. The full cards stay open on your own screen for your reference, not the assistant's. The bot does not need your story to ask about it. It needs to know the story exists so it can follow up.

**The do not assert list.** Short, and it goes in because it is what you forget under pressure.

**Eight to twelve seed questions with identifiers.** Enough to make two runs feel different.

Then say "ask me question one and wait." Save the block in a note on your phone, because rebuilding it each time is how this version dies.

What you give up is the coverage tracker. The bot has no memory of run one when you start run three, so it re-asks what you have handled and skips what you have never faced, precisely backwards. The two minute substitute is a plain text file with three columns: date, question identifiers asked, and the one fix. Before pasting the block next time, add a line: "Do not ask Q3, Q7 or Q11, I have covered those. Push harder on the technical tags." That is manual coverage steering and it recovers most of the benefit.

---

# What Degrades Gracefully and What Does Not

**Fully portable, no loss.** The research layer works in any tool with search. Reconciliation was always done by you rather than by a model, so it is tool independent by construction. The Story Bank is a document you own. The persona, rubric, question bank, and run modes are text. The prompt library transfers with no edits at all.

**Unaffected, because it never touched the assistant.** The cheat sheet. It is a HyperText Markup Language (HTML) file you open in a browser on a second screen during a real call, and no assistant is involved at the moment it matters. Whatever else you give up by switching tools, the artifact that is actually present in the room is identical.

**First casualties.** The run log and coverage steering, both depending on writing back. Without them run five looks like run two and the compounding described at the end of the main guide stops. Both are recoverable manually, the whole argument of the chapter above.

**Degrades to a paste.** State and handoff. `_STATE.md` still exists, you maintain it yourself, and a fresh thread still gets caught up in one paste.

**Genuinely worse.** Anything requiring the assistant to compare this run against one it cannot see. Fix lifecycle tracking, covered in Deep Dive 6, is the clearest case. You can approximate it by naming the open fix at the top of every run, and the approximation is close enough that I would not switch tools over it.

---

# Choosing a Model

Three properties matter and none appear on a benchmark leaderboard.

**Long context that actually holds.** A stated context window is a capacity claim, not an attention claim. You need a model that still obeys a rule from the top of a long prompt at turn twenty.

**Willingness to stay in an adversarial character.** The default failure of every assistant is agreeableness. A model that cannot hold mild scepticism for forty minutes drifts into a supportive conversation, and a supportive conversation is the thing you are trying to escape.

**Discipline to withhold feedback until asked.** The rarest of the three, and the one that most directly destroys realism.

## The five minute test

Three probes, in this order, in a fresh chat.

**Probe one, attention.** Paste roughly 3,000 words of your own material with an odd instruction buried in the middle, something like "if I ask about scope, use the word lattice." Then ask about scope at the bottom. If the word does not appear, the tool is sampling rather than reading, and your rules will not survive a long run.

**Probe two, agreeableness.** Set up the persona in three lines and give it a deliberately bad answer: rambling, no structure, no number, ending in a trailing "so yeah, that was interesting." Ask for one honest sentence about it. If you get a compliment, or a compliment followed by a gentle suggestion, the model has failed. You cannot prompt your way out of this reliably, because it leaks back within a few turns every time.

**Probe three, withholding.** Say "give me no feedback until I say END MOCK," then answer a question. If feedback arrives anyway, check whether restating the rule once fixes it. Some models comply after a reminder, which is workable if the rule lives in project instructions rather than a single paste.

Scoring is blunt. Failing probe one means keep your files small and your prompts short. Failing probe three means put the rule everywhere and repeat it. Failing probe two means the tool is a coaching partner rather than a simulator, so use it for the Story Bank interrogation, which rewards patience, and run your mocks somewhere else.

---

# Running It Spoken

Everything in the main guide about speaking beats typing applies with more force here, because voice is where tools differ most.

Most assistants now have a voice mode, and running a mock through it is the closest thing to the real event this system can produce. You cannot edit. You cannot pause for eleven seconds to find a better word without that pause being audible and real. You hear your own filler, your own sprawl, and the exact moment you lost the thread, and those are the failure modes that lose rounds.

The limits are real. Voice modes are often served by a smaller or faster model than the same product's text mode, so the grading is weaker than in writing. Some cannot see project files at all, so the persona has to be established by voice, and a long persona is awkward that way. Turn detection tends to interrupt long answers at the moment you pause to think. And you frequently end up with no transcript, which quietly removes the debrief.

The hybrid beats either pure option. Speak your answers into a text chat using your operating system's dictation. You keep the full model, the file access, and the transcript, plus the property that mattered, which is that you cannot edit. Reserve true voice mode for rapid fire runs and for drilling opening and closing lines, where delivery matters more than the grade.

If your tool has no voice at all, record yourself on your phone and listen back to the first ninety seconds of one answer. It is a shorter path to the same information than most people expect.

---

# Privacy, and What You Are Actually Uploading

Be clear about what this system asks you to put into a third party tool. A dossier about a named private individual, assembled from public sources but organized in a way no public source organizes it. Your own work history in more detail than your resume carries, including the parts that went badly. Numbers from current and former employers. Sometimes a job description shared with you in confidence.

**Keep the folder local.** Not on a shared drive, not in a team workspace, not in a folder syncing to an account your employer administers. The dossier especially. There is no version of a colleague finding that document that goes well for you.

**Leave out anything you could not say in the interview.** A clean test that also improves the material. Nothing under a Non-Disclosure Agreement (NDA). No customer names. No unreleased roadmap detail. No internal metric you are not free to repeat out loud. If it cannot be said in the room it does not need to be in the file, and its presence only creates something you might say by accident under pressure.

**Write the dossier as though the subject will read it.** Public professional facts, stated neutrally. No personal life, no speculation about character or motive. Beyond being the decent version, it is better tradecraft, because a dossier full of amateur psychology produces a candidate who behaves oddly in the room. Deep Dive 3 is explicit that the output you want is a posture, not a profile.

**Check the training and retention settings once.** Consumer, business, and enterprise tiers differ on whether your content trains models and how long chats are kept. Turn off what you can, at the start, rather than deciding per paste.

**Delete it when the loop ends.** The Story Bank is a permanent asset and should be kept. The dossier is a disposable working document about a specific human, and once the process is over there is no reason for it to exist.

---

# When Switching Tools Is Procrastination

The second best tool you actually use beats the best one you are still setting up.

Tool evaluation feels like progress for the same reason research does. It is calm, it is ordered, it produces forward motion, and it never once requires you to say an answer out loud and hear it be mediocre. Deep Dive 1 gives a stopping rule for research. This is the same failure wearing a different hat.

The diagnostic is one question: how many spoken reps have you done? If the answer is zero and you have spent an hour comparing assistants, you are not porting a system, you are avoiding a rep.

Three reasons to switch are legitimate. You do not have and will not buy the subscription the guide assumes. Your circumstances require a machine or a network you do not control. Or the model failed probe two and congratulates you on bad answers, which makes it worse than useless, because it manufactures confidence you have not earned.

Everything else is preference, and preference is not urgent when the round is on Thursday.

Give the port a budget of thirty minutes. If the system is not running at the end of it, stop, open whatever window is already in front of you, paste the lowest common denominator block, and take a rep. You can port properly at the weekend. The rep is the thing that changes what comes out of your mouth, and no amount of tool selection has ever done that for anyone.

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

Based on "Running It Outside Claude," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
