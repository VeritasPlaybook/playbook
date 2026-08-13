>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Card 3: Service mesh cutover

**Owns:** operability, choosing the right measure and defending it, cross-team change
**Tags:** `#operability` `#latency` `#crossteam` `#toil`
**Source:** Career Brain Trust, `Experience/3.2 Lumen Streams.md`, service mesh migration bullet
**Status:** drilled 1 time
**Numbers last verified:** 16 June 2026

> **Worked illustration.** Fictional person, fictional employer, illustrative numbers.

---

## Headline, say this first, then stop

> I moved our services off bare metal onto a containerised service mesh, and the argument I had to win first was that we should optimise the tail latency rather than the average.

---

## The two minute spoken version

At Lumen Streams we ran remote procedure call services on bare metal. Every team had its own approach to retries, timeouts, and certificates, so every outage investigation started with finding out which convention that service had adopted.

The proposal was to move onto a containerised service mesh so retries, timeouts, and mutual authentication became configuration rather than code. Standard platform work. What made it a real decision was the metric we committed to.

The average latency across our services was fine and had been for a year, so on average numbers there was no case for the migration. What was not fine was the 99th percentile, roughly three times the median and where all our customer complaints lived. I argued we should commit to a 99th percentile target and accept that the average might get slightly worse, because a mesh adds a hop and a hop is not free. That is uncomfortable to propose, because the average is the number leadership already had on a dashboard and I was asking them to watch a different one.

We migrated fourteen services over about five months, one team at a time, each team keeping the old path available for two weeks after cutover. The 99th percentile came down roughly 38 percent. The median got about four percent worse, exactly the trade I had said we would make and one I am glad I put in writing beforehand, because otherwise it would have been a surprise and surprises get relitigated.

The second result was the one nobody asked for. Because retries and timeouts stopped being per-service code, incident investigation stopped starting with archaeology. I estimated we freed about six engineering weeks a quarter of operational work across the group. That is the softest number on this card and I say so.

---

## The spine, five beats

1. Services on bare metal, every team with its own retry, timeout, and certificate conventions. Every investigation started with archaeology.
2. The average latency was fine and had been for a year. On the average there was no case for the migration.
3. I argued for committing to the 99th percentile and accepting a worse median, in writing, before starting.
4. Fourteen services over about five months, one team at a time, old path kept live for two weeks after each cutover.
5. Tail down about 38 percent, median about 4 percent worse as predicted, and roughly six engineering weeks a quarter of toil removed. The toil number is an estimate and I say so.

---

## The line that ends it

> Picking the metric was the whole decision, because once we were measuring the tail the migration argued for itself, and while we were measuring the average it never would have.

---

## The decisions I owned

- **Decision:** commit to a 99th percentile target and state in writing that the median would likely get worse. **Alternative considered:** commit to the average, already on the dashboard and an easier sell. **What it cost:** a harder initial approval and a real risk that if the tail had not improved I would have had nothing to show and a worse median.
- **Decision:** migrate one team at a time with a two week dual path, rather than a coordinated cutover. **Alternative considered:** a single flag day, which the platform team preferred as much less work to support. **What it cost:** about two extra months of calendar time and the burden of running both paths for most of the migration.
- **Decision:** publish the toil estimate as an estimate rather than dropping it. **Alternative considered:** leaving it out because I could not measure it properly. **What it cost:** credibility risk if somebody had pushed on the method, which is why I always attach the word estimate to it.

---

## Numbers I can defend

| Metric | Before | After | How I know | Verified |
|---|---|---|---|---|
| 99th percentile latency | baseline | about 38 percent lower | Service dashboards, same measurement window before and after, per service and aggregated | 16 Jun 2026 |
| Median latency | baseline | about 4 percent worse | Same dashboards. Predicted in advance and stated in writing. | 16 Jun 2026 |
| Services migrated | 0 | 14, over about 5 months | Migration tracker | 16 Jun 2026 |
| Operational toil removed | n/a | about 6 engineering weeks per quarter | **Estimate.** Built from incident time logs before and after, across the group. Not a tracked metric and I say so unprompted. | 16 Jun 2026 |

**Verification line:** each service kept its old path live for two weeks post-cutover with traffic split, so we compared the two paths on real traffic rather than comparing a before-window to an after-window.

---

## Who did what

- **Me:** the metric argument, the phased plan, and the migration of the four services my team owned. I wrote the proposal and defended it.
- **My team:** two engineers did most of the per-service configuration work.
- **Other functions:** the platform team owned and operated the mesh. I was a consumer and an advocate, not its owner, and I want to be precise about that because it is the kind of thing that gets inflated.

---

## Honest boundary

> I did not build or operate the mesh. I made the case for it, chose the metric we would be judged on, and migrated the services my team owned. If you ask about the control plane's behaviour under partition, I would be telling you what I read rather than what I saw.

---

## Likely follow ups

**"Why is the 99th percentile the right measure?"**
Because a customer does not experience the average. If a request is slow one time in a hundred and a customer makes a thousand requests an hour, they meet the slow path ten times an hour and form their opinion there. The average tells you the system is healthy and the tail tells you what someone actually felt. The counter-argument I take seriously is that a very high percentile is noisy at low traffic, which was true for our lowest-volume services, and I would use a different measure for those.

**"Six engineering weeks a quarter is a suspiciously round number."**
It is an estimate, and I would rather say that than defend it. I built it from incident time logs before and after across the group, and there is no way to isolate the mesh from everything else that changed in that period. What I will defend precisely is the tail number and the median regression, both from the same dashboards on both sides of the change.

**"What broke?"**
Two things. One service had a hard-coded timeout shorter than the mesh's default retry budget, so it started failing faster under load rather than slower, which took a day to diagnose because the symptom looked like the opposite of what was happening. And certificate rotation caught us once, in staging, which is where I would rather find it.

---

## Reflection

I under-communicated the median regression to the teams, as opposed to leadership. I put it in the proposal, leadership read the proposal, and the engineers who owned individual services mostly did not. So three separate teams independently noticed their median get slightly worse and each opened an investigation. That was avoidable with one message in the right channel at the right time, and the lesson is that writing something down in the document that authorises the work is not the same as telling the people who will see the effect.

---

## Variant framings

**For a question about a metric you chose:** open on the average being fine for a year and on that number there being no case for the work. *Use when:* the question is about measurement judgment rather than systems.

**For a question about cross-team change:** open on fourteen services, one team at a time, and the two week dual path. *Use when:* the question is about moving people who do not report to you.

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
