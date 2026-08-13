>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Technical Deep Dive: Question Bank

# What this round is really testing

The technical deep dive decides one thing: how far down does this person go. Not how much they know, which is unmeasurable in an hour, but where the floor of their understanding sits and what they do when they reach it. Every question here exists to find that floor.

Run by engineers, staff engineers, data scientists, or an engineering manager who still reads code. It appears in loops for engineers, data scientists, analysts, and technical product managers, and the bar differs by function: an engineer builds the thing, a product manager reasons about it accurately and knows where their knowledge stops. Both are testable, and the second is not an easier version of the first.

The defining behaviour is the descent. A technical interviewer asks a broad question, listens, then asks a narrower one about the weakest part of the answer. Then another. They keep descending until the candidate either reaches bedrock they can defend or starts generating plausible-sounding language. That transition point is the score.

The main failure mode is bluffing. It is not a moral failing, it is a detection problem: the interviewer already knows the answer, so an invented one is obvious and it retroactively discredits every confident statement from earlier in the hour. "I do not know, here is how I would find out" almost always outscores improvisation.

The second is the tour. Asked how a system worked, the candidate describes the org chart, the timeline, and the vendors, and never draws the data path. The third is the answer with no numbers: throughput, latency, volume, and cost are how a technical interviewer tells whether the candidate was near the system or near the meeting about it.

# How to use this bank

Copy the probes into the question bank section of your simulator prompt, identifiers exactly as written. Tell the simulator to descend: after every answer it must ask one narrower question about the least supported part of what you just said, at least twice, before moving on.

Start at difficulty tier one (T1), move to tier two (T2) once you can answer without a preamble, and reach for tier three (T3) probes only in the final two sessions before the round.

Drill the `dont-know` tag deliberately. Every candidate skips it and it most reliably decides a technical round. The behaviour under test is a sequence, not an admission, and it needs rehearsal like any other answer.

Bring one real system you worked on to every session and answer as many probes as possible against it. Depth on one system beats shallow coverage of five, and it matches how the round runs.

## Coverage tracker

| Tag | Times drilled |
|---|---|
| system-design | 0 |
| data | 0 |
| machine-learning | 0 |
| tradeoffs | 0 |
| failure-modes | 0 |
| dont-know | 0 |

# The probes

## System design

**TECH-01 · system-design · T1**
"Draw the architecture of something you built. Start at the request and end at the response."
*Strong answer contains:* a named entry point, each hop with its purpose, where state lives, and at least one number (requests per second, payload size, latency budget). A diagram with no data path is an org chart.

**TECH-02 · system-design · T2**
"Where is the bottleneck in that system, and how do you know?"
*Strong answer contains:* a specific component, the evidence (a measurement, not an intuition), what would break first under load, and the next bottleneck that appears once the first is fixed.

**TECH-03 · system-design · T2**
"Design a service that accepts payment authorization requests and must respond within a strict latency budget. Walk me through it."
*Strong answer contains:* clarifying questions about volume and the latency target, a synchronous path kept deliberately thin, asynchronous work moved off the critical path, an explicit timeout and fallback behaviour, and what the system does when a dependency is slow rather than down.

**TECH-04 · system-design · T2**
"How would you make that system handle ten times the traffic?"
*Strong answer contains:* the component that breaks first, a distinction between scaling out and scaling up with a reason, what becomes newly expensive (usually the database or a shared lock), and what the candidate would measure before changing anything.

**TECH-05 · system-design · T3**
"Two services need the same data and disagree about it. How do you resolve that?"
*Strong answer contains:* a named ownership model (one writer, others read), an honest treatment of eventual consistency and the window it creates, what the user sees during that window, and the reconciliation path.

**TECH-06 · system-design · T3**
"You need to change a data format that three downstream consumers depend on and you cannot coordinate a simultaneous release. Sequence it."
*Strong answer contains:* a versioned or additive transition, a dual-write or dual-read period, a way to verify all consumers have migrated, and the cleanup step that most people skip.

## Data

**TECH-07 · data · T1**
"Walk me through where the data in your last project came from and what happened to it before anyone used it."
*Strong answer contains:* the source system, the transport, the transformations, and at least one known quality problem the candidate had to handle.

**TECH-08 · data · T2**
"A daily number your team relies on dropped by thirty percent overnight. Diagnose it."
*Strong answer contains:* checking whether the pipeline ran before checking whether the world changed, a comparison of definition versus data versus reality, an ordered list of checks from cheapest to most expensive, and the point the candidate would escalate at.

**TECH-09 · data · T2**
"How do you know a dataset is trustworthy enough to make a decision on?"
*Strong answer contains:* concrete checks (row counts against expectation, distribution shift, null rates, join fan-out, freshness), what those checks do not catch, and a habit of reconciling against an independent source.

**TECH-10 · data · T2**
"Explain the difference between a metric definition problem and a data quality problem, using an example from your work."
*Strong answer contains:* an example where the numbers were correct and the definition was wrong, why that is harder to detect, and the governance habit the candidate adopted afterward.

**TECH-11 · data · T3**
"You need to backfill two years of history into a new schema without taking the live system down. Plan it."
*Strong answer contains:* chunked processing with a resumable checkpoint, load isolation from the production path, an idempotency guarantee, a verification pass comparing old and new, and a rollback story.

## Machine learning and artificial intelligence

**TECH-12 · machine-learning · T1**
"Explain a machine learning (ML) model you have worked with to someone who does not build them. What does it actually do?"
*Strong answer contains:* the input, the output, the decision it feeds, and the thing it is genuinely bad at. Jargon density is inversely correlated with score on this probe.

**TECH-13 · machine-learning · T2**
"How did you evaluate that model, and why those measures?"
*Strong answer contains:* the evaluation metric tied to the business cost of each error type, the baseline it was compared against, how the evaluation set was constructed, and an acknowledgement of leakage risk.

**TECH-14 · machine-learning · T2**
"Your model has high accuracy and the business outcome did not improve. What happened?"
*Strong answer contains:* class imbalance making accuracy meaningless, a gap between the model output and the action taken on it, a threshold or workflow problem, or an evaluation set that does not match production. The candidate should name several and say which they would check first.

**TECH-15 · machine-learning · T2**
"How would you detect that a deployed model is degrading before a person complains?"
*Strong answer contains:* input distribution monitoring, output distribution monitoring, delayed label handling, a proxy metric for the period before labels arrive, and an alert threshold the candidate would actually set.

**TECH-16 · machine-learning · T3**
"You are asked to add a large language model (LLM) to an existing product workflow. What breaks that people do not expect?"
*Strong answer contains:* non-determinism and its effect on testing, latency and cost per call at real volume, evaluation being harder than building, failure being silent rather than loud, and a plan for what the system does when the output is wrong rather than absent.

**TECH-17 · machine-learning · T3**
"How would you evaluate a system whose output is free text, where there is no single correct answer?"
*Strong answer contains:* a graded rubric applied consistently, a held-out set with human labels on a sample, automated checks for failures that are cheap to detect (format, refusal, hallucinated identifiers), a regression suite of past failures, and honesty about the limits of any automated judge.

**TECH-18 · machine-learning · T3**
"When is retrieval augmented generation (RAG) the wrong answer to a knowledge problem?"
*Strong answer contains:* cases where the failure is in retrieval quality rather than generation, where the corpus is not the source of truth, where the query is a computation rather than a lookup, and where a deterministic system would be cheaper and auditable.

## Tradeoffs

**TECH-19 · tradeoffs · T1**
"Tell me about a technical decision where both options were defensible."
*Strong answer contains:* both cases stated fairly, the criterion that broke the tie, and what the candidate has since learned about whether the criterion was right.

**TECH-20 · tradeoffs · T2**
"When have you chosen the worse engineering answer on purpose?"
*Strong answer contains:* the constraint that justified it, the ongoing cost stated explicitly, whether the debt was written down and scheduled, and what actually happened to it.

**TECH-21 · tradeoffs · T2**
"Build or buy, for a component in your last system. Argue it."
*Strong answer contains:* total cost including integration and operational burden, the switching cost of the vendor path, whether the component is close to the company's differentiation, and a stated reversal condition.

**TECH-22 · tradeoffs · T2**
"You can have correctness or availability during a partial outage, not both. Which do you pick for a payments flow?"
*Strong answer contains:* recognition that the answer differs by operation (reads versus writes, authorization versus reporting), the user-visible consequence of each choice, and who owns the decision in the organization.

**TECH-23 · tradeoffs · T3**
"Argue against the architecture you just described to me."
*Strong answer contains:* a genuine structural weakness rather than a cosmetic one, the conditions under which it becomes fatal, and what the candidate would monitor to see it coming.

## Failure modes

**TECH-24 · failure-modes · T1**
"What is the worst production incident you have been close to?"
*Strong answer contains:* detection time, the immediate mitigation separated from the durable fix, the candidate's own actions in first person singular, and one systemic change that came out of it.

**TECH-25 · failure-modes · T2**
"How does the system you described fail, and what does a user see when it does?"
*Strong answer contains:* several distinct failure modes (dependency slow, dependency down, partial write, poison message, deploy of a bad version), the user-visible behaviour for each, and which of them the system currently handles poorly.

**TECH-26 · failure-modes · T2**
"A dependency starts responding in eight seconds instead of eighty milliseconds and never errors. What happens to your system?"
*Strong answer contains:* thread or connection pool exhaustion, the cascade into unrelated traffic, timeouts and circuit breaking as the fix, and the observation that slow is more dangerous than down.

**TECH-27 · failure-modes · T2**
"What would you add to a system you inherited that had no monitoring at all? First three things."
*Strong answer contains:* a prioritization tied to what hurts the business, at least one measure from the user's perspective rather than the server's, an alert a human would act on, and a rejection of alerting on everything.

**TECH-28 · failure-modes · T3**
"Design the rollback for a change that is already half deployed and has written bad data."
*Strong answer contains:* stopping the bleeding before repairing, separating the code rollback from the data repair, identifying the affected records, an idempotent repair, and the customer communication decision.

**TECH-29 · failure-modes · T3**
"Something works in staging and fails in production. Give me your ordered list of causes."
*Strong answer contains:* an ordered list starting with configuration and data differences, moving through scale and concurrency, then dependency versions and network policy, with how each is confirmed rather than guessed.

## What you would do if you did not know

The highest-value tag in the bank and the least practised. The interviewer is not testing knowledge here, they are testing behaviour at the edge of it.

**TECH-30 · dont-know · T1**
"How does the layer below the one you work in actually work?"
*Strong answer contains:* an honest boundary stated early, the accurate part of the mental model up to that boundary, and a specific answer for how the candidate would find out. Confident invention scores zero.

**TECH-31 · dont-know · T2**
"You are handed a system nobody understands and the person who built it has left. Day one. What do you do?"
*Strong answer contains:* reading the interfaces and the monitoring before the code, tracing one real request end to end, writing down the model and getting it corrected by whoever is left, and a bias toward changing something small early to test understanding.

**TECH-32 · dont-know · T2**
"Explain something technical you learned recently. What was hard about it and what finally made it click?"
*Strong answer contains:* a real point of confusion, the specific resource or experiment that resolved it, and evidence the candidate learns by building rather than only by reading.

**TECH-33 · dont-know · T2**
"I am going to ask you something you probably cannot answer. How does the system decide which of two conflicting writes wins?"
*Strong answer contains:* either a correct answer for a system the candidate knows, or a clean stop, a statement of what the candidate does know about the problem class, and the question they would ask the person who owns it. Function-specific note: for a product manager, the clean stop plus the right question is a full score.

**TECH-34 · dont-know · T3**
"You have to make a technical call this week and you do not have the expertise. Walk me through how you get to a decision you can defend."
*Strong answer contains:* identifying who has the expertise, framing the question so a specialist can answer it in one pass, seeking a dissenting second opinion, writing down the assumptions the decision rests on, and setting a review point.

**TECH-35 · dont-know · T3**
"Tell me about a time you were confidently wrong about something technical. How did you find out?"
*Strong answer contains:* the specific belief, the mechanism that exposed it (a measurement, a colleague, an incident), how fast the candidate updated in public, and the habit adopted to catch the same error class earlier.

# The escalation ladder

A technical interviewer does not jump. They descend one rung at a time, each rung removing an abstraction the candidate was standing on. Build this ladder into your simulator explicitly: the round is unwinnable if you have only practised rung one.

**Rung one: describe.** "Tell me about the system you built." The candidate controls the frame. Almost everyone performs well here, which is why nothing is scored yet.

**Rung two: locate.** "Which part did you personally build." The tour narrows to the candidate. Anyone narrating someone else's work thins out at this rung.

**Rung three: quantify.** "How much traffic, what latency, how much data." Numbers separate people who operated the system from people who attended meetings about it.

**Rung four: mechanism.** "Why did you choose that, and what was the alternative." The candidate must show a decision existed and that they understood both sides.

**Rung five: stress.** "What happens at ten times the load, or when that dependency is slow." The design meets a condition it was not built for.

**Rung six: internals.** "Why does that component behave that way." One layer below where the candidate normally works. Most people reach their floor here, and that is normal.

**Rung seven: the edge.** "How would you find out." The interviewer has established the floor and is testing what happens standing on it. This rung decides senior candidates.

Descend with the interviewer, say at each rung how confident you are, and stop cleanly at your floor rather than one rung past it. Stopping at rung six with "that is past where I can speak accurately, here is what I do know and here is how I would confirm the rest" scores higher than a fluent rung seven answer that is wrong. Interviewers are calibrated for this transition and they will notice it.

# The follow-ups they will actually use

**"How do you know?"** The most common follow-up in the round. It converts an assertion into either evidence or an admission.

**"What were the numbers?"** Volume, latency, size, cost. Asked whenever a system is described without them.

**"What did you personally write or decide?"** Separates the builder from the narrator.

**"What was the alternative you rejected, and why?"** A design with one option was not designed.

**"What happens when that fails?"** Applied to whichever component the candidate treated as reliable.

**"Where does that break?"** Applied to whichever component the candidate is proudest of.

**"Walk me one layer down."** The literal descent. Repeated until the floor is found.

**"What would you do differently if you built it again?"** Tests whether the candidate has kept thinking about it since.

**"How would you find out?"** Asked at the floor. The highest-signal question in the round.

**"Is there a simpler design that does ninety percent of this?"** Tests whether the candidate reaches for complexity by default.

# Scoring dimensions for this round

**Depth of floor.** How many rungs down the candidate can go while remaining accurate. Measured by where they stop, not by how much they said.

**Behaviour at the floor.** What happens at the boundary: a clean stop plus a method, or improvisation. This dimension can be worth more than depth itself.

**Correctness.** Are the technical claims true. One confidently wrong statement discounts everything else in the hour, which is why bluffing is a losing strategy rather than a risky one.

**Tradeoff reasoning.** Can the candidate state both sides, name the criterion, and identify the ongoing cost of the choice they made.

**Failure thinking.** Does the candidate reach for failure modes unprompted, including the slow-dependency case and the partial-failure case, and can they describe what the user sees.

**Communication and presence.** Can the candidate explain a technical system to a listener at a chosen level, adjust when the listener is more or less expert, and stay steady through six consecutive narrowing questions.

# Landmines

**Bluffing.** Generating plausible language past the floor. The interviewer knows the answer, and the discovery invalidates the confident material from earlier in the hour.

**The tour.** Describing the team, the timeline, and the vendors instead of the data path. It reads as proximity to the work rather than participation in it.

**No numbers.** Talking about scale without any. Every technical interviewer uses this as a first-pass filter.

**Buzzword stacking.** Naming technologies rather than explaining behaviour. It starts the descent two rungs lower than it otherwise would.

**Over-engineering the answer.** Reaching for a distributed, queued, multi-region design for a problem that a single well-indexed table solves. Interviewers read it as inexperience, not ambition.

**Ignoring failure until asked.** Presenting a design as though dependencies are always fast and always available. Unprompted failure thinking is a senior marker and its absence is noted.

**Defending a wrong claim.** Doubling down after a correction rather than updating. The update is the thing being scored, not the original error.

**Hedging everything.** The opposite failure. Refusing to commit to any claim so nothing can be wrong. It reads as no floor at all.

**Answering a different question.** Being asked how the system fails and answering how it was built. Common under pressure, and it costs the entire probe.

**Apologizing for your background.** A product manager or analyst opening with a disclaimer about not being technical. State your floor as a fact, not an apology, then go as deep as you can.

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

Based on "Technical Deep Dive: Question Bank," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
