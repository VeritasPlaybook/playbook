>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# The Interviewer Dossier

This deep dive expands Step 4 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), specifically the person half. The main guide told you to research the named humans and warned about name collisions, in a few lines. This is the longer version: why the dossier's job is converting a person into a posture rather than writing a biography, the four field persona and why four fields beats a personality essay, why the headline correction goes first, structural separation of fact and inference instead of hedging adverbs, namesakes as an explicit do not merge list, grounding inference in training lineage, the quiet question in their head and how to disarm it, open flags and light touch phrasing, mirroring their vocabulary, converting all of it into numbered directives, how a panel of three differs, and what to do when the person leaves no trace.

Read Deep Dive 1 first. This file is about what you do with interviewer research once you have it, and it assumes you already run the verified and inferred split, the two pass cross validation, and the do not assert list. A dossier built on a single unreconciled research pass is a confident description of a person who may not exist.

---

# A Person Converted Into a Posture

The most common way this file goes wrong is that it becomes a biography. Three pages on where someone studied, their career arc, the companies in order, the talks. It reads well, it took two hours, and it changes nothing about how you behave in the room.

The dossier has one job: convert a person into a posture. A posture is the set of behavioural adjustments you make because of who is sitting across from you. You lead with the number instead of the narrative. You name the trade off before the outcome. You stop after ninety seconds instead of two minutes. Every fact in the dossier either produces one of those or does not belong.

The test for every line is blunt: what do I do differently because of this. If the answer is nothing, delete it. Where they went to school produces no posture. Six years in a consulting environment before moving into product produces a specific one: they will notice structure, and notice when you have none.

This is also why the dossier is one file per human, never one for a panel. Two people merged into one document produce an averaged posture, the one posture guaranteed to be wrong for both.

---

# The Four Field Persona

The persona that goes into the simulator has four fields and no more. Who they are. What they test. What wins them. What loses them.

Four is not a compromise for brevity. It is what a model can hold as a distinct voice across a forty minute mock. A long personality essay produces a blander interviewer, because the essay contains a dozen mildly contradictory traits and the model averages them into a generically pleasant professional. Specificity comes from few fields with hard content, not many with soft content.

**Who they are** is one or two sentences of confirmed background, with the part that matters for this round in front.

**What they test** is the two or three things this specific person is likely probing. Not the round's rubric, which lives elsewhere. Their personal lens.

**What wins them** must be behaviours, not virtues. "Be clear" is unfalsifiable and the model cannot act on it. "Names the failure mode before naming the fix" is usable, because the simulator can notice when you did not. Write every line so an observer could tick a box.

**What loses them** is the sharpest of the four and the one people write laziest. Not a generic list of interview mistakes. The specific thing that would make this person disengage. Someone who came up through operations disengages at hand waving about implementation. Someone from a research background disengages at a confident causal claim with no measurement behind it. Those are different failures, and you cannot prepare for both by resolving to do well.

---

# Headline Correction, Stated First

The first block in the dossier template is the headline correction, above the confirmed background deliberately: mis-levelling the interviewer is the most common failure in this step, and stating the correction first stops the file quietly reverting to your original assumption.

The block has three lines. What you or a model would assume. What the evidence shows. And the consequence for the round: the thing you would have said that would have landed wrong.

Mis-levelling dominates because titles carry no consistent meaning across companies and your assumption fills the gap automatically. A "Director" at one company runs a function of eighty people and thinks about budget and organizational design. At another it is a senior individual contributor title and the person wants to talk about the system. Prepare an executive framing for the second person and you spend forty minutes being too abstract for someone who wanted details, and they conclude you do not have them.

The consequence line is what makes the block work. "Actually a hands on technical lead, not a people manager" is a fact. "I would have opened with the organizational restructure story, which is the wrong story for someone who wants to hear how the decision was made and what the system did" is a posture. Only the second changes anything.

If you had no prior assumption to overwrite, do not skip the block. Write "none, no prior assumption," then what you expected and what you found. The exercise is the point: it forces you to notice the moment your model of the person changed, which is the moment you are otherwise most likely to forget.

---

# Structure Instead of Hedging, and Where Inference Comes From

The failure mode this chapter prevents is the hedging adverb. "They probably lead the risk platform team." "They seem to care about measurement." Each of those is a fact and a guess wearing the same coat, and three days later your eye slides over the adverb and reads the noun.

The repair is structural, not linguistic. Confirmed facts go in a table with a source link in the adjacent column. Inferences go in a separate section labelled INFERRED that keeps the label and states its reasoning line by line. A claim's status becomes a property of where it lives rather than of one adverb inside it, and you cannot promote a claim by skim reading, because that would mean moving it.

Keep the label even when it feels redundant. This file gets read at eleven at night before the round, and at that hour the section header is the only thing doing work.

## Namesakes and the do not merge list

The dossier has a section called wrong person exclusions, listing the humans you found who are not your interviewer. Same name, different city, different field, whatever distinguishes them, with a source.

Recording the people you ruled out feels like documenting a dead end. It is not, for one reason: you will open a fresh thread later, run a second pass, or hand the folder to a friend, and without the exclusion list the ruled out person walks straight back in. Every merged biography I have seen was merged twice, once by the tool and again a week later by a different tool nobody had told.

Write the distinguishing detail, not just the name. "Do not merge: same name, academic researcher in a different country, no payments background. Distinguishing detail: different middle initial on published work." That is a rule a future thread can apply. "There is another person with this name" is not.

## Training lineage, not invented personality

The legitimate source of inference is where someone was trained, not what kind of person they seem like. Research tools generate personality claims freely, and those are the least verifiable and most confidently stated content in any interviewer research output. Delete them.

What you can reason from is the environment somebody spent formative years inside, because organizations impose recognizable habits. Years in consulting usually means rewarding visible structure and noticing when an answer has none. Coming up in a heavily regulated function usually means probing what happens when the process fails. A research background usually means wanting to know how you measured a claim before caring about its size.

State the lineage and the inference together, in that order, so the chain is auditable: "spent six years in a consulting environment (VERIFIED, source linked), therefore likely rewards a stated structure at the top of an answer (INFERRED)." That is a hypothesis with its evidence attached, testable in the first five minutes. "Seems like a structured thinker" is a horoscope.

---

# The Quiet Question in Their Head

Every interviewer carries one unspoken doubt they are checking for, and they rarely ask it directly. It comes from the gap between your visible profile and what the role needs, and it is usually one sentence long.

Coming from a smaller company into a larger one, the quiet question is "has this person ever operated at our scale." For a technical round with a product candidate, it is often "can they hold a real conversation about the system, or do they manage from a distance."

Write it in their voice, as a quoted sentence, in the dossier. Then write how you will disarm it without naming it.

The disarming has to be indirect, and this is the part worth getting right. Naming their doubt out loud takes a mild concern and makes it the explicit subject of the conversation, and now you are arguing your way out of a frame you built yourself. Saying "I know my last company was smaller, but" hands them the objection fully formed.

Instead you demonstrate past the doubt inside an answer they asked for. If the doubt is about scale, the second sentence of your first story states the scale flatly and moves on. If the doubt is about technical depth, the story you lead with contains one implementation trade off described accurately, and then you carry on. The doubt dissolves because it was answered before it formed, and it never becomes a topic. Answer it early, answer it once, never label it.

---

# Open Flags, Light Touch, and Their Vocabulary

Everything you suspect but cannot confirm goes into a table of open flags, and every row gets the light touch question that lets them correct you rather than the assertion that makes you wrong out loud.

Suppose PM Jordan believes a Northwind Payments interviewer still owns the settlement service, but the only evidence is a two year old conference bio. The assertion, "since you own settlement," is a coin flip with an expensive tail. The light touch version, "I may have this out of date, is settlement still on your side of the line, or has that moved?" costs nothing if wrong, sounds like someone who reads carefully and knows the limits of outside information, and frequently produces a better answer than the fact you meant to state.

Phrase every one so being wrong is free. The pattern is a hedge about your own information, never about their reality: "I could not tell from the outside," "the public material was a couple of years old," "I did not want to over read this." Those put the uncertainty where it belongs: in your sources.

**Capture their vocabulary and mirror it.** As you read anything they wrote or said, list the exact words they use for what they work on: merchants or sellers, disputes or chargebacks, controls or guardrails. Note which concepts they treat as obviously important and which as solved, because that ratio tells you where their attention sits.

Then use their words in the room, without ceremony. This is not flattery and should never be visible as a technique. It is a compression device: the organization's own term for its core object skips the translation step in their head. The wrong word for the thing they think about all day is a small, continuous signal that you are outside it.

One caution. Mirror vocabulary, not slogans. Repeating a company's marketing line back at the people who have to live with it is the fastest way to sound like you read the careers page and nothing else.

---

# Turning the Dossier Into Directives

The last section is three to five numbered directives, each in the same form: observation about them, therefore I do X. An observation with no action is a note and belongs further up the file.

Examples of the shape, for a fictional round at Northwind Payments:

1. They came up through operations and will probe implementation, therefore I open the platform story with what got built and who built it, keeping the strategy framing for later.
2. They have written publicly about measurement quality, therefore every number I quote comes with its denominator and its window, unprompted.
3. Their team owns a surface adjacent to mine and the boundary is unclear, therefore I ask the ownership question in the first ten minutes rather than assume a structure and get corrected in the last ten.
4. They interrupt, based on two recorded talks, therefore I front load the conclusion of every answer and treat the interruption as normal rather than a sign I am failing.

Five is the ceiling. This is the section you actually reread before the call, and a list of eleven behavioural intentions produces zero behavioural changes, in the same way a list of six coaching fixes produces zero fixes.

The directives are also the hand off into the rest of the system. Directive one becomes a persona line in the simulator. Directive two becomes a scoring dimension you ask the bot to weight. Directive three becomes a row in the questions you ask them. Directive four becomes a run mode where the interviewer interrupts (more on that in Deep Dive 4). If a directive cannot be turned into something in another file, it was a note after all.

---

# Panels, and People Who Leave No Trace

## A panel of three is three lenses, not one interview

When three people are in the room they are almost never asking about the same thing, so map each person to one dimension of the rubric. The skip level executive usually tests judgment and whether you can operate at the altitude of the role. The peer tests whether working with you would be pleasant and whether you take credit for other people's work. The functional expert tests depth, and is the only one who will follow a technical thread to the bottom.

Two consequences. First, thread ownership: answer the expert's question at the executive's altitude and you have given a good answer to the wrong person, and the expert will not ask again. Notice who asked. Second, randomize the opener in a panel simulator, because the difference between a panel and a sequence of one on one conversations is not knowing which lens comes first, and rehearsing a fixed order trains a reflex that will not fire.

Build one dossier per person, then a single short panel page on top saying only who owns which dimension and who is likely to speak first. That page is what you glance at, not the three dossiers.

## When the person is genuinely un-researchable

Sometimes there is nothing. No public writing, no talks, a profile with a title and two dates. This is common for people in risk, compliance, and security functions, and it is an occupational norm rather than evasion.

Do not fill the gap with inference. A dossier built from a title alone describes a job category, and playing that category as a persona trains you against a stereotype.

Do three things instead. Write "searched, not found" with the platforms you searched, so nobody redoes it. Shift the weight of your preparation to the competency model, which does not require a name. And build the persona from the function rather than the person, labelled honestly as a functional persona, with the simulator instructed to stay generic rather than invent history.

Then take the useful thing the absence tells you: this person does not expect you to have read anything of theirs, so referencing a half matched item you found is a larger risk than saying nothing.

---

# The Ethics and the Limits

You are researching a professional footprint. What someone has published, presented, patented, shipped, or written under their own name in a professional capacity. That is the boundary and it is not a soft one.

Their personal social accounts, their family, their neighbourhood, their photographs, their political activity, old accounts under a name they no longer use: none of it is in scope or useful. The line is easy to find in practice. If they published it in a professional context, it is fair. If you found it by looking into their life rather than their work, close the tab.

There is a self interested version of the argument too, the one that holds when nobody is watching. An interviewer who can tell you have over-researched them is a bad outcome, even when everything you found was public. The feeling on the other side is being handled: this person has studied me and is performing a version of themselves calibrated to what they think I want. That reads as a candidate managing an impression, the opposite of what the dossier is for, and worse than no research at all.

Practical restraints follow. Reference at most one specific piece of their public work, once, and only where it is relevant. Do not open with it. Do not stack references to demonstrate thoroughness. Never quote something back verbatim. Do not mention anything you could only have found by digging, even when it is public, because the tell is not whether it was findable, it is how far you went.

And keep the dossier's limits in view. It is a set of hypotheses about a stranger, and the person who walks into the call has had a day you know nothing about. The posture is a starting position, not a script, and if the first five minutes tell you the read was wrong, drop it. Its real value was never the accuracy of its predictions. It was that building it forced you to think about the round from the other side of the table, and that habit works even on the interviewer you could find nothing about.

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

Based on "The Interviewer Dossier," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
