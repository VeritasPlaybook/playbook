>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Run Log Excerpt: Alex Rivera, Northwind Payments technical panel

> **Worked illustration.** Alex Rivera, Ines Kowalczyk, Marcus Dube, Northwind Payments, Beacon Pay, and Lumen Streams are fictional. Every number is illustrative. The answers below are written the way a person actually talks when dictating, false starts included, because a cleaned-up transcript would hide the exact failures the system exists to find.

**What this file is.** Two full rehearsals, four days apart, with the version bump in between. The pattern to watch: run one finds a specific hole in an artifact, the hole gets fixed, run two is markedly better on the fixed dimension and half a point worse on a dimension nobody touched. The second part is not coincidence or bad luck. It is what concentrated practice does, and the repair is different from the repair for the original problem.

**What this file is not.** A flattering demo. Run one scores a three on the round's least forgiving dimension. The largest gap identified in run one is still only half closed the night before the round.

---

# Run 1

**Date:** 23 June 2026
**Mode:** realistic, full rehearsal, 55 minutes. Ines opened. Mood rolled: neutral and efficient.
**Probes used:** TECH-01, TECH-11, TECH-02, TECH-24, TECH-26, NW-TECH-01, TECH-30, TECH-20
**Artifacts in play:** Cheat Sheet v1, Story Bank cards 1, 2, 3

---

## Exchange 1

**Ines:** You need to backfill two years of history into a new schema without taking the live system down. Plan it.

**Alex:** Okay. So I did close to exactly this at my current company. We moved from a single database instance to a sharded cluster and we hit about a seven times throughput improvement with zero customer-facing downtime over a four month rollout.

The way you do it is you dual write first, so every new record goes to both stores, which means the backfill has a fixed end rather than chasing a moving target. Then you backfill in chunks with a checkpoint so it can resume, and you rate limit it against the source so it does not become the incident. Then you shift reads over gradually, a percentage at a time, and then you retire the old store.

**Ines:** How did you know the shard key was right?

**Alex:** We looked at our query patterns. Most of our reads were merchant scoped, so we sharded on merchant identifier, which keeps those queries on a single node.

**Ines:** How did you know that. Specifically.

**Alex:** I mean, we knew our access patterns from, honestly, from experience with the system. It was fairly clear that merchant was the dimension.

**Ines:** Right.

---

## Exchange 2

**Marcus:** What is the worst production incident you have been close to?

**Alex:** So there was a duplicate charge problem at Beacon Pay in early 2024. Clients were retrying after a lost response and we were charging cards twice. That is actually what motivated the idempotency work I did afterwards, which brought duplicate charge incidents down about 95 percent year over year.

**Marcus:** Before the fix. The incident itself. What happened, and when did you know?

**Alex:** It ran for a while before we caught it. I want to say most of a day. We saw it in the duplicate reports coming through support.

**Marcus:** Who told you first?

**Alex:** It came through support, so, a customer, effectively.

**Marcus:** What did you do?

**Alex:** I was one of the people who worked on the fix afterwards. During the incident itself I was, I think I was mostly helping identify the affected transactions.

---

## Exchange 3

**Marcus:** A dependency starts responding in eight seconds instead of eighty milliseconds and never errors. What happens to your system?

**Alex:** Slow is worse than down, and the reason is that down releases resources and slow holds them.

Concretely, requests to that dependency stop returning, the connection pool fills up, and then requests that have nothing to do with that dependency start queueing for a connection they are never going to get. So one slow downstream takes out traffic paths that never touch it, and that is what makes it so hard to diagnose, because the symptom appears somewhere unrelated to the cause.

The fixes are a timeout that is shorter than the caller's patience, a circuit breaker so the fifty first request fails fast instead of waiting, and bulkheading so that dependency has its own pool and cannot starve everything else. And your health signal has to be latency based, not error rate based, because error rate looks perfect the entire time this is happening.

I will say directly that I read your February post-mortem and the shape of it looked like this. I would rather say that than pretend I am reasoning about it fresh.

**Marcus:** What would you have added to our system to catch it earlier?

**Alex:** A latency-based alert on that dependency specifically, and a saturation metric on the connection pool, which is the thing that actually runs out. Pool utilisation over some threshold is a much earlier signal than anything at the request layer.

---

## Exchange 4

**Ines:** Say our ledger and the bank's record disagree about a single movement of money. Walk me through how you would even start.

**Alex:** Right, so this is adjacent to work I have done rather than work I have done. Let me say what I would want to know first.

I would want to know what the two records are keyed on, because everything depends on that. If there is a shared identifier that both sides carry, this is a lookup problem with some edge cases. If there is not, and you are matching on amount and timestamp and some counterparty reference, then it is a fuzzy matching problem and it is a completely different system.

Then I would want to know which side is authoritative, and my guess is that the honest answer is neither, that the bank is authoritative about whether money moved and you are authoritative about what it was for.

**Ines:** And when the automated match gives up?

**Alex:** Then it goes to a person, and the thing I would care about is what that person gets handed. The queue entry needs enough context that they are not doing an investigation from scratch every time.

**Ines:** Have you built one of those?

**Alex:** No. I have built matching logic that either succeeded or retried. I have never built one where a human is the fallback.

---

## Run 1 grading

**Scores**

| Dimension | Score |
|---|---|
| Structure | 3.5 |
| Technical depth | 3 |
| System thinking | 3.5 |
| Risk awareness | 3 |
| Explaining to a non-specialist | 3.5 |
| Communication and presence | 3.5 |

Technical depth and risk awareness are the two dimensions this round cannot forgive, per the rubric, and both are at three. That is a no-hire simulation and the debrief should say so plainly.

**Two things that worked**

1. You said: *"slow is worse than down, and the reason is that down releases resources and slow holds them."* That is the whole failure mode in fourteen words, delivered first, and then you went down a level. It is the best-structured answer of the run and the shape every other answer should have.
2. You said: *"I read your February post-mortem and the shape of it looked like this. I would rather say that than pretend I am reasoning about it fresh."* Marcus is a former site reliability engineer and this is the move that wins him. You also stopped there rather than asserting their cause, which the Do not assert list told you to do and which you did.

**One highest leverage fix**

On the migration you opened with *"we hit about a seven times throughput improvement with zero customer-facing downtime."* Ines then asked how you knew the shard key was right, twice, and your second answer was *"we knew our access patterns from, honestly, from experience with the system."* That is the moment the round would have been decided.

You have the real answer. A week of production query logs classified by what they filtered on, about 80 percent filtering by merchant, then per-shard load watched for two months after cutover, confirming both the distribution and the two hot merchants you had predicted. None of that was on the card, so under pressure you produced the vibe version of an analysis you actually did.

The fix, concretely: rewrite the opening of Card 2 so the verification comes before the number, and add a shard key block with the key chosen, the two rejected candidates, and the reason for each. Do this before the next run.

**Artifact gap list**

1. **Card 2, no shard key rationale.** The single most likely follow-up from a Staff Engineer who came up through databases, and there was nothing on the card.
2. **Card 2, no verification figures.** The 140 million rows, the 0.4 percent, the 31 real disagreements. All real, none written down, so none of them arrived.
3. **No incident card.** TECH-24 was answered from memory and it showed. You produced *"it ran for a while before we caught it. I want to say most of a day"* and *"I think I was mostly helping identify the affected transactions." "I think I was mostly"* is not an answer to a former site reliability engineer, and the underlying facts are better than that sentence.
4. **No boundary line for the migration.** You said "we" throughout and never named that the data platform group operated the cluster. Ines did not push on it this time. She will.

---

# Version bump between runs

**24 June 2026. Cheat Sheet v1 to v2.** Version one kept, not edited. Four changes, all traceable to the list above.

| Change | Which gap it closes |
|---|---|
| Story 2 headline rewritten. Was "seven times throughput, zero downtime." Now "the part that took the longest was proving the new path agreed with the old one on four months of history." | Gap 2, and the highest leverage fix |
| New beat on Story 2: shard key chosen, two candidates rejected, one line each. | Gap 1 |
| Verification figures added to the Numbers tab: 140 million rows, 0.4 percent then 31, and the note that 31 is the number to defend. | Gap 2 |
| Boundary line added to Story 2: I did not operate the cluster, the data platform group did. | Gap 4 |

**Story Bank Card 2** was promoted to version 2 with the same material plus the full three-candidate shard key analysis.

**Not done:** the incident card. Logged as the top gap, deferred, and this is the decision the rest of this file is about.

---

# Run 2

**Date:** 27 June 2026
**Mode:** realistic, full rehearsal, 58 minutes. Marcus opened. Mood rolled: skeptical, pushing on every claim. Designed experiment: roughly 70 percent testing whether the v2 sheet holds, 30 percent new ground.
**Probes used:** TECH-05, TECH-06, TECH-25, TECH-22, TECH-28, TECH-35, NW-TECH-02, NW-TECH-03, TECH-33
**Artifacts in play:** Cheat Sheet v2, Story Bank cards 1, 2 v2, 3

---

## Exchange 1

**Ines:** You need to change a data format that three downstream consumers depend on and you cannot coordinate a simultaneous release. Sequence it.

**Alex:** Additive first, and never remove anything until you can prove nobody is reading it.

So: add the new field alongside the old one, write both. Consumers migrate on their own schedule because nothing they depend on has changed. Then you need a way to know when they have actually migrated, and this is the step people skip, because "we told them to" is not evidence. I would instrument reads on the old field, per consumer, and only stop writing it when that count has been zero for longer than the longest deployment cycle any of them has.

Then cleanup, which is the step people skip twice. The old field sits there for a year and becomes something the next person has to reason about.

**Ines:** How long is "longer than the longest deployment cycle"?

**Alex:** For us it would have been about three weeks, because one team deployed monthly. I would take the slowest consumer's cadence and double it. And I would rather be wrong in the direction of leaving a dead field in place for an extra month than in the direction of a silent read failure in a system that moves money.

**Ines:** You said "prove nobody is reading it." What if the consumer is a batch job that runs quarterly?

**Alex:** Then reads-are-zero tells you nothing for three months and I would have to wait a full cycle plus margin, or find the job and ask its owner directly. That is the case where instrumentation does not save you and a conversation does. I would want a register of consumers that includes cadence, not just names, and I have never actually seen one of those maintained properly.

---

## Exchange 2

**Ines:** Tell me about a time you were confidently wrong about something technical. How did you find out?

**Alex:** The migration comparison, and it is a good example because I was wrong about the category of problem rather than about a detail.

Going in, I had enumerated the ways the two stores could disagree: schema differences, dual write failures, ordering. What I had not considered was that both stores could be technically correct and represent the same value differently. We started the comparison and the disagreement rate came back at about 0.4 percent, which for about a day I believed meant we had a real correctness problem.

It was a timestamp precision difference. One column stored at a different resolution on the new side. Once we fixed that, the real disagreements were 31 rows, all from a two-minute window in week one where the dual write had a bug.

What I do now is enumerate every column whose representation could differ across the two systems before I write the comparison job, and report on those separately so they do not bury the rate.

**Ines:** So how much of the seven times do you actually stand behind?

**Alex:** The seven times is write throughput on a load test built from production-shaped traffic, plus the peak we observed after cutover. It is not a claim that everything got faster. Merchant-scoped reads improved modestly. Anything that scatters across shards got worse, and we have two report queries that are meaningfully slower now than they were before.

The seven times is the headline and the 31 rows is the actual result.

---

## Exchange 3

**Marcus:** Design the rollback for a change that is already half deployed and has written bad data.

**Alex:** Stop the bleeding, then repair, and never do them in the same step.

Stopping the bleeding is halting the deploy and rolling the code back on the instances that have it, which stops new bad rows. That is fast and it is not the hard part. The hard part is that the code rollback does nothing about the rows already written, and the instinct to fix both at once is how you end up with a repair job running against a version of the code you are also changing.

Then you identify the affected records, which is only possible if you can bound them: a time window plus the instances that had the bad version. Then the repair itself has to be idempotent, because it will get run twice, either because someone reruns it or because it fails partway.

Then verification, and I would compare the repaired rows against an independent source rather than against my own repair job's own report, because a repair job that is wrong will happily tell you it succeeded.

**Marcus:** During those four hours, what did the merchant see?

**Alex:** So in our case the disagreement rate on the comparison job was showing about, well, we were seeing rows that did not match on the reconciled side, and the volume of that was what told us the scope.

**Marcus:** That is what you saw. What did the merchant see?

**Alex:** Right. Their balance would have been wrong. I think the settlement figure in their dashboard would have been off for that period.

**Marcus:** You think.

**Alex:** I do not know precisely. I know what our systems showed. I would have to check what the merchant-facing number actually was during that window.

---

## Exchange 4

**Marcus:** You are applying to a Senior posting and your profile says you are targeting Staff. Talk to me about that.

**Alex:** Yes, my profile says that, and it is accurate. I want to stay on the individual contributor track and I want the scope that comes with it.

I am running this loop at Senior because the work is money movement at a company where money movement is the product, and that is worth more to me than a title at a company where payments is a feature. Your recruiter was straightforward that Senior is a wide band here and a Staff outcome from this loop is possible and not the default. I would rather have that conversation with real information on both sides than optimise for the label on the posting.

The thing that would make the question moot is scope. If the work is owning the matching engine and the data model under it, the level takes care of itself in about a year.

**Marcus:** And if it does not?

**Alex:** Then I would want to know that at the twelve month mark rather than at the twenty four, and I would ask. I do not think that is a dramatic conversation.

---

## Run 2 grading

**Scores**

| Dimension | Run 1 | Run 2 | Movement |
|---|---|---|---|
| Structure | 3.5 | 4 | up 0.5 |
| Technical depth | 3 | 4.5 | up 1.5 |
| System thinking | 3.5 | 4 | up 0.5 |
| Risk awareness | 3 | 4.5 | up 1.5 |
| Explaining to a non-specialist | 3.5 | 3 | **down 0.5** |
| Communication and presence | 3.5 | 4 | up 0.5 |

Both unforgiving dimensions moved 1.5 points and cleared the bar. The version two cheat sheet did exactly what it was edited to do. And a dimension nobody was working on went down, on a question type that had not come up before, the signature of an overcorrection rather than a new weakness.

**Two things that worked**

1. You said: *"the seven times is the headline and the 31 rows is the actual result."* That is the whole run one fix compressed into one sentence, offered unprompted, in front of the person whose public work is about exactly that. Compare it with run one's *"we knew our access patterns from, honestly, from experience with the system."* Same underlying knowledge, entirely different outcome, and the only change is that it is now written down.
2. You said: *"that is the case where instrumentation does not save you and a conversation does. I would want a register of consumers that includes cadence, not just names, and I have never actually seen one of those maintained properly."* You answered a hypothetical, found the limit of your own answer, and named a real-world reason the clean solution fails. Ines pushed and you went down rather than sideways.

**One highest leverage fix**

On TECH-28, Marcus asked what the merchant saw during the four hours and you answered with *"the disagreement rate on the comparison job was showing about, well, we were seeing rows that did not match."* He asked again and you got to *"their balance would have been wrong. I think the settlement figure in their dashboard would have been off."*

Read naively this is a knowledge gap and the naive repair is to learn more about merchant-facing surfaces. That is the wrong medicine. The pattern says otherwise: you were drilled for four days on mechanism-and-verification-first, executed it beautifully on every question that asked how something worked, and then it fired on a question that asked what a person experienced. That is a drilled behaviour escaping its context.

The repair is a discriminator, not more drilling. One line, written on the cheat sheet: *mechanism when they ask how it works, symptom when they ask what someone saw.* One line, one card, one rep to install. Then add a customer-visible symptom line to each of the three story cards, which is three sentences and forces you to know the answer.

**Artifact gap list**

1. **Still no incident card.** Identified in run one, deferred, and now the reason two separate probes went badly across two runs. The most expensive open item in the folder.
2. **No customer-visible symptom line on any card.** Three cards, three missing sentences. Cheapest fix available and it closes the run two failure directly.
3. **Triggers table has no row for "what did the customer see" or "what did a user experience."** You had no route from the question to the right material, so you took the material you were holding.
4. **Card 2 shard key block worked.** Recording a closed gap rather than dropping it silently, because a closed gap can reopen as an overcorrection and a log that only records failures cannot show that.

**Cross-cutting patterns**

- Everything written down came out level. Everything improvised came out with hedges and a rising inflection. That gap widened rather than narrowed between runs, which is an argument for writing down more, not for practising more.
- Ines-shaped questions are now consistently four or better. Marcus-shaped questions are consistently three to three and a half. The split is not about difficulty, it is about which card exists.
- The pattern from run one, describing a system without describing a person, is now RECURRING across two runs and is the parent of the new failure. Fix the parent and the child closes.
- You caught the event log assumption yourself in run two, unprompted, which is a partial win worth naming so it does not get read as still open.

---

# What happened next

The discriminator was written the same evening, because it was one line: *mechanism when they ask how it works, symptom when they ask what someone saw.* It went on the Landmines tab in version 2.1, along with a Triggers row and three customer-visible symptom lines, one per card.

Card 4, the incident card, was half built on 30 June. The spine, the detection time, and who found it are written. One field is deliberately blank: what the cardholder saw on a statement during the incident. That fact was not recoverable in the time available, and the decision recorded in `_STATE.md` was to leave it blank and say the boundary out loud rather than invent something in front of a payments panel.

The stopping rule then applied. The card read pass on the evening of 1 July produced no new artifact gap and no new fix, so there was no third run. See `Round Debrief.md` for what the panel actually asked, and for the one question that made the half-built card matter more than either run predicted.

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

Based on "Run Log Excerpt," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
