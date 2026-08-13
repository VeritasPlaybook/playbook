>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Card 2: Sharded migration

**Owns:** migrating a live financial data store, verification, staged rollout
**Tags:** `#migration` `#data` `#verification` `#risk`
**Source:** Career Brain Trust, `Experience/3.1 Beacon Pay.md`, PostgreSQL to sharded cluster bullet
**Status:** drilled 2 times. Version 2 of this card, updated 24 June 2026 after mock run one.
**Numbers last verified:** 16 June 2026, verification figures added 24 June 2026

> **Worked illustration.** Fictional person, fictional employer, illustrative numbers.

---

## Headline, say this first, then stop

> I led the migration of our transaction store from a single PostgreSQL instance to a sharded cluster, and the part that took the longest was proving the new path agreed with the old one on four months of history before we let it serve anything.

*Changed in version 2. Version 1 opened with "we hit a seven times throughput improvement with zero customer-facing downtime," which is the number, and the number is not what this panel screens for. See the run log for what happened when I led with it.*

---

## The two minute spoken version

At Beacon Pay the transaction store was a single PostgreSQL instance and the thing that was going to break first. We were at roughly four million transactions a day and the write path was the constraint. The plan was to shard it using a PostgreSQL extension for distributed tables.

The interesting decision was the shard key, and I want to start there because it determines everything downstream. We had three candidates. Transaction identifier gives perfect distribution and makes every merchant-level query a scatter-gather across every node, which is most of our read traffic, so that was out. Date range gives clean archival and a permanently hot last shard, a slow-motion version of the problem we were trying to solve. We sharded by merchant identifier. That gives merchant-level queries on one node, the read pattern that matters, and accepts a real cost: a merchant with unusual volume produces a hot shard, and we had two. We isolated those two onto dedicated shards, an ugly special case that is still there.

The rollout was four phases over four months. Dual write to both stores while reading only from the old one. Then a comparison period where a job read both and reported disagreements without anyone acting on them. Then reads shifted a percentage at a time. Then the old instance was retired.

The comparison period is the part I would spend the most time on. We compared about 140 million rows across four months of history. The disagreement rate started at roughly 0.4 percent, alarming for about a day, until we found essentially all of it was a timestamp precision difference in one column we were storing at a different resolution on the new side. Real disagreements after that fix were 31 rows, all transactions written during a two-minute window in the first week when the dual write had a bug. We fixed those by hand and I have the list.

Throughput ended up about seven times better with no customer-facing downtime window. But the number I would defend under scrutiny is 31 rows, not seven times.

---

## The spine, five beats

1. Single PostgreSQL instance at about four million transactions a day, write path was the constraint.
2. Shard key was the decision. Transaction identifier scatters our main read pattern, date range gives a permanently hot last shard, merchant identifier wins and costs us two hot merchants we isolated by hand.
3. Four phases over four months: dual write, comparison period, staged read shift, retire the old instance.
4. Comparison period on about 140 million rows over four months of history. Disagreement started at 0.4 percent, almost all of it a timestamp precision difference. Real disagreements were 31 rows from one two-minute dual-write bug.
5. About seven times throughput, no customer-facing downtime. The 31 rows is the number worth trusting.

---

## The line that ends it

> The seven times is the headline and the 31 rows is the actual result, because a migration you cannot prove is a migration you have not finished.

---

## The decisions I owned

- **Decision:** shard by merchant identifier. **Alternatives considered:** transaction identifier, rejected because it scatters our dominant read pattern across every node. Date range, rejected because it produces a permanently hot last shard. **What it cost:** two high-volume merchants produce hot shards. We isolated them onto dedicated shards, a special case still in the system that still needs a human to notice when a third merchant crosses the line.
- **Decision:** run the comparison period for six weeks reporting only, with nobody acting on the output, before shifting any reads. **Alternative considered:** a two week comparison, which the original plan had and the schedule wanted. **What it cost:** four weeks of calendar time and an uncomfortable conversation about the roadmap. It also caught the two-minute dual-write bug, so the argument made itself afterward.
- **Decision:** fix the 31 affected rows by hand rather than writing a repair job. **Alternative considered:** a general repair tool, which we would have kept. **What it cost:** roughly a day of my time and no reusable tooling, which was wrong if a second occurrence had ever happened. It did not, so I got away with it rather than being right.

---

## Numbers I can defend

| Metric | Before | After | How I know | Verified |
|---|---|---|---|---|
| Rows compared in the verification period | n/a | about 140 million, over 4 months of history | Comparison job output | 24 Jun 2026 |
| Disagreement rate at start of comparison | n/a | about 0.4 percent, almost all timestamp precision | Comparison job output | 24 Jun 2026 |
| Real disagreements after the precision fix | n/a | 31 rows, all from one two-minute window | Comparison job output, list retained | 24 Jun 2026 |
| Write throughput | baseline | about 7 times | Load test on production-shaped data, plus observed peak after cutover | 16 Jun 2026 |
| Customer-facing downtime | n/a | none scheduled, none observed | Status page and incident tracker for the rollout period | 16 Jun 2026 |
| Rollout duration | n/a | 4 phases, 4 months | Project record | 16 Jun 2026 |

**Verification line:** the comparison period is the verification. Dual write, read both, report disagreement, act on nothing for six weeks.

---

## Who did what

- **Me:** the shard key analysis and decision, the phase plan, the comparison job design, and the argument for extending the comparison period from two weeks to six. I wrote the Request-for-Comments document.
- **My team:** two engineers built the dual write path and the read shifting mechanism. One of them found the timestamp precision difference, which I had not anticipated.
- **Other functions:** our data platform group ran the cluster itself. I did not operate the shards and I would not claim to.

---

## Honest boundary

> I owned the shard key decision, the phasing, and the verification design. I did not operate the cluster, that was our data platform group, so if you ask about rebalancing behaviour under node failure I can tell you what we planned for and not what actually happens, because it did not happen to us.

---

## Likely follow ups

**"How did you know the shard key was right?"**
Two ways, one before and one after. Before: I took a week of production query logs and classified them by what they filtered on. About 80 percent filtered by merchant, which made merchant identifier the candidate rather than a guess. After: I watched per-shard load for the two months following cutover, and the distribution was acceptable except for the two merchants we had predicted would be hot. So the analysis predicted the outcome, including the ugly part.

**"What would have made you reverse it?"**
If the comparison period had produced a disagreement class I could not explain. The 0.4 percent was fine once we understood it, and the point of six weeks of reporting-only is that an unexplained pattern buys a stop rather than an investigation on a deadline. Concretely, with unexplained disagreements still at week four I would have gone back to the phase plan rather than shifting any reads.

**"Seven times sounds like a lot. What is the honest version?"**
Seven times on write throughput on a load test built from production-shaped traffic, plus the observed peak we hit afterward. It is not a claim that everything got seven times faster. Read latency for merchant-scoped queries improved modestly. Anything that scatters got worse, and two report queries are meaningfully slower than they were.

---

## Reflection

I underestimated the timestamp precision problem class entirely. I had thought about schema differences and the dual write failing, and not about the two stores being technically correct and representing the same value differently. What I now do at the start of any migration is enumerate every column whose representation could differ across the two systems, before writing the comparison job, so it reports those separately rather than burying them in a single disagreement rate.

---

## Variant framings

**For a question about a technical decision under pushback:** open on the shard key and the three candidates, and name the hot shard cost before being asked. *Use when:* the interviewer came up through databases and will go straight there.

**For a question about risk:** open on extending the comparison period from two weeks to six and the roadmap conversation that cost. *Use when:* the question is about how you decide something is safe rather than about how you built it.

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

Based on "Story Bank Card Template," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
