---
name: interview-research
description: Use this skill whenever the user wants to build the intelligence layer for a specific interview round, meaning the verified research about the company, the role, the round format, and the named humans who will be in the room. Trigger phrases include "research this company for my interview", "who is interviewing me", "build me an interviewer dossier", "run the deep research prompts", "reconcile my two research passes", "what should I not say in this interview", "write the company and role brief", "I have an interview at Northwind Payments and I need the research", and "cross validate what I found about my interviewer". Always trigger when the user is gathering, verifying, or reconciling outside information about an employer, a hiring panel, or a round format ahead of an interview, even if the exact wording differs. Do NOT use this skill for building or running the mock interview itself, which is the interview-simulator skill, for producing the glanceable HyperText Markup Language cheat sheet, which is the cheat-sheet-builder skill, or for capturing what happened after a real round has already been sat, which is the round-debrief skill.
---

# Interview Research skill

This skill turns a job posting, a recruiter email, and a list of names into a verified intelligence layer for one specific interview round, producing a Company and Role Brief, one Interviewer Dossier per human in the room, and an explicit written list of claims the user is not allowed to assert out loud.

The workflow has 8 steps. Run them in order. Steps 1, 2, 3, 4, 5 and 7 pause for the user. Steps 6 and 8 are write steps that only run once the user has approved what goes into them.

---

## Step 1: Confirm the round and inventory what is already known

Before any research happens, establish what round this is. "I have an interview at Northwind Payments" cannot be researched usefully. A thirty minute first call with a hiring manager and a forty five minute executive panel with three people are different events that reward different intelligence.

Ask the user for the following, and accept "I am guessing" as a valid answer for any of them:

1. Company name and the exact role title as posted.
2. Who is in the room, full names and functions, and how confident the user is in each name.
3. Format, length, and medium.
4. What the recruiter called the round, verbatim.
5. What the recruiter said it assesses, verbatim if they said anything.
6. Where it sits in the loop.
7. Whether the user has already run any research, and in which tool.

Then read `[Your round folder]/_STATE.md` if it exists. If it does not exist, say so and offer to create it from the template rather than proceeding without an anchor file.

Produce a short table back to the user showing every field, what you have, and whether it is confirmed by a human or inferred. Mark every guess explicitly. The guesses become recruiter intake questions, not research questions, because a research tool cannot tell you who is on a panel and a recruiter can.

Ask the confirmation question in multi choice form with a copy and paste answer sheet.

PAUSE HERE. Wait for the user to confirm the round definition and correct any names.

---

## Step 2: Select which Prompt Library prompts to run, and hand them over

This skill does NOT perform the deep research itself. It builds the prompts and consumes the output. Say this to the user plainly the first time, because the most common failure is a user assuming the assistant already went and looked.

There are five prompts in the Prompt Library:

| Prompt | What it produces | When to run it |
|---|---|---|
| 01 Company and Role Deep Research | The problem space, the business model, the product surface, recent public changes | Always |
| 02 Interviewer Deep Research | One named person, career history, visible worldview, what they are likely to test | Once per named human |
| 03 Round Format and Competency Model | What this company's version of this round type actually tests | When the round type is known and the company is large enough to have a public pattern |
| 04 Cross Validation and Reconciliation | The second pass, run in a different tool | Always, unless the user has explicitly declined a second tool |
| 05 Recruiter Intake | The five questions to email the recruiter | When any Step 1 field is a guess |

Select the set, then fill each selected prompt with the user's specifics. Two fills matter more than the rest:

**State the hypothesis.** Inside the interviewer prompt, write what the user believes about the person and ask the research tool to confirm or refute it. A tool asked to verify a stated belief is more useful than one asked to summarize, because it tells you when you are wrong.

**Warn about name collisions explicitly.** If the interviewer shares a name with a public figure, or with anyone else in the same industry, describe the other person inside the prompt and instruct the tool to keep them separate and to say which one each source refers to.

Output the filled prompts in individual fenced code blocks so the user can copy each one cleanly. Tell the user which tool to run each in, and tell them to run the same set twice in two different tools.

PAUSE HERE. Wait for the user to run the prompts and paste back the output of pass one.

---

## Step 3: Ingest pass one

Read the pasted output. Do not summarize it back. Instead, decompose it into atomic claims, where a claim is one assertable sentence with one subject.

For every claim, record four things:

- The claim, in one line.
- Whether the source output marked it VERIFIED with a link, or INFERRED with reasoning, or left it ambiguous.
- The source, if one was given.
- Which artifact it belongs in, meaning the Company and Role Brief or a specific person's dossier.

ALWAYS separate VERIFIED from INFERRED. If the research output blended them, split them yourself and mark the ones you had to split as low confidence, because a blended output is evidence the tool was not disciplined.

Report negative findings rather than dropping them. If the prompt asked for the interviewer's published writing and found none, the correct record is "searched, not found" and not silence. A silent gap reads later as an unasked question. A recorded negative finding is intelligence, because it tells you what the person has no public position on.

NEVER merge two people who share a name. If any part of pass one looks like two careers stapled together, an implausible timeline, two cities at once, a seniority jump that does not fit the dates, flag it as a suspected collision and hold the whole person aside until pass two arbitrates.

PAUSE HERE. Wait for the user to paste the output of pass two.

---

## Step 4: Ingest pass two from a different tool

Run the same decomposition on pass two. You are not looking for a better answer. You are looking for disagreement.

Two rules make this step worth doing:

1. **Do not read pass one while decomposing pass two.** Decompose pass two on its own terms first, then compare. Comparing while reading anchors you on pass one and records agreement that is not there.
2. **A second pass from the same tool is not a second pass.** If the user ran both in the same product, say so and mark the reconciliation as single source, which changes how much of it can be promoted to fact.

If the user declined the second pass entirely, that is allowed. Say once, without lecturing, that everything from a single pass will be treated as unverified in Step 5, and continue.

PAUSE HERE. Wait for the user to confirm both passes are in before you reconcile.

---

## Step 5: Reconcile into AGREED, CONTRADICTED, UNVERIFIED

The step that converts raw research into something the user can safely open their mouth about, and the step people skip.

Sort every claim into exactly one bucket:

**AGREED.** Both passes found it and at least one cited a primary source. A primary source means the company said it, the person said it, or a filing said it. Two secondary write ups of the same press release are one source, not two.

**CONTRADICTED.** The passes disagree, on the fact, on the date, on the scale, or on who did it. Every contradiction gets assigned to a human who can settle it. The recruiter can confirm panel composition and round format. The interviewer can confirm their own history, gracefully, if asked lightly rather than asserted at.

**UNVERIFIED.** One pass asserted it and nothing backs it up, or it came from a single pass because the user declined the second, or it was inferred rather than found.

Present the three buckets as three tables. Do not bury a contradiction in prose.

Then ask the user, in multi choice form with a copy and paste answer sheet, what to do with each contradiction, offering at minimum promote, assign to the recruiter, assign to the interviewer as a light question, or drop.

PAUSE HERE. Wait for the user to resolve the contradictions.

---

## Step 6: Write the Company and Role Brief and one Interviewer Dossier per human

Now write the artifacts, using only what survived Step 5.

**`[Your round folder]/Company and Role Brief.md`** carries the problem space. What the company sells and to whom, how it makes money, what changed recently and what that implies about hiring priorities, what the product feels like to use, what the role is being hired to fix, and the ten questions the user could ask that only someone who did this work could ask.

**`[Your round folder]/Interviewer Dossier - [Name].md`**, one file per human, converts a person into a posture. Career arc, what they are likely to be measured on, their visible worldview and where it came from, the quiet question in their head when they meet a candidate at this level, what wins them, what loses them, and the two or three probes they are most likely to run.

Three hard rules govern both files:

- NEVER fabricate a quote. If you cannot produce the sentence the person actually wrote or said, write what they appear to believe and mark it INFERRED. A paraphrase presented as a quote is the fastest way to embarrass the user in the room.
- NEVER fabricate a job title, an employer, a date, or a tenure. An approximate date is written as approximate.
- Every line in either file carries a confidence marker. VERIFIED with a source, INFERRED with the reasoning shown, or UNVERIFIED. A file where you cannot tell which is which is worse than no file.

Use the templates at `templates/Company and Role Brief.md` and `templates/Interviewer Dossier.md` so the structure matches the rest of the kit.

---

## Step 7: Write the Do not assert list with safe substitute phrasings

Take every UNVERIFIED claim and every unresolved CONTRADICTED claim and write it into a section called **Do not assert**, in both the Company and Role Brief and in `_STATE.md`.

Each entry has two parts, and the second is what makes this step valuable. A list of forbidden sentences is a list of things to nervously avoid. The same list with the safe replacement written out is a list of good questions.

Worked example:

> **Do not assert.** "Your team owns the fraud platform end to end."
> **Say instead.** "I could not tell from the outside how the ownership splits between your team and the platform group. How does that actually work?"

The reframe converts a landmine into a question that signals the user did the reading without claiming a fact they cannot defend.

Also write, verbatim, into the same section, explicit written permission to say "I do not know, and I do not think that is public." It reads as senior. Bluffing reads as junior and is detectable inside one follow up.

Present the Do not assert list to the user before writing it, because they may know that one of the flagged claims is actually true from a source you never saw.

PAUSE HERE. Wait for the user to approve the Do not assert list.

---

## Step 8: Update the anchor file

Update `[Your round folder]/_STATE.md`:

1. Rewrite the WHERE THIS IS banner in one line saying that research is complete, what it produced, and what a fresh thread must not redo.
2. Fill in the round table with the confirmed fields, marking each as recruiter confirmed or inferred.
3. Copy the short version of the Do not assert list into its section.
4. Add any accuracy guards that fell out of the research, meaning facts that are easy to cross under pressure.
5. Add the new files to the Files in this folder table.
6. Update the Last updated line.

Then tell the user, in three lines or fewer, what exists now and what the natural next step is, which is usually building the Story Bank and then the simulator.

---

## Customization: Guard rules (optional)

Guard rules are short standing corrections that stop the same error from recurring across every run of this skill. They exist because research errors repeat in personal patterns. One user keeps getting a name collision on the same common surname. Another keeps having a former employer's numbers attributed to their current one.

Add yours to the block below. Two illustrative examples:

```
- There are two people named Priya Raghunathan in payments. Ours is the staff engineer at
  Northwind Payments, not the one who writes the fraud newsletter. Never merge them.
- Northwind Payments and Northwind Logistics are unrelated companies with a shared founder name.
  Never attribute one company's funding history to the other.
```

Keep this block short. It is read on every run, so a long block costs attention on every use and crowds out the steps above it. If it grows past roughly ten lines, promote older entries into the accuracy guards section of `_STATE.md`, where they belong to the round rather than the skill.

---

## Reference files

- Prompt Library, all five prompts: `Prompt Library/`
- Company and Role Brief template: `templates/Company and Role Brief.md`
- Interviewer Dossier template: `templates/Interviewer Dossier.md`
- Anchor file template: `templates/_STATE.md`
- Deep Dive on this layer: `deep dives/01 - The Intelligence Layer.md`
- Deep Dive on turning a person into a posture: `deep dives/03 - The Interviewer Dossier.md`
- The user's round folder: `[Your round folder]`
- The user's Career Brain Trust, if they have one: `[Your Career Brain Trust folder]`

---

## Locked preferences for this skill (default; override during install)

- Ask clarifying questions in multi choice form with a copy and paste answer sheet at the bottom.
- Never produce a draft artifact before the user has confirmed the material going into it.
- No em dashes and no en dashes in any output.
- Define acronyms in full on first use, then use the short form.
- Never assert a claim in an artifact without a confidence marker attached to it.
- Report negative findings as "searched, not found" rather than omitting them.
- When a fact is unreachable or a tool returns nothing, say so and ask. Do not fill the gap from memory.
