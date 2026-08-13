---
name: round-debrief
description: Use this skill whenever the user has just finished a real interview round and wants to capture it, mine it, and turn it into the specification for the next round. Trigger phrases include "I just had my interview", "debrief my round", "let us capture what happened", "the panel just ended", "here is what they asked me", "help me remember the interview", "what does it mean that they never asked about X", "write the handoff for the next round", and "they told me the next round is with two more people". Always trigger when the user is describing an interview that has already happened, in the past tense, and wants it recorded or interpreted, even if the exact wording differs. Do NOT use this skill for gathering research before a round, which is the interview-research skill, for building or running a practice mock, which is the interview-simulator skill, or for producing and versioning the glanceable HyperText Markup Language cheat sheet, which is the cheat-sheet-builder skill.
---

# Round Debrief skill

This skill turns a fresh memory of a real interview round into a written debrief, a set of locked answers and accuracy guards, and a handoff file that seeds the next round's build.

The workflow has 9 steps. Run them in order. Steps 1, 5, 6, 7 and 8 pause for the user. Steps 2, 3, 4 and 9 run without stopping.

Timing is the whole game here. The interviewer just told the user what the team cares about, in their own words, answering the user's questions. That is the next round's build specification, and it has a shelf life of about a day.

---

## Step 1: Capture within hours, questions in the order actually asked

Open by telling the user how this works and how long it takes, because a person who just walked out of a round has low patience and high value information.

Ask for the round basics first, quickly. Company, round label, date, who was in the room with their titles, format, and length.

Then get the question list. This is the priority capture and it comes before everything else, including how the user felt about it.

**Order matters and must be preserved.** Ask for the questions in the sequence they were asked, as close to verbatim as the user can manage, numbered. The sequence is diagnostic on its own, because people front load what they are screening for. A round that opened with a scope question and reached motivation at minute forty tells you something a reordered list would hide.

NEVER reorder the question list into topic groups. NEVER clean up the interviewer's phrasing into a tidier version of the question. The clumsy real wording is the data. "So, like, walk me through a time something you shipped did not work" and "tell me about a failure" are not the same question, and the difference changes which story routes to it.

Also capture the tone read while it is fresh. Their energy, the moment the energy changed and what changed it, whether it felt like a screen or a conversation, and anything about the setup worth recording such as running late, camera off, a second person joining.

PAUSE HERE. Wait for the user to give the question list and the tone read.

---

## Step 2: What landed and what was shaky

Two lists, both specific, both blunt.

**What landed.** Only moments where the user saw a reaction. A note taken, a follow up asked, a "that is exactly the thing," a visible shift in posture. Record what the user actually said, not just the topic, because the sentence is reusable and the topic is not.

**What was shaky.** Blunt, because nobody else reads this file. Shaky includes anything the user got through but would not want asked again the same way. For each one, record the question in the interviewer's wording and the specific failure mode, chosen from ran long, no number, wrong story, hedged, overclaimed, or trailed off without landing.

Add one more line people skip: anything the user said that they are not sure they can defend. That becomes an accuracy guard in Step 7, and if the loop continues, it is the thing most likely to be revisited.

Do not soften the shaky list. A debrief that reads well is a debrief that will not change what gets built next.

---

## Step 3: What was NOT asked, and what it signals

The absences are diagnostic and almost nobody records them.

Take every area the user prepared heavily and cross off the ones that came up. What remains goes in a table with three columns: the prepared area, what the absence probably means, and a confidence marker.

There are only three real interpretations. Force a choice between them rather than hedging:

1. **Saved for a later round.** Common when the round was short or when the interviewer's function does not own that area.
2. **Not a priority.** The user weighted something the company does not.
3. **Already satisfied.** A referral, a portfolio, an earlier round, or the resume already answered it.

Mark each guess with low, medium, or high confidence, and say what would resolve it. Usually the recruiter can, in one email.

This table is the most direct input to the next round's build, because it changes both what to drill and what to stop drilling.

---

## Step 4: Mine the interviewer's answers to the user's questions

The highest value section in the debrief, and the one most likely to be lost, because it happens at the end of a round when the user has stopped concentrating.

When interviewers answer questions, they stop performing and start describing their actual working life. Capture:

- How they described the team, verbatim where possible.
- The hardest problem they named, and the words they used for the pain.
- Words or phrases they repeated, with a count and the context each was used in. Repetition is the cheapest available signal about what is on their mind.
- What they seemed tired of, whether a topic, a tool, a process, or a type of candidate.
- What they lit up about.
- Anything they said about the next round, meaning who, what format, what focus.
- Any name they dropped, and in what context.
- Anything that contradicted the Company and Role Brief, along with which line in the brief needs correcting.

NEVER paraphrase a repeated phrase into a synonym. If the interviewer said "plumbing" four times, the word is plumbing, and mirroring it in the next round is worth more than a better word would be.

If the user recorded the round, ask for the transcript now, because this section is dramatically better with one and the mining is mechanical rather than reconstructive.

---

## Step 5: Flag what could not be remembered, and offer the recall questionnaire

Ask the user directly what they cannot remember, and record the gaps honestly. Blank spots an hour after a round are normal.

NEVER invent filler to complete a section. NEVER reconstruct a question the user does not actually remember being asked, even if it obviously fits the pattern of the round. A plausible reconstruction is indistinguishable from a real memory a week later, and the next round gets built on it.

Then offer the recall questionnaire. Roughly a third of the round comes back once the user stops trying to remember it, and a short list of pointed questions recovers far more than remembering cold. Good recall questions are specific and anchored: what was the second question, what did they say right before the questions section, what tool did they name, who spoke least, what was on the screen when they shared.

Offer it as a choice with a copy and paste answer sheet. Options should include sending it tomorrow morning, sending it in two days, or skipping it.

Whatever comes back goes into the existing sections above, not into a second file. A debrief split across two files is a debrief nobody reads.

PAUSE HERE. Wait for the user to say whether they want the recall questionnaire and when.

---

## Step 6: Promote validated answers to locked

Any answer that worked well enough should stop being rehearsed and start being fixed wording.

For each candidate, record the question type it answers, the line as the user actually said it, and why it is being locked. Valid reasons are narrow: it got a visible reaction, it fit the time, it had a clean ending. "It felt good" is not a reason and should be pushed back on once.

Locked means no future thread rewrites it. Not a style preference: protection against a real failure mode, where a later session politely improves a line that was working and the user walks into the next round with an unrehearsed sentence they have never said out loud.

Write locked answers into the locked decisions table in `_STATE.md` as well as into the debrief, because `_STATE.md` is the file every fresh thread reads.

Present the proposed locks before writing them.

PAUSE HERE. Wait for the user to confirm which answers get locked.

---

## Step 7: Update the accuracy guards

Accuracy guards are facts the user must not get wrong again under pressure. Each exists because they almost got it wrong once, or did.

Each guard has three parts, and all three are required:

1. **The guard.** What not to say.
2. **The correct version.** The exact phrasing to use instead, written out so it can be read rather than composed in the moment.
3. **Where it came from.** What happened that produced this guard.

Two sources feed this step. The first is the shaky list from Step 2, specifically anything the user is not sure they can defend. The second is the contradictions from Step 4, where the interviewer said something that conflicts with the Company and Role Brief.

A guard without a written correct version is only half a guard, because knowing what not to say does not produce a sentence when the question lands.

Write the guards into `_STATE.md` and, if a handoff to a new round is happening, into `HANDOFF.md` as well. They carry forward across every round in the campaign, not just the next one.

PAUSE HERE. Wait for the user to confirm the guards.

---

## Step 8: Propose the next round's build as a DRAFT

Write the proposal. Do NOT build any of it.

Open the section with the warning, in full, exactly this strong:

> **DRAFT ONLY. DO NOT BUILD THIS YET.** This is a proposal written while the round was fresh. It is here so the thinking is not lost, not because it is approved. Nothing in this section gets built until the user explicitly says go.

The proposal covers the next round label and date or "unconfirmed", the interviewers or "unknown", what today suggests they will test and the evidence for it, whether a new dossier is needed and for whom, proposed cheat sheet changes as add, sharpen, or retire, stories to add, stories to retire and why, question areas to drill, and what the user does not yet know and needs before building.

NEVER start building the next simulator, the next dossier, or the next cheat sheet inside this skill, no matter how obvious the shape looks. The proposal is written before the panel is known, and it will almost certainly change once it is. Building it now produces work that gets thrown away and, worse, attachment to a build designed on a guess.

PAUSE HERE. Wait for the user to say go before any building starts, and if they say go, hand off to the interview-research skill or the interview-simulator skill rather than doing it here.

---

## Step 9: Write the debrief and the handoff

Write two files.

**`[Your round folder]/Round Debrief - [Round Label].md`**, built from `templates/Round Debrief.md`, containing everything from Steps 1 through 8.

**`[Your round folder]/HANDOFF.md`**, built from `templates/HANDOFF.md`. This is the seed of the next round's folder and it contains only what a fresh thread needs to come up to speed with one paste:

- The locked decisions, so nothing gets re-litigated.
- The accuracy guards, so nothing gets crossed.
- The already drilled list, so the next simulator does not repeat what is solved.
- The recurring fixes and their current status, including anything marked overcorrected.
- The read order for a fresh thread, meaning which files to open and in what sequence.
- The one line statement of where this campaign actually is.

Then update `_STATE.md`, meaning the WHERE THIS IS banner, the files table, the locked decisions table, the accuracy guards, and the last updated line.

Close by telling the user the three things from this round that most change what happens next. Not a summary of the debrief. Three things.

---

## Customization: Guard rules (optional)

Guard rules are short standing corrections this skill applies to every debrief, without being reminded. They exist because debrief errors repeat, mostly in how a user habitually distorts their own memory of a round.

Add yours to the block below. Two illustrative examples:

```
- The user consistently underrates rounds immediately afterward. Do not accept "it went badly"
  as a summary. Ask for the specific moments and let the moments decide.
- Never record a question as asked unless the user can give the wording. If they only remember
  the topic, log it as a topic with the wording missing.
```

Keep this block short. It is read on every run, and this skill already asks for a lot of recall under time pressure, so anything that lengthens the preamble costs capture quality. If it grows past roughly ten lines, promote older entries into `HANDOFF.md`, where they belong to the campaign rather than the skill.

---

## Reference files

- Debrief template: `templates/Round Debrief.md`
- Handoff template: `templates/HANDOFF.md`
- Anchor file: `[Your round folder]/_STATE.md`
- The brief this round may have corrected: `[Your round folder]/Company and Role Brief.md`
- Story Bank routing file: `[Your Story Bank folder]/INDEX.md`
- Questions the user asked them: `templates/Questions to Ask Them.md`
- Deep Dive on state and multi round campaigns: `deep dives/05 - State, Handoff, and Multi-Round Campaigns.md`
- Deep Dive on round types: `deep dives/08 - Round Types and What Each One Tests.md`
- The user's Career Brain Trust, if they have one: `[Your Career Brain Trust folder]`

---

## Locked preferences for this skill (default; override during install)

- Capture before interpretation. The question list comes before any analysis of it.
- Preserve the interviewer's real wording and the real order. Never tidy either.
- Never invent a question, a quote, or a detail the user does not actually remember.
- The next round's build is always a draft, and nothing gets built until the user says go.
- Ask clarifying questions in multi choice form with a copy and paste answer sheet.
- No em dashes and no en dashes in any output.
- Define acronyms in full on first use, then use the short form.
- When something is unreachable or uncertain, say so and ask. Do not fill the gap from memory.
