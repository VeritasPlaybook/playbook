>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Recruiter Screen: Question Bank

# What this round is really testing

The recruiter screen is a filter, not an evaluation. It answers four questions: is this person roughly the right level, are they interested, do the logistics work, and will they be easy to move through a process. Nothing else is decided, and treating it as a chance to prove your depth is the most common way to fail it.

Run by a recruiter or a sourcer, occasionally a coordinator working from a script. In most companies they are not the domain expert and are not pretending to be. They check your answers against a short list of requirements from the hiring manager, and their notes become the first thing that manager reads about you.

That last point is why it matters. The recruiter writes the summary that frames you for the rest of the loop. Clear, well-calibrated on level, and pleasant produces a summary that helps you. Dense and long produces a summary that says strong background, hard to follow.

The dominant failure mode is over-rotation: answering a two sentence question with a five minute technical or strategic answer. To this audience it does not demonstrate depth, it demonstrates that you cannot read a room, and it eats the time the recruiter needed for the logistics questions they are accountable for.

The second failure mode is being unprepared on the mechanics. Compensation, notice period, location, and work authorization come up in almost every screen, and hesitancy reads as evasiveness or as not having thought about whether you would take the job.

This screen is also your best chance to gather intelligence. The recruiter knows the loop structure, the interviewers' names, the level, and the band. They are usually willing to share all of it, and almost nobody asks.

# How to use this bank

Copy the probes into the question bank section of your simulator prompt, identifiers exactly as written. This is the one bank to run whole in a single thirty minute session rather than drilling by tag, because the real screen is short and continuous.

The probes carry a difficulty tier: tier one (T1) is the plain version, tier two (T2) is the pressured version, and tier three (T3) is the hardest.

Rehearse the logistics answers out loud until they are boring. Aim for a flat, unhesitant delivery of your notice period, location constraints, authorization status, and compensation position. Any wobble creates work for the recruiter and doubt in the summary they write.

Set your simulator to enforce the depth ceiling below. It is the most valuable configuration in this file.

## Coverage tracker

| Tag | Times drilled |
|---|---|
| narrative | 0 |
| interest | 0 |
| screening | 0 |
| logistics | 0 |
| compensation | 0 |
| intake | 0 |

# The depth ceiling

Add this rule to your simulator prompt verbatim. It changes the recruiter screen from a rehearsal of content into a rehearsal of restraint.

> DEPTH CEILING RULE: In this round, no answer may exceed ninety seconds, and no answer may go deeper than one level of technical or strategic detail. If the candidate begins explaining an architecture, a modelling approach, a market analysis, or a multi-step framework, interrupt them at the point of the second technical term or the second nested clause. Say some version of: "That is helpful, and the hiring manager will want to go deep on that. For me, the short version is enough." Then log a ceiling breach in the run log with the probe identifier. At the end of the session, report the total number of breaches. Three or more breaches is a failed session regardless of answer quality.

The reason is mechanical. The recruiter has a form to complete and roughly twenty five usable minutes. Every minute you spend on depth they cannot evaluate is taken from the questions that determine whether you advance. Depth is not wasted because it is unwelcome, it is wasted because this listener cannot score it and the next one will ask again anyway.

The correct pattern is a two sentence answer plus an offer. Answer at the surface, then say there is a longer version you are happy to go into with the technical panel. That sentence tells the recruiter you have depth and that you know when to deploy it. Recruiters routinely write that observation down.

The rule has one exception. If the recruiter explicitly asks you to go deeper, go one level deeper and stop again. They are usually checking a specific requirement on their list, and one level is enough to tick it.

# The probes

## Narrative

**REC-01 · narrative · T1**
"Tell me a bit about yourself."
*Strong answer contains:* ninety seconds or less, a through-line ending at this role, at most two roles named, and a stop. The answer most worth rehearsing verbatim.

**REC-02 · narrative · T1**
"Walk me through your current role. What do you own?"
*Strong answer contains:* scope in plain terms, one or two headline outcomes, and no architecture, no methodology, and no acronyms the recruiter would have to look up.

**REC-03 · narrative · T2**
"How does your background line up with this job description?"
*Strong answer contains:* three requirements from the posting matched to specific experience, in the posting's own language, plus one honest partial match. Under two minutes.

**REC-04 · narrative · T2**
"What level do you consider yourself, and what is your title trajectory?"
*Strong answer contains:* a direct answer, an honest statement about title inflation or deflation at previous employers if relevant, and a description of scope rather than a defence of a title.

## Interest

**REC-05 · interest · T1**
"What made you apply, or what interested you when I reached out?"
*Strong answer contains:* one specific thing about the company or the role that a search would not have produced by accident, and no flattery.

**REC-06 · interest · T1**
"What do you know about us?"
*Strong answer contains:* the business model in one sentence, the product or segment the role sits in, and one honest question about something the candidate could not determine from outside.

**REC-07 · interest · T2**
"What are you looking for in your next role?"
*Strong answer contains:* two or three criteria that this role can plausibly satisfy, stated as things the candidate is moving toward, with no criticism of the current employer.

## Screening

**REC-08 · screening · T1**
"How many years have you worked with [the core requirement in the posting]?"
*Strong answer contains:* a direct number, the most recent and most relevant example in one sentence, and no expansion into how it worked.

**REC-09 · screening · T2**
"This role requires experience in an area your resume does not show. Tell me about that."
*Strong answer contains:* an honest acknowledgement, the closest adjacent experience, evidence of learning a comparable area quickly, and no attempt to reframe the gap as covered.

**REC-10 · screening · T2**
"Have you worked in a regulated environment, or with a team of this size, or at this stage of company?"
*Strong answer contains:* a direct yes or no, one concrete example if yes, and if no, the nearest analogue plus what the candidate expects to be different.

**REC-11 · screening · T2**
"Are you interviewing anywhere else, and where are you in those processes?"
*Strong answer contains:* an honest general answer (stage and rough timing) without naming companies, and a clear statement of how this role ranks. Useful information for the recruiter, and it sets up timeline conversations later.

## Logistics

**REC-12 · logistics · T1**
"Why are you leaving your current role, or why did you leave your last one?"
*Strong answer contains:* one clean sentence, factually accurate, neutral in tone, and no elaboration unless asked. For a layoff or a restructure, name it plainly and move on. Volunteered detail here is almost always damaging.

**REC-13 · logistics · T1**
"What is your notice period, and when could you start?"
*Strong answer contains:* the exact notice period, any known constraints (a handover, a booked absence, a vesting or bonus date if the candidate chooses to raise it), and a realistic start date.

**REC-14 · logistics · T1**
"Where are you based, and what is your expectation on office days?"
*Strong answer contains:* the candidate's location, their real constraint, and either alignment with the posted arrangement or an early honest flag. Discovering a mismatch in round four wastes everyone's time.

**REC-15 · logistics · T1**
"Are you authorized to work in this location, and do you need any sponsorship now or in the future?"
*Strong answer contains:* a plain factual answer, including any future timing, with no volunteered personal circumstances. Accuracy matters more than brevity on this one.

**REC-16 · logistics · T2**
"Is there any travel, on-call, or schedule requirement that would be a problem for you?"
*Strong answer contains:* a direct answer, one specific constraint if there is one, and flexibility described honestly rather than promised unconditionally.

## Compensation

**REC-17 · compensation · T1**
"What are your compensation expectations?"
*Strong answer contains:* either a question back about the band for the level (preferred, and legal to ask in many places), or a researched range with a note that it depends on the total package. A single precise number given first is the weakest available move.

**REC-18 · compensation · T2**
"That is above our range for this level. How do you want to proceed?"
*Strong answer contains:* no immediate capitulation and no immediate exit, a question about the full package and the level definition, and a clear statement of what would make the conversation worth continuing.

## Intake for you

**REC-19 · intake · T1**
"What questions do you have for me?"
*Strong answer contains:* the loop structure and number of rounds, the names and roles of the interviewers, the level and band, what the hiring manager most wants this person to fix, and the target decision date. Ask these in the screen, not later.

**REC-20 · intake · T2**
"Is there anything else I should know before I write this up?"
*Strong answer contains:* one sentence that fills a gap the conversation exposed, phrased so the recruiter can paste it directly into their summary. The highest-leverage sentence in the round.

# The follow-ups they will actually use

**"Can you give me the short version?"** The most important follow-up in this round. It is a ceiling warning, so treat it as one.

**"So that would be a yes or a no?"** Asked when a screening question gets a nuanced answer. Give the binary first, then one clause of nuance.

**"Roughly how many years?"** Asked when an experience claim arrives without a duration.

**"And that was in your current role, or before?"** Recency check. Recruiters match against a requirement that usually specifies recent experience.

**"How firm is that number?"** Asked after any compensation figure. It tests your flexibility, not your arithmetic.

**"Would you be able to start before then?"** Asked after a notice period. Answer factually rather than eagerly.

**"Is that something you would be comfortable with?"** Asked about a location, travel, or schedule requirement. Ambiguity here creates a problem later.

**"What would it take for you to say yes to us?"** Late screen probe. A real question, and a vague answer wastes it.

# Scoring dimensions for this round

**Brevity.** Are answers inside ninety seconds, with the short version first. Track ceiling breaches as a hard count.

**Level calibration.** Does the candidate describe scope that matches the posted level, in language the recruiter can transfer accurately to the hiring manager.

**Logistics readiness.** Are compensation, notice, location, and authorization answered flatly and immediately, with no hedging or audible discomfort.

**Interest specificity.** Is there one concrete reason for this company that could not have been said about any other posting in the same category.

**Intake quality.** Did the candidate leave with the loop structure, the interviewer names, the level, and the band. A screen that ends without these is a wasted opportunity regardless of performance.

**Communication and presence.** Warmth, easy pace, and a summary-friendly way of speaking. The measure is whether the recruiter could accurately repeat what you said to the hiring manager.

# Landmines

**Over-rotating into depth.** Answering a screening question with an architecture walkthrough or a market thesis. The defining failure of this round.

**Acronyms and internal jargon.** Terms specific to your last employer or your specialty. The recruiter cannot transfer what they cannot spell.

**Hesitating on compensation.** Long pauses, nervous laughter, or an unresearched answer. It reads as a negotiation risk before the process has started.

**Volunteering too much on why you left.** One sentence is the answer. Elaboration turns a neutral fact into a topic.

**Criticizing a former employer.** The recruiter writes down the tone, and it travels with your file through the whole loop.

**Hiding a logistics mismatch.** Concealing a location, authorization, or start date constraint until a later round. It wastes the candidate's time far more than the company's.

**Treating the recruiter as an obstacle.** Condescension toward a non-technical interviewer is noticed, remembered, and reported.

**Asking nothing.** Ending without the loop structure, the names, or the band. Everything you build later depends on knowing who is in the room.

**Negotiating in the screen.** Trying to close terms before an offer exists. It is the wrong conversation with the wrong person at the wrong time.

**Being unfindable afterward.** Slow replies, unclear availability, and missed scheduling. The screen is also an audition for how easy you are to move through a process.

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

Based on "Recruiter Screen: Question Bank," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
