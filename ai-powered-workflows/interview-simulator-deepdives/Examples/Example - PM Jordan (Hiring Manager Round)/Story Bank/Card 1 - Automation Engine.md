>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Card 1: Automation engine

**Owns:** taking manual work out of a workflow, adoption when users do not trust the automation, trade-off ownership
**Tags:** `#build` `#adoption` `#workflow` `#tradeoffs`
**Source:** Career Brain Trust, `Experience/3.1 Tessera.md`, workflow automation engine bullet
**Status:** drilled 2 times
**Numbers last verified:** 14 June 2026

> **Worked illustration.** Fictional person, fictional employer, illustrative numbers.

---

## Headline, say this first, then stop

> I built a workflow automation engine that about 70 percent of our paying customers were using inside 90 days, and it got adopted because it never took the manual path away.

---

## The two minute spoken version

At Tessera I own developer workflow tooling. The problem I picked up in early 2024 was that engineering teams were doing the same five or six sequences by hand every day. Somebody merges a change, then somebody has to move the ticket, then notify the on-call channel, then close the review thread. Every step is trivial and every one gets forgotten under load, so teams had built their own scripts, which broke silently and nobody owned them.

The obvious product is an automation engine: triggers, conditions, actions. That is what we built. The part worth talking about is the decision I made about failure, because that determined whether it got used.

The first design had the engine take over the step entirely. Trigger fires, action happens, the human is notified after the fact. Our two design partner teams hated it in the first week, and when I sat with them I found out why. Not because it was wrong. Because when it was wrong they could not tell what it had done, so their fix was to turn the whole thing off. One bad automation poisoned the feature.

So I made the call to keep the manual path permanently, not as a migration step. Every automated action stays visible in the same queue a person would have worked, marked as done by the engine, and reversible for 24 hours. That cost us the clean version of the product and about three weeks of engineering. What we got back was that a team could adopt one automation without betting their whole workflow on it.

Ninety days after general availability, roughly 70 percent of paid customers had at least one automation running. The number I watch is the second one: about 40 percent had three or more, the point where it stops being a trial. What I would do differently is instrument the reversals sooner. For the first two months I had no idea how often the engine was wrong, and I was making adoption arguments without that number for longer than I should have.

---

## The spine, five beats

1. Teams were hand-running the same sequences daily and had built fragile private scripts.
2. First design took the step over completely. Design partners rejected it inside a week.
3. The real problem was not accuracy, it was that a wrong automation was invisible and irreversible.
4. I chose to keep the manual path permanently and make every automated action visible and reversible for 24 hours. Cost: the clean product, plus three weeks.
5. About 70 percent of paid customers running one automation by day 90, about 40 percent running three or more. I did not instrument reversals early enough.

---

## The line that ends it

> The lesson I took is that in workflow tooling the adoption blocker is almost never accuracy, it is what happens on the day the tool is wrong.

---

## The decisions I owned

- **Decision:** keep the manual path permanently rather than as a temporary migration affordance. **Alternative considered:** deprecate it at 60 days, as the original roadmap said. **What it cost:** a permanently more complicated product surface, two code paths for the same action forever, and about three weeks of engineering in the first release.
- **Decision:** make every automated action reversible for 24 hours rather than immediately final. **Alternative considered:** an audit log with no undo, which was cheaper. **What it cost:** holding state we would otherwise have thrown away, and the engineering lead was openly unhappy about it.
- **Decision:** ship to two design partners for six weeks before general availability rather than going straight out. **Alternative considered:** a public beta, which our head of product preferred as faster. **What it cost:** roughly five weeks of calendar time. It also surfaced the failure problem, so I would take that trade every time.

---

## Numbers I can defend

| Metric | Before | After | How I know | Verified |
|---|---|---|---|---|
| Paid customers with at least one automation running | 0 | about 70 percent at day 90 | Product analytics, counted at the account level, paid accounts only, 90 days after general availability | 14 Jun 2026 |
| Paid customers with three or more automations | 0 | about 40 percent at day 90 | Same query, different threshold. The number I trust more. | 14 Jun 2026 |
| Design partner teams before general availability | 0 | 2, over 6 weeks | My own project notes | 14 Jun 2026 |
| Engineering cost of the reversibility decision | n/a | about 3 weeks | Estimate from the engineering lead at the time, not a tracked figure | 14 Jun 2026 |

---

## Who did what

- **Me:** framed the problem, ran the design partner sessions, made the manual path and reversibility calls, wrote the specification, chose the adoption metric and argued for the three-or-more threshold over the simpler one.
- **My team:** two engineers designed the trigger and condition model, the actual hard part of the system and not my design. A designer owned the queue interface where automated actions appear.
- **Other functions:** our support team flagged the pattern of broken private scripts in the first place. I did not find it, they did.

---

## Honest boundary

> I owned the product decisions and the adoption argument. The trigger and condition model, the part a payments engineer would actually find interesting, was designed by two engineers on my team. I can tell you why we scoped it the way we did and what it could not express, but if you ask how the evaluation order works internally I would be reconstructing rather than remembering.

---

## Likely follow ups

**"How much of that was you and how much was the team?"**
The problem framing, the design partner programme, and the two calls about failure behaviour were mine. The trigger and condition model was designed by two engineers, and it is what I would point at if you asked what was hardest. The metric choice was mine, argued against a simpler one, which is probably the clearest example of a decision I made alone.

**"How did you know 70 percent was good?"**
I did not, at first. It was the number I had. I added the three-or-more threshold because a single automation is a trial and does not tell you the product landed. Forty percent at three or more is the number I would defend, because it tracks with renewal conversations. The honest limit is that I never ran a clean counterfactual, so I cannot separate the automation engine's effect from everything else that shipped that quarter.

**"What did the manual path cost you later?"**
Two code paths for the same action, permanently, and a support surface where a customer can be confused about whether a person or the engine did something. We have not fixed that. If I were doing it again I would keep the decision and spend some of the three weeks making the "who did this" attribution clearer in the queue.

---

## Reflection

The thing I got wrong was instrumentation order. I built the adoption metrics first because those were the ones I had to report, and did not instrument the reversals until month three. For two months I argued the engine was trusted, using adoption as the proxy, when the number that would have told me was how often people undid what it did. When I finally got it, the reversal rate was low, so the argument survived. It could just as easily not have.

---

## Variant framings

**For a question about influencing without authority:** open on the design partner sessions and the head of product wanting a public beta, and lead with how I got the extra five weeks rather than the adoption number. *Use when:* the question is about moving people who do not report to you.

**For a question about a technical trade-off:** open on the reversibility decision and the state we had to hold to support it, and name the engineering lead's objection explicitly. *Use when:* the interviewer came up through engineering and the question is about a decision that cost engineering something. This is the version to use with Devin.

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
