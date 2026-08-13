>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Northwind Payments Technical Panel Super Simulator

**Round being simulated:** Live video panel, 60 minutes, Thursday 2 July 2026, 1:00 in the afternoon Pacific
**Panel:** Ines Kowalczyk, Staff Engineer, Money Movement. Marcus Dube, Engineering Manager, Authorization and Risk Platform.
**Their stated focus:** the recruiter said "systems and how you work under failure, no live coding." Roughly 70 percent design and data, 30 percent incidents and operability.
**Built:** 21 June 2026
**Build:** Super Simulator, the heavy build. Chosen because 60 minutes with two people is a coverage problem: the real fear is a topic that never got drilled arriving cold. A Mock Kit would have been two hours cheaper and would not have covered the ground.

> **Worked illustration.** Fictional candidate, fictional company, fictional interviewers, illustrative numbers.

---

# How to use this file

Three layers. The **engine** is the structure every answer runs through. The **banks** are breadth, so run six is still finding new ground. The **worked answers** are depth, fully written for the questions most likely to arrive and most likely to be fumbled.

Say "run a mock" to start. Everything else is read by the bot, not by you.

---

# The interviewers

## Ines Kowalczyk, Staff Engineer, Money Movement

- **Background:** came up through database and data platform work. Owns the Ledger data model. Wrote the June 2025 post on moving reconciliation off the overnight batch window, and gave a 2025 talk that spent nine of twenty minutes on the migration comparison period.
- **What they test:** whether this person has actually changed a live system that holds money, or built new things beside old things and called it a migration.
- **What wins them:** the verification method stated before the result. Edge cases treated as the main event. A named cost for every change.
- **What loses them:** a throughput number with nothing behind it. A migration described as a sequence of steps with no failure branch. Treating a shard key as an implementation detail.
- **Time weighting:** roughly 35 minutes of the round.

## Marcus Dube, Engineering Manager, Authorization and Risk Platform

- **Background:** six years as a site reliability engineer before three years in management. Still carries a pager one week in six by choice. Listed as a contact on the February 2026 authorization degradation post-mortem.
- **What they test:** whether this person has been woken up, what they did, and whether they can describe it from the customer inward rather than from the dashboard outward.
- **What wins them:** the user-visible symptom first. Detection time and who detected it. Mitigation separated from durable fix. First person singular.
- **What loses them:** answering "what did the customer see" with a graph. Being the narrator of an incident rather than a participant. Any suggestion that good engineering makes on-call unnecessary.
- **Time weighting:** roughly 25 minutes of the round.

**The one mental cue:** every answer needs a mechanism Ines can push on and a consequence Marcus can picture a customer experiencing.

---

# What this panel knows about me

- [ ] Have read my resume closely
- [x] Know my current title and employer only
- [ ] Have seen a public profile and a referral note
- [ ] Know nothing except that I passed the screen

**Rule for the bot:** they were sent the resume this morning and skimmed it. They know Senior Backend Engineer at Beacon Pay, and that there was a coding exercise they have not personally reviewed. Do not reference Lumen Streams or Hearthstone Labs unless I bring them up. Do not reference any specific project on the resume by name.

---

# The engine

*Beats for a technical deep dive. A behavioural round would want different ones and borrowing them would produce answers that miss.*

1. **Answer the question asked, in one sentence.** Not a preamble, not the setup. The claim.
2. **The mechanism.** How it actually works, one level below the claim. This is where Ines lives.
3. **The verification.** How I knew it was right. Not that it worked, how I knew.
4. **The consequence.** What a customer or an operator experienced, in words a non-specialist would use. This is where Marcus lives.
5. **The cost.** What I gave up, or what is still ugly. Never end on a clean win.

**The opener that buys ten seconds and shows structure:**

> "Let me answer that directly and then go one level down, because the interesting part is a level below the answer."

**Length discipline:** 90 seconds for a design question, 60 for a mechanism question, 45 for an incident question. Marcus's questions want shorter answers than Ines's, which is counterintuitive and worth rehearsing.

**Close every answer with:**

> The cost, or the thing still unresolved. "What that cost us was..." or "the part that is still ugly is..."

---

# Story drill table

| Card | One line | Numbers | Best for | Which interviewer |
|---|---|---|---|---|
| 1 | Idempotency primitives for the payment interface | about 95 percent fewer duplicate charge incidents, about 4 million transactions a day, 2 client integrations broken | correctness, interface design, trade-offs, being wrong | Ines primarily, Marcus on the rollout failure |
| 2 | Single instance to sharded cluster, live | about 140 million rows compared, 0.4 percent then 31 real disagreements, about 7 times write throughput, 4 phases over 4 months | migration, verification, data modelling, risk | Ines, this is her territory |
| 3 | Bare metal to containerised service mesh | tail down about 38 percent, median about 4 percent worse, 14 services, about 6 engineering weeks a quarter estimated | measurement judgment, operability, cross-team | Marcus primarily, Ines on the metric argument |
| 4 | **Does not exist.** The 2024 duplicate charge incident: found by a customer, about six hours | detection about 6 hours, found by a platform customer, not by us | incidents, detection, on-call | Marcus. This is the gap. |

---

# Question bank

*Probes from Question Bank 04, identifiers unchanged. Northwind-specific probes carry an `NW-TECH` prefix. Grading notes are never read aloud.*

## System design

```
**TECH-01 · system-design · T1**
"Draw the architecture of something you built. Start at the request and end at the response."
*Strong answer contains:* a named entry point, each hop with its purpose, where state lives, and at least one number. A diagram with no data path is an organisation chart.
```

```
**TECH-02 · system-design · T2**
"Where is the bottleneck in that system, and how do you know?"
*Strong answer contains:* a specific component, a measurement rather than an intuition, what breaks first under load, and the next bottleneck that appears once the first is fixed.
```

```
**TECH-04 · system-design · T2**
"How would you make that system handle ten times the traffic?"
*Strong answer contains:* the component that breaks first, scaling out versus up with a reason, what becomes newly expensive, and what to measure before changing anything.
```

```
**TECH-05 · system-design · T3**
"Two services need the same data and disagree about it. How do you resolve that?"
*Strong answer contains:* a named ownership model, honest treatment of eventual consistency and the window it creates, what the user sees during that window, and the reconciliation path. Ines will ask this one and the third element is the one Alex keeps dropping.
```

```
**TECH-06 · system-design · T3**
"You need to change a data format that three downstream consumers depend on and you cannot coordinate a simultaneous release. Sequence it."
*Strong answer contains:* a versioned or additive transition, a dual-write or dual-read period, a way to verify all consumers migrated, and the cleanup step most people skip.
```

## Data

```
**TECH-09 · data · T2**
"How do you know a dataset is trustworthy enough to make a decision on?"
*Strong answer contains:* concrete checks, a statement of what those checks do not catch, and a habit of reconciling against an independent source.
```

```
**TECH-11 · data · T3**
"You need to backfill two years of history into a new schema without taking the live system down. Plan it."
*Strong answer contains:* chunked processing with a resumable checkpoint, load isolation from the production path, an idempotency guarantee, a verification pass comparing old and new, and a rollback story. Card 2 owns this almost completely and it should be a five.
```

## Tradeoffs

```
**TECH-20 · tradeoffs · T2**
"When have you chosen the worse engineering answer on purpose?"
*Strong answer contains:* the constraint that justified it, the ongoing cost stated explicitly, whether the debt was written down and scheduled, and what actually happened to it. The two isolated hot merchant shards are the honest answer.
```

```
**TECH-22 · tradeoffs · T2**
"You can have correctness or availability during a partial outage, not both. Which do you pick for a payments flow?"
*Strong answer contains:* recognition that the answer differs by operation, reads versus writes and authorization versus reporting, the user-visible consequence of each choice, and who owns the decision in the organisation.
```

```
**TECH-23 · tradeoffs · T3**
"Argue against the architecture you just described to me."
*Strong answer contains:* a genuine structural weakness rather than a cosmetic one, the conditions under which it becomes fatal, and what to monitor to see it coming.
```

## Failure modes

```
**TECH-24 · failure-modes · T1**
"What is the worst production incident you have been close to?"
*Strong answer contains:* detection time, who detected it, the immediate mitigation separated from the durable fix, first person singular actions, and one systemic change that came out of it. Card 4 owns this and Card 4 does not exist.
```

```
**TECH-25 · failure-modes · T2**
"How does the system you described fail, and what does a user see when it does?"
*Strong answer contains:* several distinct failure modes, the user-visible behaviour for each, and which of them the system currently handles poorly. The second clause is the one that gets dropped.
```

```
**TECH-26 · failure-modes · T2**
"A dependency starts responding in eight seconds instead of eighty milliseconds and never errors. What happens to your system?"
*Strong answer contains:* pool exhaustion, the cascade into unrelated traffic, timeouts and circuit breaking as the fix, and the observation that slow is more dangerous than down. Note: this is very close to Northwind's own February 2026 incident. Acknowledge having read the post-mortem rather than pretending.
```

```
**TECH-28 · failure-modes · T3**
"Design the rollback for a change that is already half deployed and has written bad data."
*Strong answer contains:* stopping the bleeding before repairing, separating code rollback from data repair, identifying affected records, an idempotent repair, and the customer communication decision. The last one is the one Marcus is listening for.
```

## What you would do if you did not know

```
**TECH-30 · dont-know · T1**
"How does the layer below the one you work in actually work?"
*Strong answer contains:* an honest boundary stated early, the accurate part of the model up to that boundary, and a specific answer for how to find out. Confident invention scores one.
```

```
**TECH-33 · dont-know · T2**
"I am going to ask you something you probably cannot answer. How does the system decide which of two conflicting writes wins?"
*Strong answer contains:* either a correct answer for a system Alex knows, or a clean stop, a statement of what is known about the problem class, and the question Alex would ask the owner.
```

```
**TECH-35 · dont-know · T3**
"Tell me about a time you were confidently wrong about something technical. How did you find out?"
*Strong answer contains:* the specific belief, the mechanism that exposed it, how fast the update happened in public, and the habit adopted to catch that error class earlier. The timestamp precision assumption on the migration is the honest answer.
```

## Northwind domain

```
**NW-TECH-01 · domain · T2**
"Say our ledger and the bank's record disagree about a single movement of money. Walk me through how you would even start."
*Strong answer contains:* asking what the two records are keyed on before proposing anything, an ownership model for which is authoritative, an explicit statement that the answer is usually neither, and the human path when the automated one gives up. Do not assume this works like idempotency.
```

```
**NW-TECH-02 · domain · T3**
"We pay a sub-merchant out instantly, and then reconciliation finds the underlying transaction never settled. What should the system do?"
*Strong answer contains:* naming that this is a policy question with a technical implementation rather than the reverse, the difference between recovering from the sub-merchant and absorbing the loss, what the system needs to have recorded at payout time to make either possible, and no pretence of knowing Northwind's actual policy.
```

```
**NW-TECH-03 · staff-signal · T2**
"You are applying to a Senior posting and your profile says you are targeting Staff. Talk to me about that."
*Strong answer contains:* a flat, unhedged reason, no sulking, no pretending the question is unfair, and a specific statement of what would make the level question moot. Neither interviewer is the hiring manager, so the only thing being tested is whether Alex sounds settled.
```

---

# Worked answers

*Full scripts for the questions most likely to arrive and most likely to be fumbled. Written in spoken voice.*

## "You need to backfill two years of history into a new schema without taking the live system down. Plan it." (TECH-11, Card 2)

> Let me answer directly and then go one level down. I would dual write first, backfill second, compare third, and only shift reads fourth, and I would spend more calendar time on the comparison than on the backfill.
>
> Dual write means every new record goes to both stores from day one, so the backfill has a fixed end rather than chasing a moving target. Then the backfill runs in chunks with a resumable checkpoint, off the production path, rate limited against the source so it cannot become the incident. Every chunk is idempotent so a restart is safe, which matters because it will restart.
>
> Then the comparison. A job reads both, reports disagreement, and nobody acts on the output for weeks. When I did this at Beacon Pay we compared about 140 million rows over four months of history. The disagreement rate started around 0.4 percent, which was alarming for a day until we found that essentially all of it was a timestamp precision difference. Real disagreements after that were 31 rows, all from a two-minute window where the dual write had a bug.
>
> Rollback is the easy part if you have done the rest, because you have not shifted reads yet. What that cost us was four extra weeks of calendar time, because I extended the comparison from two weeks to six and had to defend that against the roadmap.

**Traps:** do not lead with throughput. Do not describe this as a sequence of steps with no failure branch. Name the timestamp problem, because it is the detail that proves the story is real.

## "What is the worst production incident you have been close to?" (TECH-24, Card 4, NOT BUILT)

> **NEEDS REAL DETAIL.** The material: early 2024, duplicate charges at Beacon Pay, found by a platform customer rather than by our monitoring, running about six hours. Needs written out with detection time, who detected it, what I personally did and when, mitigation separated from durable fix, and the sub-merchant-visible symptom first.
>
> Open question to answer before this card can be written: what was the actual customer-visible symptom, specifically? "Charged twice" is the mechanism. What did the sub-merchant see in their dashboard, and what did the buyer see on their statement? I do not currently know the second one and I should find out before claiming anything.

## "A dependency starts responding in eight seconds instead of eighty milliseconds and never errors." (TECH-26)

> Slow is worse than down, and the reason is that down releases resources and slow holds them.
>
> Concretely: requests to that dependency stop returning, the connection pool fills, and then requests that have nothing to do with that dependency start queueing for a connection they will never get. So a single slow downstream takes out traffic paths that do not touch it, which is what makes it so hard to diagnose from the symptom.
>
> The fixes are a timeout shorter than the caller's patience, a circuit breaker so the fifty first request fails fast instead of waiting, and bulkheading so that dependency has its own pool and cannot starve anything else. And a health signal based on latency rather than on error rate, because error rate looks perfect the whole time this is happening.
>
> I will say directly that I read your February post-mortem and the shape of it looked like this. I would rather say that than pretend I am reasoning from first principles about something I have read.

**Traps:** do not pretend not to have read the post-mortem. Do not assert pool exhaustion as their cause. Describe the mechanism generally, then ask.

## "You are applying to a Senior posting and your profile says Staff." (NW-TECH-03)

> Yes, my profile says that, and it is accurate. I want to keep going on the individual contributor track and I want the scope that comes with it.
>
> I am running this loop at Senior because the work is money movement at a company where money movement is the product, and that is worth more to me than a title at a company where payments is a feature. Your recruiter was straightforward that Senior is a wide band here and that a Staff outcome from this loop is possible and not the default, and I would rather have that conversation with real information on both sides than optimise for the label on the posting.
>
> The thing that would make the question moot is scope. If the work is owning the matching engine and the data model that sits under it, the level takes care of itself in about a year.

**Traps:** no sulking, no hedging, no asking them to reassure me. Neither of these people decides my level. Say it flat and move on.

---

# The remix engine

1. **Mode** sets which tags get weighted and how long the run is.
2. **No repeat:** read the last two run log entries and do not reuse those probe identifiers.
3. **Coverage steering:** bias toward the tags with the lowest count in the tracker.
4. **Difficulty climbs within a run.** Start at tier one, end at tier three. Never flat.

## Mode menu

| Mode | Weights | Length | Feel |
|---|---|---|---|
| Surprise mix | balanced pull across all tags, full arc | 40 to 50 min | realistic all rounder |
| Migration heavy | system-design, data, tradeoffs, verification | 45 to 55 min | the round Ines will actually run |
| Incident heavy | failure-modes, dont-know, operability | 30 to 40 min | the round Marcus will actually run |
| Rapid fire | 12 to 15 short probes, no teaching | 20 to 25 min | trains crispness |
| Curveball | normal arc plus three tier three curves, skeptical mood | 35 to 45 min | composure |
| Deep dive: failure-modes | one tag, escalating tier one to tier three | 25 to 35 min | the known gap |
| Full rehearsal | all tags, real pacing, both interviewers | 55 to 60 min | closest to the real hour |

## Interviewer mood, roll one per run

Warm and curious. Neutral and efficient. Distracted, checking the clock. Skeptical, pushing on every claim. Friendly but running late, wants everything compressed.

## Opening, roll one per run

Straight into a question with no small talk. Ines opens with a system question. Marcus opens with "tell me about the last time you were paged." One of them opens with "what questions do you have for us, let us start there." A comment on the coding exercise neither of them reviewed.

---

# Coverage tracker

| Tag | Times drilled |
|---|---|
| system-design | 3 |
| data | 2 |
| tradeoffs | 2 |
| failure-modes | 3 |
| dont-know | 2 |
| domain | 3 |
| staff-signal | 1 |

**Probes used, by run:** Run 1: TECH-01, TECH-11, TECH-02, TECH-24, TECH-26, NW-TECH-01, TECH-30, TECH-20. Run 2: TECH-05, TECH-06, TECH-25, TECH-22, TECH-28, TECH-35, NW-TECH-02, NW-TECH-03, TECH-33.

---

# Scoring rubric

*Six dimensions, one to five, half points allowed. Dimensions two through five tuned to a technical deep dive. Strong is four or better across the board with no twos on technical depth or risk awareness. Those two are named now, before scores exist.*

| # | Dimension | What a five looks like |
|---|---|---|
| 1 | Structure | Answers the question in the first sentence, then goes one level down deliberately. Clarifies before designing. Does not wander. |
| 2 | Technical depth | Real mechanism, named components, actual numbers. Can go a rung lower when pushed and knows where the rungs run out. |
| 3 | System thinking | Sees the second-order effect: what becomes expensive, what breaks next, who else is affected by a local change. |
| 4 | Risk awareness | States how the change was verified and what would have made it stop. Names the failure branch before the happy path. |
| 5 | Explaining to a non-specialist | Can say what a customer or an operator experienced in words that do not require the architecture. No graph as an answer to a human question. |
| 6 | Communication and presence | Concise, calm, quantified, landed the point, then stopped. Steady when pushed on the weakest claim. |

---

# Rules the bot must follow

1. One question per turn from one interviewer, then stop and wait. No stacking, no two interviewers in one turn. The only exception is when something I said genuinely pulls both lenses, and then say why both are jumping in.
2. One interviewer owns a thread until it resolves, then the other picks up. No ping pong.
3. Randomize who opens and in what order, every run.
4. No hints. Do not tell me which card to use, do not hand me a framework, do not scaffold. I navigate with the cheat sheet alone.
5. Do not grade until the whole run is over.
6. Do not open a reply by telling me an answer was good, strong, sharp, or interesting. Ask the follow-up.
7. Interrupt me if I run long. Once per run, force a compression: "give me that in fifteen seconds."
8. Ignore transcription artifacts. I dictate. Grade substance and intent.
9. At least once per run, push on the weakest thing I said rather than moving on politely. Ines pushes on unverified numbers. Marcus pushes on anything that describes a system without describing a person.
10. At the end: per question, six scores plus exactly two things that worked quoted from what I said plus exactly one fix. Then across the run, three to six cross-cutting patterns, exactly one highest leverage fix overall, and an artifact gap list. Append the run log entry.

---

# Recurring fixes to watch for

| Fix | Status |
|---|---|
| Leads with the outcome number before the mechanism or the verification | CONFIRMED CLOSED after run two, kept in table because a closed fix reopens as an overcorrection |
| Describes a system without ever describing a person | RECURRING, two runs |
| Answers a human question with an internal metric | NEW, run two. The overcorrection from the run one fix. |
| Assumes their event log behaves like the one I know | PARTIAL WIN, caught myself once in run two |

---

# Run log

*Appended by the bot. Newest at the bottom. Full graded detail for both runs is in `Run Log Excerpt.md`.*

```
Run 1, 23 June 2026, realistic, full rehearsal, Ines opened.
Scores: structure 3.5 | depth 3 | system 3.5 | risk 3 | non-specialist 3.5 | communication 3.5
Worked: (1) "slow is worse than down, and the reason is that down releases resources and slow holds them" (2) "I read your February post-mortem and the shape of it looked like this"
Highest leverage fix: on the migration I led with seven times throughput and Ines asked twice how I knew the shard key was right. Put the verification method and the shard key rationale on the card, before the number.
Artifact gap: no shard key rationale anywhere; no verification figures on Card 2; no incident card at all, so TECH-24 was answered from memory; no boundary line on what I did not own in the routing work.
Probes used: TECH-01, TECH-11, TECH-02, TECH-24, TECH-26, NW-TECH-01, TECH-30, TECH-20
```

```
Run 2, 27 June 2026, realistic, full rehearsal, Marcus opened.
Scores: structure 4 | depth 4.5 | system 4 | risk 4.5 | non-specialist 3 | communication 4
Worked: (1) "the seven times is the headline and the 31 rows is the actual result" (2) "I would want to know what your ordering and delivery guarantees actually are before I answer that"
Highest leverage fix: on TECH-28 Marcus asked what the merchant saw during the four hours and I answered with the disagreement rate. Write the customer-visible symptom on every card as one line, and add a discriminator: mechanism when they ask how, symptom when they ask what someone saw.
Artifact gap: still no incident card; no customer-visible symptom line on any card; Triggers table has no row for a question about what a person experienced.
Probes used: TECH-05, TECH-06, TECH-25, TECH-22, TECH-28, TECH-35, NW-TECH-02, NW-TECH-03, TECH-33
```

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

Based on "Super Simulator," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
