>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# The Story Bank

This deep dive expands Step 6 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which gave you the seven line version: build five to nine cards, use the ten element checklist, make the assistant interrogate you, harden the numbers, map coverage, write a failure card. This is the longer version: why this is the only fully reusable layer, how it sits on a Career Brain Trust without duplicating it, what each of the ten elements tests and why element five carries most of the weight, the interrogation method in detail, metric hardening and date stamping, the coverage map and what a gap really means, ranking and demotion, the required shape of the failure card, the honest boundary line, drilling endings separately, variant framings, and the `NEEDS REAL DETAIL` marker as a machine readable question queue.

Read the main guide first, at least Steps 1 and 6, and read Deep Dive 1 if you have not. The coverage map here is built against the competency model the intelligence layer produces, and building stories before you know what the round is scoring produces a beautiful set of cards aimed at the wrong rubric.

---

# The Only Layer That Is Fully Reusable

Everything else in this kit expires. The Company Brief is about one company. The Interviewer Dossier is about one person in one round. The simulator persona is built for a specific chair on a specific panel, and the cheat sheet is version controlled against this week's mocks. None of it survives the offer.

The Story Bank survives all of it. The seven stories you can tell cold, with real numbers, under follow up, are the same seven at the next company and the one after. This is why the main guide says to build it with no interview booked. It is the slowest layer, the only one that compounds, and the one that actually gets scored. Everything else here is scaffolding around it.

There is a second, less obvious return. Working out what you decided on a project three years ago, what the alternatives were, and what you gave up is real reflective work, the only part of preparation that improves your judgment rather than your recall. People finish it and stop being able to give a vague answer, because they now know the specific one.

---

# How It Sits on a Career Brain Trust

If you have a Career Brain Trust, the Story Bank sits on top of it and does not replace it. Confusing the two is the most common way people end up with a Story Bank they cannot use.

**The Career Brain Trust holds canonical written material.** Verified bullets per role, the numbers, the phrasings that have survived editing, organized so a resume or cover letter can draw from them. It is written to be read. Its unit of organization is the employer, because that is how a resume is organized.

**The Story Bank holds spoken narratives.** The same work, re-cut into two minute stories with a headline, a decision you owned, a defensible number, and a closing line. It is written to be said out loud. Its unit of organization is the competency, because that is how an interview is scored. The same project can appear on two cards under two competencies, which would be duplication in a Brain Trust and is correct here.

The bridge is the `Source` field on every card, pointing back at the Brain Trust file the material came from. It does one job: trace any spoken claim back to a verified written bullet. When a mock asks a follow up you cannot answer, open the source file rather than inventing.

If you do not have a Career Brain Trust, leave the field blank and build from your resume. It works, just slower, because a resume gives you outcomes without the decisions underneath and you spend longer in the interrogation step.

---

# The Ten Elements, and Why Element Five Carries the Weight

Every card is built against the same ten element checklist: headline, situation and stakes, the ambiguity, your assessment, the decisions you personally made, what you built and who did what, how you communicated across functions, the result with real numbers, the reflection, and the competency tags.

Three are worth a note. **The ambiguity** is a filter as much as an element: if nothing was unknown or contested, this is a task rather than a story, and it will not score. **Who did what** exists because vagueness about your part versus your team's reads as credit taking, and any competent interviewer probes it. **The reflection** has to be real, because an interviewer who has run two hundred loops spots a humblebrag dressed as a flaw from the first clause.

Element five, the decisions you personally made, carries the weight and is the one most people leave out. The result tells the interviewer what happened. It does not tell them whether you caused it, and at senior levels causation is the question. Plenty of people were standing near a good outcome.

A decision has three parts, all of them present. What you chose. What you did not choose, named specifically. And what it cost, because a decision with no cost was a preference. "We decided to prioritize the merchant onboarding flow" is not a decision. "I chose to fix onboarding before disputes, knowing that pushed the disputes work a quarter later and left that team holding a manual process through peak season, because onboarding was where we were losing volume we could never get back" is a decision. The second is longer because it contains the trade off, and the trade off is what gets scored.

Fill in the block for every card, even where the decision feels small. If you cannot name a decision you owned on a project, that project belongs in somebody else's Story Bank.

---

# The Interrogation Method

## Hand over the raw story first

Do not start by asking the assistant to write a card. Start by telling it the story the way it comes out of your mouth: unstructured, out of order, with the parts you remember best in front. Speak it if you can. Two or three rambling paragraphs is the correct input.

The assistant's first move is not a question and not a draft. It is to reflect the story back in two or three lines and name which of the ten elements are thin. Something like: "So you inherited a fraud rule set that was blocking good customers, you rebuilt the review queue, and false positives came down. Situation and result are clear. The ambiguity is missing, I do not know what was contested. And element five is empty, you have told me what the team built but not what you decided."

That reflection does three things. It confirms the assistant understood the story before asking about it. It shows you holes you cannot see from inside your own memory. And it makes the interrogation targeted rather than a form.

## Then probe in clusters of two to four, and wait

After the reflection, the assistant asks two to four focused questions, then stops and waits for your answers. Not eight. Not a numbered list covering every thin element at once.

The reason is practical. A wall of twelve questions gets one sentence each, because you are pattern matching down a form. Three get answered properly, and the third answer usually changes what the next three should be. The interrogation is adaptive or it is a survey.

Put the rule in the prompt, because assistants default to the wall: "Ask me at most four questions at a time, then stop and wait before asking more. Do not write any part of the card until I say the story is complete."

Expect three or four rounds per card, and expect the useful material in round three. The first round gets the facts you already had. The round where Engineer Alex says "actually, the real reason was that the vendor contract renewed in March" is the round that produces the card.

## Never accept a story it wrote from your resume

The assistant can produce a fluent, well structured, competency tagged story card from your resume in about eight seconds. It will look excellent. Do not use it.

The problem is not that it is fabricated, although parts of it usually are. The problem is that you cannot defend it. The follow up goes one level below whatever you said, and a story you did not build has no level below. Interviewers are good at spotting the moment a candidate runs out of their own material, because the tell is the same every time: the answer gets more general exactly where it should get more specific.

The test is simple. For every sentence on the card, you should be able to say where it came from. If you cannot, it goes back into the interrogation or comes out.

---

# Hardening the Numbers

Every metric on a card gets checked once, and where it was generous, corrected downward to what you can survive being pushed on. This feels like sabotage and it is the opposite.

Run each number through three questions. Where it came from, down to the dashboard, report, or person. What the denominator is, because "reduced false positives by forty percent" means nothing until you say forty percent of what, over what window. And what the honest attribution is, because if three things changed that quarter, "we cut it by forty percent and my change was the largest single contributor, though a pricing change landed the same month" is the version that survives.

A defensible smaller number beats an impressive one that collapses. The collapse is the problem, not the size. An interviewer who pushes on forty percent and gets a clean, bounded, slightly smaller answer learns you are careful with evidence. One who watches the number dissolve will test every other number you give for the rest of the round.

Date stamp the verification. The card template has a `Numbers last verified` field and a `Verified` column, because memory of a number decays into a rounder, better version of itself. A number you checked four months ago is a different asset from one you remember confidently, and when you reuse the card at the next company the date tells you whether to re-check.

---

# The Coverage Map and the Ranking

The coverage map is a two column table: every competency the round will test, and the card that owns it. The left column comes from the intelligence layer, specifically the competency model in Prompt 03 and whatever the recruiter told you was being assessed. The right column comes from your cards. Then you look for empty rows.

**A competency with no card is a gap to fix, not a card to stretch.** The tempting move is to take your strongest story and argue it also demonstrates, say, conflict resolution. Occasionally true. Usually stretching, and stretching has a specific failure mode: the story enters the answer aimed at the wrong target, the interviewer asks the follow up that framing invites, and you defend a claim the story was never built to support. Better to build a new, weaker, honest card, or say plainly that your strongest example here is smaller than they might expect.

Each card should own two or three competencies. One is under-using a story you spent an hour building. Five means the tags are aspirational rather than descriptive, and your simulator will reach for that card for everything.

Then rank the cards. One through three are your strongest and do most of the work in any round. Everything below three is reinforcement, a deliberate reframe: the lower cards give you a second angle on a competency, they do not fill gaps. If a card exists only because the set looked thin, cut it. Six cards you can tell cold beats nine where four are half remembered, because in the room you reach for whatever the trigger phrase surfaced, and the half remembered ones are live ammunition.

---

# The Failure Card and the Honest Boundary

You will be asked about a failure. Everyone is asked. Write one card for it, deliberately, and give it the required shape.

**What you assumed.** Not what went wrong, what you believed that turned out to be false. A failure with no false assumption underneath is bad luck, and bad luck does not demonstrate learning.

**What happened.** Briefly, without softening. The scale of the consequence matters, because a failure with no consequence is not one and the interviewer will notice you picked a safe example.

**What you own.** Specifically yours, separated from what the environment or other people contributed. You can name the context. You cannot lead with it.

**What you changed.** A concrete change in how you work, ideally with a later example where the change held.

**End on the lesson, never on the grievance.** This is the rule people break, usually in the last fifteen seconds and without noticing. The story goes well, then the closing sentence drifts into what the organization should have done differently, and the card converts from evidence of learning into evidence you are still arguing about it. Write the last sentence down and use it.

The related move is the **honest boundary line**, which belongs on every card, not just the failure one. It is what you say when a follow up goes past what you did or know. Something like: "I owned the design and the trade offs. The implementation of the scoring service was owned by the platform team, so I can tell you why we chose it and what we measured, but I would be guessing about the internals."

Naming the edge of your knowledge cleanly reads as senior, and the reason is worth understanding rather than accepting. Senior people work in systems too large to know entirely, so knowing where your knowledge stops is evidence you have operated at that scale. Bluffing past the boundary is detectable inside one follow up, because the second question in any technical thread goes exactly where the first one pointed.

---

# Endings, Variants, and the Question Queue

**Write the ending of every story down.** Late in my own runs I discovered three of my five stories had no ending, which is why they kept sprawling. I could start any story well. I could not stop. The card template has a block called "the line that ends it" holding one sentence: say this and stop talking.

Then drill the endings separately, a distinct exercise that takes six minutes. Do not tell the whole story. Say the last two sentences of each card, out loud, in order, five times through. Landings respond to isolated practice in a way whole story repetitions do not, because when you run the whole story you spend your attention on the middle and arrive at the ending tired.

**Append variant framings, never rewrite the canonical version.** The same story gets re-cut for different questions. The onboarding rebuild is a prioritization story, an influence story, or a data story depending on what was asked. Each re-cut goes into the Variant Framings block at the bottom of the card with a note on when to use it, and the canonical two minute version stays put. Rewriting the canonical version to suit this week's round destroys the reusability that makes the bank worth building, and after three companies you have a card edited toward four rubrics that serves none of them.

**Use `NEEDS REAL DETAIL` as a question queue.** Anything you cannot verify stays marked `NEEDS REAL DETAIL` with a specific question beside it. Not a blank. Not a plausible placeholder. A question, in full, that you could email to a former colleague.

This is machine readable on purpose. Ask the assistant to scan the folder and return every marker as one list, and a scattered set of half finished cards becomes a work queue you can clear in an evening. It also creates a safety property: a placeholder phrased as a question cannot be promoted into a claim by a later thread trying to be helpful. A blank invites the assistant to fill it. A question does not.

---

# When the Bank Is Big Enough

Five to nine cards. Below five you have coverage gaps you cannot cover honestly. Above nine you have a retrieval problem, because in the room you are not selecting from a library, you are grabbing whatever the trigger phrase surfaced, and a large bank surfaces the wrong card more often.

The restraint worth naming: **a ninth card is almost always worse than a better third card.** Building a new card feels productive because it produces a new file, and re-drilling card three produces nothing you can look at. But the ninth card gets used in perhaps one interview in six, and card three in nearly every one. Given an hour, the hour goes to card three, into the parts that break under pressure: the ending, the follow ups, the number you have not checked in a while.

Three signals the bank is done. You can tell cards one through three cold, without notes, including the closing sentence. Every competency on the coverage map has an owner, or an acknowledged gap you have decided to live with. And every number on the top three cards has a source and a date.

Two signals you are polishing rather than building. If you are rewording the two minute version for the fourth time, stop, because what you say out loud diverges from the written version anyway and the written one is a memory aid rather than a script. If you are adding a fourth variant framing to a card nobody has asked about, you are optimizing for an interview that has not happened.

And one thing not to do at all: do not build cards for hypothetical questions. The bank is organized by what you can prove, not by what you might be asked. Construct a story to answer a specific anticipated question and you have started writing fiction with a deadline, and it will be the answer that collapses, because it is the only one with nothing underneath it.

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

Based on "The Story Bank," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
