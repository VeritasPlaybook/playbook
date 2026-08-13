>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Card 1: Idempotency primitives

**Owns:** correctness under distributed failure, interface design, blast radius
**Tags:** `#correctness` `#api` `#distributed` `#payments`
**Source:** Career Brain Trust, `Experience/3.1 Beacon Pay.md`, idempotency bullet
**Status:** drilled 2 times
**Numbers last verified:** 16 June 2026

> **Worked illustration.** Fictional person, fictional employer, illustrative numbers.

---

## Headline, say this first, then stop

> I designed the idempotency primitives for our payment Application Programming Interface, and duplicate charge incidents dropped about 95 percent in the twelve months after, against the twelve months before.

---

## The two minute spoken version

At Beacon Pay I own the transaction processing service, written in Go, handling roughly four million transactions a day across four regions.

The problem I picked up in early 2024 was duplicate charges. A client would submit a payment, our response would be lost somewhere between us and them, and the client would retry. Their retry was correct behaviour. We charged the card twice. From the outside it looks like a bug in our system, and from the inside there was no bug anywhere, which is why it took a while for anyone to own it.

The obvious fix is an idempotency key on the request. What made it interesting was deciding what a key means when the two requests are not identical. Same key, different amount: is that a retry of a request we already processed, a client bug, or a different payment that reused the key by accident. I made the call that a mismatched payload under an existing key returns a conflict error rather than the original result or a new charge. That is stricter than some payment interfaces, and it makes life harder for a client generating keys sloppily. I took that trade on purpose, because the alternative failure is silently returning the wrong transaction, and a silent wrong answer in a payments system is much more expensive than a loud error.

The other decision was scope. The keys live in a table with a 24 hour retention window, not forever. Forever is easier to reason about and grows without bound in a system doing four million a day. Twenty four hours covers essentially every real retry pattern in the logs. If a client retries after 25 hours they get a second charge, and we documented that rather than hiding it.

Duplicate charge incidents went from roughly one a week to about one every five weeks over the following year, the 95 percent reduction. The primitives were picked up by the refund and dispute services afterward, which I did not plan and am most pleased about.

---

## The spine, five beats

1. Clients retried after a lost response and we charged twice. Correct behaviour on both sides, no bug anywhere.
2. The design question was not "add a key," it was what a key means when payloads differ under it.
3. My call: mismatched payload under an existing key returns a conflict, not the original result and not a new charge. Loud beats silent.
4. Twenty four hour retention rather than forever, documented rather than hidden, because unbounded growth at four million a day is its own incident.
5. About one duplicate incident a week down to about one every five weeks. The primitives were later reused by refunds and disputes.

---

## The line that ends it

> The principle I took from it is that in a payments system a loud wrong answer is cheap and a quiet wrong answer is not, and the interface should be designed around that asymmetry.

---

## The decisions I owned

- **Decision:** mismatched payload under an existing key returns a conflict error. **Alternative considered:** return the original stored response, which one of the interfaces we looked at does and which is friendlier to a sloppy client. **What it cost:** two client integrations broke on rollout and had to be fixed by their teams, and I defended that in a meeting I did not enjoy.
- **Decision:** 24 hour key retention rather than indefinite. **Alternative considered:** indefinite, with a separate archival job later. **What it cost:** a real hole in the guarantee at the 25 hour boundary, which we documented rather than papered over.
- **Decision:** put the key handling in a shared library rather than in the service. **Alternative considered:** implement it inside the transaction service only, three days of work instead of two weeks. **What it cost:** two weeks, plus the ongoing burden of a shared library with several consumers. It is why refunds and disputes could adopt it later, so I would take the trade again, though I did not foresee that when I made it.

---

## Numbers I can defend

| Metric | Before | After | How I know | Verified |
|---|---|---|---|---|
| Duplicate charge incidents | about 1 per week | about 1 per 5 weeks | Incident tracker, counted over the 12 months before launch and the 12 months after. Same classification, same team classifying. | 16 Jun 2026 |
| Transaction volume on the service | about 4 million per day | unchanged | Service dashboards, daily average over a quarter | 16 Jun 2026 |
| Client integrations broken at rollout | 0 | 2 | My own rollout notes | 16 Jun 2026 |
| Services that later adopted the library | 1 | 3 | Repository dependency list | 16 Jun 2026 |

**Verification line:** what told me it worked was not the incident count, which takes months to be meaningful. It was a shadow counter: for the first six weeks the library logged every case where it would have rejected a request, without rejecting it, and we read those logs by hand. That told us the conflict rule was firing on real retries and not on something we had not thought of.

---

## Who did what

- **Me:** the design, the conflict semantics, the retention decision, the shared library structure, and the shadow counter rollout. I wrote the Request-for-Comments document and defended it.
- **My team:** one engineer implemented the storage layer and did the load testing. Another did the client migration work for the two broken integrations.
- **Other functions:** the support team supplied the original duplicate charge reports, which is how we sized the problem before building anything.

---

## Honest boundary

> I owned the semantics and the interface. I did not own the storage layer implementation, and if you ask about the locking behaviour under contention I would be reconstructing rather than remembering. What I can tell you precisely is why we chose the conflict semantics and what it cost in client integrations.

---

## Likely follow ups

**"Why not just return the stored response on a mismatch? That is what most people do."**
Because a mismatched payload is evidence something is wrong on the client side, and returning a stored response tells them everything is fine. If the amount differs, one of two things is true: they are retrying a request they mutated, or they reused a key by accident. Both are bugs I would rather they find in staging with a loud error than in production with a silently wrong transaction. It cost us two broken integrations and I still think it is right. I would accept the argument that a well-documented interface with the friendlier behaviour and good client libraries gets to the same place with less friction.

**"What happens at hour 25?"**
They get a second charge, and we say so in the documentation. It is a real hole. The alternative was unbounded growth in a table on a system doing four million a day, and I judged an honest documented boundary better than an implicit one that shows up as a storage incident in eighteen months. If I were doing it again I would add a metric on retries arriving near the boundary, so we would know if anyone was living there. We did not have that and I was guessing.

**"How would this apply to a reconciliation matching engine?"**
Carefully, and I would want to be told where I am wrong. The surface similarity is that both are about deciding whether two things are the same thing. The difference is that idempotency has an explicit key supplied by a client who wants to be understood, and matching has no key and a counterparty not trying to help you. So the primitive I would reach for is different. What I would expect to transfer is the shadow counter: run the new rule alongside the old, do not act on it, and read what it would have done.

---

## Reflection

The thing I got wrong was sequencing the client communication. I shipped the shared library and the conflict semantics before talking to the two client teams whose integrations were generating keys loosely. I found them by breaking them. A one-week shadow period with a report to each client team would have cost nothing and turned two escalations into two scheduled fixes. I now do that as a matter of course, the specific habit that came out of this project.

---

## Variant framings

**For a question about a technical decision where both options were defensible:** open on the conflict versus stored response choice and give both cases fairly before saying which I took. *Use when:* the question is explicitly about a trade-off rather than a system.

**For a question about being wrong:** open on the client communication failure, not the design. The design held. The rollout did not. *Use when:* the question asks about a mistake and I do not want to reach for a story where nothing went wrong.

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
