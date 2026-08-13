>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# _STATE: Northwind Payments, technical panel

**Purpose:** Anchor for this round. Every new thread reads this file first, then the file it needs. Every thread updates this file before it closes.
**Round date:** Thursday 2 July 2026, 1:00 in the afternoon Pacific
**Last updated:** 1 July 2026, evening. Card 4 half built. Cheat sheet at version 2.1. Card read pass done.

> **Worked illustration.** Fictional candidate, fictional company, fictional interviewers, illustrative numbers.

---

## >>> WHERE THIS IS: Two full rehearsals run, cheat sheet at v2.1, card read pass done tonight. Card 4, the incident card, is HALF built: the spine and the detection facts are written, the customer-visible symptom for the buyer side is still unknown and could not be verified in time. Do NOT run a third mock. Do NOT invent the missing symptom. If asked, say what is known and stop.

---

# The round

| Field | What I know | Confirmed? |
|---|---|---|
| Who is in the room | Ines Kowalczyk, Staff Engineer, Money Movement. Marcus Dube, Engineering Manager, Authorization and Risk Platform. Both present for the full hour. | recruiter confirmed |
| Format | Live video, no live coding | recruiter confirmed |
| Length | 60 minutes | recruiter confirmed |
| What the recruiter called it | "Technical panel, systems and how you work under failure" | verbatim |
| What it assesses | Recruiter said "no coding, they want to hear how you think about systems that hold money" | verbatim |
| Where it sits in the loop | Third of four. Recruiter screen and a coding exercise done. After this: a hiring manager conversation. | recruiter confirmed |
| Anything to prepare or bring | Nothing requested. No slides, no diagram tool named, so assume talking rather than drawing. | confirmed |

**What I am most afraid they will ask:** "What is the worst production incident you have been close to." Marcus will ask it. The honest answer is one that a customer found before we did, it ran about six hours, and I have never told it out loud to anyone outside the company.

---

# Locked decisions (do not re-litigate)

| # | Decision | Locked on |
|---|---|---|
| 1 | Card 2 opens with the verification, never with the seven times figure. Locked after run one. | 23 Jun 2026 |
| 2 | Acknowledge having read the February post-mortem rather than pretending to reason from first principles. | 21 Jun 2026 |
| 3 | Do not assume their event log behaves like the broker I know. Ask about ordering and delivery guarantees first, every time. | 23 Jun 2026 |
| 4 | The Staff versus Senior question gets a flat two-sentence answer and then I move on. Neither interviewer decides my level. | 21 Jun 2026 |
| 5 | Say "agreement" rather than "reconciliation match." It is their word and it costs nothing. | 21 Jun 2026 |

---

# Accuracy guards (carry these forward)

- The 95 percent duplicate reduction belongs to Beacon Pay. The 38 percent tail latency reduction belongs to Lumen Streams. Two different projects, two different companies, and I crossed them once in run one.
- The seven times figure is write throughput on a load test built from production-shaped traffic, not a claim that everything got seven times faster. Read latency for scattered queries got worse.
- The six engineering weeks a quarter is an estimate, not a tracked metric. Say the word estimate before being asked.
- I did not operate the sharded cluster. The data platform group did. Do not let "I led the migration" drift into "I ran the cluster."
- I did not build or operate the service mesh. I made the case for it and migrated four services.
- Platform partner is the paying customer. Sub-merchant is the end business. Two different parties.

---

# Do not assert

*Short version, copied forward from the Company and Role Brief.*

- That their event log is Apache Kafka or behaves like it. Say instead: "I would want to know what your ordering and delivery guarantees actually are before I answer that. What I have worked with is a partition-aware consumer model with offset checkpointing."
- That the February 2026 degradation was connection pool exhaustion. Say instead: "The shape of it, a dependency that got slow and never errored, is the failure mode I find most dangerous. Is that roughly what happened?"
- That Ines still owns the Ledger data model, or that the batch window migration is finished. Say instead: "I may have this out of date, but is the data model still on your side of the line? And is the move off the batch window done, or still in flight?"

---

# Story coverage

| Card | What it proves | Drilled | Status |
|---|---|---|---|
| 1 | Correctness under distributed failure, interface design, blast radius | 2 | drilled |
| 2 | Migrating a live financial store, verification, staged rollout | 2 | drilled, version 2 after run one with shard key rationale and comparison figures |
| 3 | Operability, choosing the measure, cross-team change | 1 | drafted, said out loud once |
| 4 | Detection, mitigation versus durable fix, customer-visible symptom | 0 | **half built.** Spine and detection facts written 30 Jun. Buyer-side symptom unverified and left blank. |

**Coverage gaps:** the buyer-visible symptom of the 2024 duplicate charge incident. I know what the sub-merchant saw in their dashboard. I do not know what the cardholder saw on a statement, and I am not guessing it in front of a payments panel. The plan is to say that boundary out loud if it comes up, a worse answer than knowing and a much better answer than inventing.

---

# Question bank coverage

| Tag | Times drilled |
|---|---|
| system-design | 3 |
| data | 2 |
| tradeoffs | 2 |
| failure-modes | 3 |
| dont-know | 2 |
| domain | 3 |
| staff-signal | 1 |

**Least drilled, steer the next run here:** staff-signal, data. Not being drilled: the stopping rule applies. Two full rehearsals, and the card read pass tonight produced no new artifact gap.

---

# Recurring fixes

| Fix | Status | First seen |
|---|---|---|
| Leads with the outcome number before the mechanism or the verification | CONFIRMED CLOSED, run two gave it four genuine opportunities | 23 Jun 2026 |
| Describes a system without ever describing a person | RECURRING, two runs | 23 Jun 2026 |
| Answers a human question with an internal metric | NEW, the overcorrection produced by fixing the first row. Discriminator written to the cheat sheet. | 27 Jun 2026 |
| Assumes their event log behaves like the one I know | PARTIAL WIN, caught it once unprompted in run two | 23 Jun 2026 |

---

# Artifact versions

| Artifact | Version | What changed and why |
|---|---|---|
| Cheat Sheet | v1 | Initial build, 21 Jun 2026 |
| Cheat Sheet | v2 | 24 Jun 2026, after run one. Story 2 rewritten to lead with the verification. Shard key rationale added as a beat. Comparison figures added to the Numbers tab. Boundary line added for the routing work. |
| Cheat Sheet | v2.1 | 28 Jun 2026, after run two. One discriminator on the Landmines tab: mechanism when they ask how, symptom when they ask what someone saw. New Triggers row for questions about what a person experienced. |
| Story Bank Card 2 | v2 | 24 Jun 2026, shard key block and verification figures |
| Story Bank Card 4 | v0.5 | 30 Jun 2026, spine and detection facts only, symptom left blank on purpose |

*Version one was kept. Never edit it, copy it forward, so you can see which run caused which change.*

---

# Files in this folder

| File | What it is | Status |
|---|---|---|
| `README.md` | Orientation for a reader of this example | done |
| `Company and Role Brief.md` | Company, role, and the do-not-assert list | done |
| `Interviewer Dossier.md` | Ines Kowalczyk and Marcus Dube, one file, sections kept separate | done |
| `Story Bank/INDEX.md` | Routing file, three cards plus one half-built | done |
| `Simulator.md` | Super Simulator: engine, two personas, 20 probes, worked answers, run log | done |
| `Kickoff Prompt.md` | Paste into a fresh thread | done |
| `Run Log Excerpt.md` | Both graded runs with verbatim exchanges | done |
| `Cheat Sheet.html` | v2.1, the only thing open during the call | done |
| `Round Debrief.md` | Filled in the evening of 2 July | done |

---

# What the next thread should do

1. Read this file in full.
2. Do not run another mock. The card read pass on 1 July produced no new artifact gap and no new fix.
3. Do not attempt to finish Card 4 by inference. The missing field is a fact, not a writing problem.
4. Open `Cheat Sheet.html` twenty minutes before the call and read the Landmines tab last.
5. Fill in `Round Debrief.md` the same evening.
6. Update this file before closing.

---

# Standing preferences

- One question per turn during a mock, then stop and wait.
- No hints. Do not tell me which card to use.
- Grade at the end of the run, not after each answer.
- I dictate. Assume garbled or misplaced words are transcription artifacts. Grade substance and intent.
- No em dashes in anything written for me.
- Do not produce drafts or take actions I did not ask for. Grading and appending to the run log at the end of a mock are pre-authorised.

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

Based on "_STATE," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
