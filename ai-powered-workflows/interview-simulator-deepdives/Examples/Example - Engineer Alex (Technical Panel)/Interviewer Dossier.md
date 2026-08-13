>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Interviewer Dossier: Ines Kowalczyk and Marcus Dube, Northwind Payments technical panel

> **Worked illustration. Both people are fictional and so are all the sources.** Ines Kowalczyk and Marcus Dube do not exist. Northwind Payments does not exist. Every citation below is invented, written in the real format only so you can see the shape of a filled dossier. When you build your own, sources must be Uniform Resource Locators (URLs) you can open, and anything unverified belongs in the open flags section rather than a confirmed table.
>
> **A note on the one-file exception.** The template says one file per human, and it is right, because merging two people is how you lose track of which one is testing what. This example uses one file for two because it is a single 60-minute call and a reader benefits from seeing them side by side. The sections below are still kept strictly separate per person. If this were a four-person loop it would be four files.

**Round:** Technical panel
**Date:** Thursday 2 July 2026, 1:00 in the afternoon Pacific
**Format:** Video, 60 minutes, both interviewers present for the whole call

---

## Headline correction

> **Assumed:** the Staff Engineer runs the hard technical portion, probably a system design exercise, and the Engineering Manager runs the softer half: collaboration, how you work with people, why you want the job. Prepare a greenfield design narrative for her and teamwork stories for him.
>
> **Actually:** close to the reverse on both counts. Ines's public work is not about designing new systems, it is about changing existing ones without breaking them. Her conference talk and the June 2025 post are both about verification during a cutover: proving the new thing agrees with the old before you trust it. And Marcus spent six years as a site reliability engineer before moving into management three years ago. He still carries a pager one week in six, by choice, and the two questions he is known for internally, according to a candidate write-up I found, are both about incidents.
>
> **Consequence for the round:** I would have walked in with a throughput narrative for Ines and a collaboration narrative for Marcus. Both would have missed. Ines will hear "seven times throughput improvement" and ask how I knew the data was still right, and if my answer is thinner than my throughput number I have shown her exactly what she is screening for. Marcus will not ask about teamwork at all. He will ask what a customer saw during the worst hour of my career, and I do not have a card for that.

---

## Interviewer one: Ines Kowalczyk, Staff Engineer, Money Movement

### Who she is, confirmed background

*All sources fictional.*

| Fact | Source |
| --- | --- |
| Staff Engineer, Money Movement. At Northwind since 2021. | Fictional careers page team listing |
| Came up through database and data platform work at two previous companies before Northwind | Fictional conference speaker biography, 2025 |
| Named on the byline of the June 2025 engineering post on moving settlement reconciliation off the overnight batch window | Fictional engineering blog |
| Gave a 2025 conference talk on verifying a migration by running the old and new paths in parallel | Fictional conference archive |

### Her team and its mandate

- **Team:** Money Movement, inside the merged risk and money movement group formed in January 2026.
- **What it owns:** Ledger, the matching engine, and the exception path. Payouts sits adjacent.
- **Likely success metric:** unmatched value and its age, meaning how much money is unexplained and for how long. (INFERRED. Nothing public states it.)
- **Where this role sits relative to her:** peer on paper, in practice a person she would review. She is the technical bar setter for the loop.

### Public footprint

| Item | Where | The specific detail I would reference |
| --- | --- | --- |
| Conference talk, 2025, on migration verification | Fictional conference archive | She spent nine of the twenty minutes on the dual-run comparison period and about three on the new design. The ratio is the message. |
| Engineering post, June 2025 | Fictional Northwind engineering blog | The post says they ran old and new in parallel and alerted on disagreement rate rather than the new system's own health, and the disagreements they found were almost all edge cases nobody had modelled. |

- Searched: professional network profile. Result: found, minimal.
- Searched: personal blog. Result: searched, not found.
- Searched: public code repositories. Result: found one, a small library, last commit 2023, not worth referencing.

### What she is likely to test, and why (INFERRED)

1. **Likely test:** whether I have actually run a migration or read about one.
   **Why I think so (INFERRED):** both public artifacts are about migration verification. Somebody who spends nine of twenty minutes on the comparison period has been burned by a cutover that looked fine.
2. **Likely test:** whether I can defend a data modelling choice under pushback, specifically a partitioning or sharding decision.
   **Why I think so (INFERRED):** she came up through database work and owns the Ledger data model. This is her home ground and she will go there.
3. **Likely test:** what I do when a system is correct and slow versus fast and occasionally wrong.
   **Why I think so (INFERRED):** that is the stated tension in her 2025 talk and the permanent condition of a reconciliation system.

### What wins her

- Naming the verification method before naming the result.
- Saying how I would know a change was wrong, not just how I would make it.
- Treating edge cases as the main event rather than as cleanup.
- Being specific about what I gave up. She will not believe a migration that cost nothing.

### What loses her

- Leading with a throughput or latency number and having nothing behind it.
- Describing a migration as a sequence of steps with no failure branch.
- Asserting anything about Northwind's internals. She knows and I do not.
- Treating a shard key or partition key as an implementation detail.

---

## Interviewer two: Marcus Dube, Engineering Manager, Authorization and Risk Platform

### Who he is, confirmed background

*All sources fictional.*

| Fact | Source |
| --- | --- |
| Engineering Manager, Authorization and Risk Platform. Manager for three years, at Northwind for five. | Fictional careers page |
| Six years as a site reliability engineer before management, at a different company | Fictional professional network profile |
| Carries a pager one week in six by choice | Fictional candidate write-up on a public interview experience forum, dated January 2026 |
| Listed as a contact on the February 2026 authorization degradation post-mortem | Fictional status page |

### His team and its mandate

- **Team:** Authorization and Risk Platform. Different team from the one this role would join.
- **What it owns:** the authorization path and Sentinel. Upstream of Ledger.
- **Likely success metric:** availability and acceptance rate on the authorization path. (INFERRED.)
- **Where this role sits relative to him:** cross-functional. He is on this panel as the on-call and operability check, not as the hiring manager.

### Public footprint

| Item | Where | The specific detail I would reference |
| --- | --- | --- |
| February 2026 post-mortem, listed as a contact | Fictional status page | The post-mortem describes a dependency that got slow and never errored, and unrelated traffic failing as a consequence. The remediation list has "add timeouts" third, behind two items about detection. |
| Candidate write-up mentioning him | Fictional interview experience forum, January 2026 | The write-up says he asks "what did the customer see" and does not accept an internal metric as an answer. Single-source and unverified, treat as rumour, but cheap to prepare for and expensive to be surprised by. |

- Searched: conference talks. Result: searched, not found.
- Searched: personal blog or newsletter. Result: searched, not found.
- Searched: public code repositories. Result: searched, not found.

### What he is likely to test, and why (INFERRED)

1. **Likely test:** whether I have been woken up, and what I did.
   **Why I think so (INFERRED):** six years in site reliability, still carries a pager voluntarily. This is not a hypothetical for him.
2. **Likely test:** whether I can describe an incident from the outside in, meaning what a sub-merchant experienced, before describing it from the inside out.
   **Why I think so (INFERRED):** the forum write-up, plus the ordering of the February remediation list, which puts detection above mitigation.
3. **Likely test:** whether I write things down after the fact, and whether anyone reads them.
   **Why I think so (INFERRED):** Northwind publishes post-mortems externally, which is a cultural choice somebody has to defend internally.

### What wins him

- The user-visible symptom first, then the mechanism.
- Separating what stopped the bleeding from what fixed the cause, and giving both timestamps.
- Naming what was not fixed and why that was the right call.
- First person singular. What I did, at what time.

### What loses him

- Answering "what did the customer see" with a graph.
- An incident story where the candidate is the narrator rather than a participant.
- Any suggestion that on-call is somebody else's problem, or that good engineering makes it unnecessary.
- Blaming a vendor without saying what the system should have done about it.

---

## The quiet question in each of their heads

> **Ines's unspoken doubt:** "Has this person actually changed a live system that holds money, or have they built new things next to old things and called it a migration?"
>
> **How I disarm it without naming it:** the first time a migration comes up, I lead with the comparison period rather than the outcome. Something like: "before I tell you what it did to throughput, the part that took longest was proving the new path agreed with the old one on four months of history." That answers her doubt before she has to design a question to test it, and it is true, which is why it works.

> **Marcus's unspoken doubt:** "When this person's change breaks at three in the morning, am I going to hear about it from them, or from a platform partner?"
>
> **How I disarm it without naming it:** one incident answer where I name the time of detection, who detected it, and whether it was us or a customer. The honest version of my worst one is that a customer told us first, and saying that out loud is more disarming than any story where monitoring caught it, because he has heard the polished version many times.

---

## Wrong person exclusions

- **Do not merge:** a Marcus Dube who is an academic in a different field with a substantial publication record. Distinguishing detail: different country, no industry history. Source: fictional.
- **Do not merge:** a second Alex Rivera working in payments, my own name and not an interviewer, worth recording because two searches for "Alex Rivera payments" returned that person's conference biography and briefly contaminated a research pass. Distinguishing detail: different employer, different specialty. Source: fictional.
- **Do not merge:** Northwind Logistics is an unrelated company that shares part of the name. Two search results for Northwind leadership belong to it. Source: fictional.

---

## Open flags to verify in person

| Open flag | How to ask lightly |
| --- | --- |
| Ines still owns the Ledger data model | "I may have this out of date, but is the data model still on your side of the line, or has that moved?" |
| The move off the overnight batch window is finished | "Is the move off the batch window done, or is it still in flight?" |
| The February degradation was pool exhaustion | "The shape of it, a dependency that got slow and never errored, is the failure mode I find most dangerous. Is that roughly what happened?" |
| Marcus asks the "what did the customer see" question | Do not ask. Just prepare the answer. |
| Their event log's ordering and delivery guarantees | "What are your ordering and delivery guarantees on the event log? I want to know before I answer that, because what I have worked with may not match." |

---

## What this means for my prep

1. Ines spent nine of twenty conference minutes on the dual-run comparison period, therefore I rewrite the opening of Story 2 so the verification method comes before the throughput number, and add the comparison figures to the card: how many rows were compared, over what history, and the disagreement rate at cutover.

2. Ines came up through database work and owns the data model, therefore I write down the shard key rationale for my own migration in one sentence, plus the two candidates I rejected and why. This is the follow-up I will get and it is nowhere in my artifacts.

3. Marcus is a former site reliability engineer who still carries a pager, therefore I build an incident card before the round, with the detection time, who detected it, the mitigation and the durable fix separated, and the customer-visible symptom stated first. I do not have one and this is the largest gap in the folder.

4. A single-source rumour says Marcus does not accept an internal metric as an answer to "what did the customer see," therefore I write the customer-visible symptom onto every technical card, including the two that are not incident stories, as one line each. Cheap insurance and it forces me to know the answer.

5. Both of them will find the edge of what I know about their event log inside twenty minutes, therefore I rehearse the substitution line rather than the assumption: describe the guarantees I have worked with, ask what theirs are, and then answer. Saying it once in a mock is the difference between arriving naturally and arriving as a dodge.

6. This is a Senior posting and my public positioning says I am targeting Staff, therefore I write two flat sentences about why I am running this loop anyway, and say them without hedging or sulking. Neither interviewer is the hiring manager, so this is not their decision, and the only thing at stake is whether I sound settled about it.

---

## Sources

*All fictional. Dead ends included.*

- Fictional Northwind Payments careers page, team listing, retrieved 15 June 2026.
- Fictional conference archive, 2025 talk on migration verification.
- Fictional Northwind Payments engineering blog, June 2025 post, byline.
- Fictional Northwind Payments status page post-mortem, March 2026, contact list.
- Fictional public interview experience forum, January 2026, single candidate write-up. Treat as rumour.
- Searched conference archives for Marcus Dube: not found.
- Searched public code repositories for Marcus Dube: not found.
- Searched for the size of the Money Movement team: not found.

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

Based on "Interviewer Dossier: Ines Kowalczyk and Marcus Dube," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
