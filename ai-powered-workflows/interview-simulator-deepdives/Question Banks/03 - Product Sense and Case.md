>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Product Sense and Case: Question Bank

# What this round is really testing

This round decides whether you can be trusted with an undefined problem. Not whether you get the right answer: there is no right answer, and the interviewer usually does not have one. The question is whether, handed something vague and expensive, you produce a structured path to a defensible call or a pile of opinions.

Usually run by a product manager one or two levels above the role, sometimes paired with a design lead or a general manager. Versions exist outside product management: designers get a critique and a redesign, marketers get a growth or positioning case, analysts get a measurement and diagnosis case, engineers get the same round in a system design costume. The scoring shape is identical even when the surface changes, so the probes below re-point at whichever function you are interviewing for.

The first failure mode is skipping the frame. A candidate hears the prompt and starts generating features in the first thirty seconds. Ideas are the cheapest thing in the room. The structure that says which ideas matter is what is being bought.

The second is the frame with no decision at the end. A candidate builds an elegant segmentation, lists six options, weighs them evenly, and never chooses. The interviewer reads that as someone who will run a great workshop and never ship. Pick, say why, and name what would change your mind.

The third is a hollow metric: success measures that cannot move, cannot be attributed, or would look identical if the product got worse. The fourth is the case answered entirely from the interviewer's chair, reciting what a well-known company did instead of reasoning from the user in front of you.

# How to use this bank

Copy the probes into the question bank section of your simulator prompt, identifiers exactly as written. The short probes are warm-ups and diagnostics. The six full cases at the end are the actual round: run them in real time, on a clock, with the simulator playing an interviewer who interrupts.

Start at difficulty tier one (T1), move to tier two (T2) once you can answer without a preamble, and reach for tier three (T3) probes only in the final two sessions before the round.

Run a full case no more than twice a week and debrief each properly. Six cases run badly teach you to talk faster. Two, with your framing rebuilt between them, teach you to think.

Tell the simulator to hold you to a clock: two minutes to clarify, three to frame, ten to work, three to land and defend. Most failed cases come from spending eighteen minutes being interesting and two minutes being useful.

## Coverage tracker

| Tag | Times drilled |
|---|---|
| user-empathy | 0 |
| opportunity | 0 |
| metrics | 0 |
| tradeoffs | 0 |
| critique | 0 |
| strategy | 0 |
| execution | 0 |
| case | 0 |

# The probes

## User empathy

**CASE-01 · user-empathy · T1**
"Pick a product you use every day. Who is it for, and who is it quietly not for?"
*Strong answer contains:* a named primary user with a specific job to be done, an explicit excluded segment, and a reason the exclusion is a deliberate decision rather than an oversight.

**CASE-02 · user-empathy · T2**
"Describe the last time you watched someone use something you built. What surprised you?"
*Strong answer contains:* a specific observed behaviour that contradicted an assumption, what the candidate changed, and evidence they now build to surface such surprises earlier.

**CASE-03 · user-empathy · T3**
"A segment of your users is loudly asking for a feature. Your data says they will barely use it. How do you decide?"
*Strong answer contains:* a hypothesis about why the request and the behaviour disagree, a cheap test separating stated from revealed preference, and a decision rule set in advance.

## Opportunity and sizing

**CASE-04 · opportunity · T1**
"How would you size the opportunity for a new payments feature aimed at small merchants?"
*Strong answer contains:* a stated approach (top down, bottom up, or both), assumptions written out loud with rough numbers, one sanity check against a known quantity, and which assumption the estimate is most sensitive to.

**CASE-05 · opportunity · T2**
"You have three candidate markets and can only enter one. What do you need to know to choose?"
*Strong answer contains:* three or four decision criteria named before any market is discussed, the cheapest source for each, and a pre-committed rule for walking away from all three.

**CASE-06 · opportunity · T3**
"Your estimate says the opportunity is large and your instinct says it is not. Which do you trust?"
*Strong answer contains:* an audit of the assumption most likely to be wrong, a named mechanism by which large estimates get inflated (double counting, ignoring willingness to pay, assuming full penetration), and what evidence would settle it.

## Metrics

**CASE-07 · metrics · T1**
"You launch a feature. What is the one metric you watch, and what is the one you watch to make sure you did not break something?"
*Strong answer contains:* a primary metric tied to the user behaviour the feature is meant to change, a guardrail metric, and a stated time window for both.

**CASE-08 · metrics · T2**
"Engagement is up fifteen percent and revenue is flat. What is your first hypothesis?"
*Strong answer contains:* at least three competing explanations (mix shift, measurement artifact, engagement without intent), the order the candidate would test them in, and the cheapest test first.

**CASE-09 · metrics · T2**
"Define success for a feature that has no obvious numeric outcome, like a trust or safety improvement."
*Strong answer contains:* a proxy chain from the intended outcome down to something observable, what the proxy fails to capture, and a qualitative check alongside it.

**CASE-10 · metrics · T3**
"Your north star metric is being gamed by an internal team. What do you do?"
*Strong answer contains:* recognition that the metric design created the incentive, a fix at the metric or incentive level rather than a scolding, and a check for other metrics with the same weakness.

## Tradeoffs

**CASE-11 · tradeoffs · T1**
"You can ship half the feature on time or all of it two months late. Which and why?"
*Strong answer contains:* a question about what the deadline is actually attached to, a stated criterion for the split, and a named test of whether the half is independently useful.

**CASE-12 · tradeoffs · T2**
"A change would improve conversion by a measurable amount and make the experience slightly worse for existing customers. How do you decide?"
*Strong answer contains:* a sizing of both sides in comparable units, a reversibility check, a limited rollout that produces evidence, and a stated threshold for shipping or reverting.

**CASE-13 · tradeoffs · T2**
"Engineering says the right architecture takes a quarter and the workaround takes two weeks. Argue both sides, then pick."
*Strong answer contains:* the cost of the workaround stated as ongoing rather than one-time, the conditions under which each is correct, a pick, and a written trigger for revisiting.

**CASE-14 · tradeoffs · T3**
"You have to remove something people use. Walk me through it."
*Strong answer contains:* sizing of the affected group, a migration or substitute path, a communication sequence with lead time, and a defined point of no return.

## Critique

**CASE-15 · critique · T1**
"Take any product flow you know well and tell me the worst thing about it."
*Strong answer contains:* a specific step, a hypothesis about why it exists (usually a real constraint, not stupidity), and a proposed change with a stated risk.

**CASE-16 · critique · T2**
"Here is a competitor's onboarding flow. What are they optimizing for, and what are they willing to lose?"
*Strong answer contains:* an inferred objective, evidence in the design for that inference, and a named cost the competitor has accepted deliberately.

**CASE-17 · critique · T3**
"Critique something you built. Not the constraints you were under: the decision you would defend differently."
*Strong answer contains:* a decision the candidate owned, an honest account of what they got wrong about the user or the market, and no retreat into resourcing.

## Strategy

**CASE-18 · strategy · T2**
"A larger competitor just shipped your differentiator for free. What now?"
*Strong answer contains:* a check on whether the differentiator was the reason customers stayed, at least two structurally different responses (move up the stack, go narrower, compete on a dimension they cannot copy), and a stated basis for choosing.

**CASE-19 · strategy · T2**
"What should this company build next, and what should it stop building?"
*Strong answer contains:* a thesis about where the company's advantage compounds, one concrete build, one concrete stop, and an acknowledgement of what the candidate cannot know from outside.

**CASE-20 · strategy · T3**
"Make the strongest case against the strategy we are currently pursuing."
*Strong answer contains:* a fair statement of the current strategy first, one structural objection rather than an execution complaint, and the evidence that would prove the objection right or wrong.

## Execution

**CASE-21 · execution · T2**
"You are two weeks from launch and discover a problem that affects a small share of users. Walk me through the next hour."
*Strong answer contains:* sizing the impact before deciding, who gets told in what order, the decision owner named, and a default action if the data does not arrive in time.

**CASE-22 · execution · T3**
"The launch metrics are ambiguous after four weeks. Do you keep it, kill it, or extend?"
*Strong answer contains:* a check on whether the test was powered to detect the effect at all, the cost of each option, a decision, and a pre-commitment to a date so the ambiguity does not become permanent.

## Full cases

Run these live. Each has a note on who typically leads it and what is being scored. Those two lines are for the person building the simulator and are never read aloud.

**CASE-23 · case · T2**
"Northwind Payments wants to grow the number of small merchants who accept payments through us. Design the approach."
*Who leads this:* a product manager one level above the role, occasionally with a growth lead observing.
*What they are really testing:* whether the candidate segments before ideating, and whether they can distinguish an acquisition problem from an activation problem before proposing anything.
*Strong answer contains:* two or three clarifying questions that change the answer, an explicit segmentation with one segment chosen and justified, the specific barrier for that segment, two or three interventions ranked by cost and evidence, a success metric with a guardrail, and a stated first test.

**CASE-24 · case · T2**
"Merchants at Northwind Payments are abandoning setup partway through. Diagnose it."
*Who leads this:* a product manager or an analytics lead. In an analyst loop this becomes the entire round.
*What they are really testing:* diagnostic discipline. Whether the candidate narrows before guessing, and whether they know which data would separate the hypotheses.
*Strong answer contains:* a funnel decomposition, a question about whether abandonment is concentrated at one step or spread, at least three hypothesis families (friction, trust, requirement the merchant cannot satisfy, technical failure), the cheapest disambiguating evidence for each, and a fix proposed only after the diagnosis.

**CASE-25 · case · T2**
"Design a way for Northwind Payments to help merchants understand why a payment was declined."
*Who leads this:* a product manager, frequently paired with a design lead who will push on the interface.
*What they are really testing:* whether the candidate can hold two users at once (the merchant and the end customer) and whether they notice the constraint that not all decline reasons can be safely disclosed.
*Strong answer contains:* explicit naming of the disclosure constraint without being prompted, a user need stated as a job rather than a feature, a proposed experience with what is shown and withheld, and a measure of whether merchants act differently afterward.

**CASE-26 · case · T3**
"Northwind Payments has a fraud detection system that blocks too many legitimate transactions. You own the tradeoff. What do you do?"
*Who leads this:* a senior product manager, often with a risk or data science partner in the room.
*What they are really testing:* whether the candidate understands that the false positive rate and the false negative rate move together, and whether they can turn a threshold into a business decision with named owners.
*Strong answer contains:* the two error types named with their different costs, a segmentation showing the tradeoff is not uniform across merchants, a proposal that changes the shape of the problem rather than only the threshold (review queues, step-up verification, per-segment policy), the metric pair being managed, and who signs off on the risk appetite.

**CASE-27 · case · T3**
"Northwind Payments is considering expanding into a new country. Should we, and what would you need to decide?"
*Who leads this:* a general manager, a director of product, or an executive in a later round.
*What they are really testing:* whether the candidate can build a decision structure under heavy uncertainty and resist producing a research plan with no recommendation attached.
*Strong answer contains:* a small set of decision criteria set out before any analysis, a rough sizing with assumptions visible, the regulatory and local payment method constraints named as first-class rather than an afterthought, a recommendation with a confidence level, and the one piece of evidence that would flip it.

**CASE-28 · case · T3**
"You have a machine learning model in production that is quietly getting worse. Your team disagrees about whether to retrain, rebuild, or roll back. Run the decision."
*Who leads this:* a senior product manager or an engineering leader. In a technical loop this case belongs to the technical deep dive instead.
*What they are really testing:* whether the candidate can separate a data problem from a model problem from a measurement problem, and whether they can decide with a divided team.
*Strong answer contains:* a first question about whether the degradation is real or a measurement change, distinct hypotheses (input drift, label drift, a broken upstream pipeline, a changed user population), the cheapest check for each, a decision with a rollback path, and a plan for how the disagreement gets resolved rather than absorbed.

# The follow-ups they will actually use

Case interviewers escalate by adding constraints. Each follow-up removes an escape route until only the candidate's reasoning is left. Load these into the simulator and have it interrupt rather than wait politely.

**"Why that segment and not the other one?"** Asked the moment a choice is made without stated criteria.

**"What would you do if you could not do that?"** Removes the candidate's preferred solution and tests whether the frame survives without it.

**"How did you know that was the right metric?"** Tests whether the measure was chosen or borrowed. Follow-up to the follow-up: "what would make that metric go up while the product got worse".

**"What is your estimate most sensitive to?"** Asked after any sizing. A candidate who cannot name the load-bearing assumption did not build the estimate, they recited it.

**"Say the experiment comes back flat. Then what?"** Tests whether the candidate has a decision rule or just a hope.

**"You have half the time and half the budget."** Compression test. Watches whether the candidate cuts scope coherently or shaves everything evenly.

**"Who disagrees with this inside the company, and what is their strongest argument?"** Tests whether the candidate can hold the opposing case fairly.

**"What are you giving up by doing this?"** Every proposal costs something. Naming it unprompted is the level signal.

**"Convince me you are wrong."** Late-stage probe. Tests intellectual honesty and whether the candidate is attached to the answer or the reasoning.

**"Give me the recommendation in three sentences."** Compression close. If the frame was real, the summary is easy.

# Scoring dimensions for this round

Score each one to five. Strong on structure and weak on decisiveness is the most common near-miss profile in this round, and it is fixable in a week of practice.

**Framing.** Did a structure appear before ideas did, was it stated out loud, and did it organize the rest of the answer rather than get abandoned after a minute.

**Clarifying and assumptions.** Were the questions asked ones whose answers would change the approach, and were assumptions stated explicitly rather than smuggled in.

**Decisiveness.** Was a choice made, with a reason, and with a named condition that would reverse it. Listing options without picking scores two however good the options were.

**Measurement.** Is the proposed success metric attributable, movable, and paired with a guardrail. Does the candidate know what would make it go up for the wrong reasons.

**Depth on one thread.** Did the candidate go three levels deep somewhere, rather than one level deep everywhere. Breadth without a single deep dive reads as surface fluency.

**Communication and presence.** Signposting, time control, graceful handling of an interruption, and a clean landing that a busy person could repeat to someone else.

# Landmines

**Feature vomit.** Generating solutions in the first minute. The most common way this round is lost, and the interviewer will have stopped scoring content by minute three.

**The framework recital.** Naming a well-known acronym framework and filling it in mechanically without adapting it to the prompt. Interviewers hear it constantly and read it as memorized rather than thought.

**No decision.** An even-handed comparison with no recommendation. It reads as risk aversion at the level where decisions are the job.

**The borrowed answer.** Reciting what a large well-known company did. It answers a different question and signals no independent reasoning.

**Assumption smuggling.** Building an estimate on numbers introduced quietly and never flagged. When the interviewer challenges one, the whole answer collapses.

**Ignoring the constraint you were handed.** The prompt said the budget is fixed or the disclosure is restricted, and the answer quietly ignores it. Interviewers plant these deliberately.

**The unmovable metric.** Proposing a success measure that cannot shift inside the horizon of the decision, or that would look the same if the product degraded.

**Breadth with no depth.** Six shallow branches and no single thread taken to a real conclusion. Pick one and go all the way down.

**Defensiveness under challenge.** Treating pushback as an attack rather than new information. It is usually a test of whether new evidence updates the answer.

**Losing the clock.** Spending most of the time on setup and rushing the recommendation. The recommendation is the part being scored.

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

Based on "Product Sense and Case: Question Bank," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
