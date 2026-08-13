>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Card 3: Connector roadmap

**Owns:** prioritising against teams you do not control, saying no to a large customer, expansion mechanics
**Tags:** `#prioritisation` `#influence` `#roadmap` `#integrations`
**Source:** Career Brain Trust, `Experience/3.1 Tessera.md`, integrations roadmap bullet
**Status:** drilled 1 time
**Numbers last verified:** 14 June 2026

> **Worked illustration.** Fictional person, fictional employer, illustrative numbers.

---

## Headline, say this first, then stop

> I owned the integrations roadmap and shipped six connectors in a year, and the decision I am most sure about is the seventh one I refused to build.

---

## The two minute spoken version

At Tessera I owned integrations. Our product sits in the middle of an engineering team's day, so it is only as useful as the tools it can reach: source control, the issue tracker, the alerting system. Every connector we did not have was a reason to keep a browser tab open somewhere else.

I had about twenty requested connectors and capacity for maybe six in the year. The default way to pick is by request count, which gives a list dominated by whoever shouts loudest in the customer council. Instead I scored each on two things: how many accounts inside an existing paying customer it would unlock, and whether the vendor's Application Programming Interface (API) was stable enough that we would not maintain the connector forever. The second criterion changed the answer, and it took a fight.

The six we shipped drove about a 19 percent increase in average accounts per paying customer over the year. That is the expansion mechanic: a connector does not usually win a new logo, it spreads one you already have into a second and third team.

The one I refused was a connector to an internal deployment tool used by one very large customer, the single loudest request I had. Their API had no versioning, it changed without notice twice during our evaluation, and we would have owned that maintenance forever for one account. I said no in the customer council, in front of the other seven customers, which was uncomfortable and turned out to be the right room, because two of them told me afterward they had assumed we built whatever the biggest account asked for.

The thing I would do differently: I let that refusal sit for four months without offering anything. Eventually we shipped a generic webhook that solved about 70 percent of what they wanted. I should have offered it in the same conversation.

---

## The spine, five beats

1. Twenty requested connectors, capacity for six, default prioritisation would have followed the loudest voice.
2. I scored on accounts unlocked inside existing customers, and on whether the vendor API was stable enough not to become permanent maintenance.
3. Six shipped. About 19 percent growth in average accounts per paying customer over the year.
4. I refused the loudest request, an unversioned internal API for one large account, and said so in the customer council rather than privately.
5. I left the no sitting for four months before offering the generic webhook that covered most of it. That gap was my mistake.

---

## The line that ends it

> The connector I did not build is the one that taught the rest of the council what our roadmap actually responded to, which was worth more than the connector would have been.

---

## The decisions I owned

- **Decision:** score connectors on accounts unlocked plus vendor API stability rather than request volume. **Alternative considered:** straight request count, what the previous roadmap used and what our account team expected. **What it cost:** two connectors with high request counts got pushed to the following year, and I defended that to the account team twice.
- **Decision:** say no to the largest account's request in the customer council rather than in a private call. **Alternative considered:** the private call, which was safer for the relationship. **What it cost:** a genuinely uncomfortable 20 minutes and some short-term friction with that account's engineering lead.
- **Decision:** hold the line for four months before offering the webhook alternative. **Alternative considered:** offering it immediately. **What it cost:** four months of that customer believing we had simply dismissed them. I got this one wrong and would reverse it.

---

## Numbers I can defend

| Metric | Before | After | How I know | Verified |
|---|---|---|---|---|
| Average accounts per paying customer | baseline at start of year | about 19 percent higher at year end | Product analytics, accounts per paying customer, measured at the same point in each quarter | 14 Jun 2026 |
| Connectors shipped | 0 in the prior year | 6 | Release record | 14 Jun 2026 |
| Requests on the list | about 20 | 6 built, 2 deferred, the rest declined | My own roadmap document | 14 Jun 2026 |
| Customer council accounts | 8 | 8, weekly | Meeting record | 14 Jun 2026 |

The 19 percent needs a caveat I should say before being asked: connectors were not the only thing that shipped that year, so I cannot attribute all of it. What I can attribute is the pattern: account growth inside a customer clustered in the weeks after a connector landed for that customer's stack.

---

## Who did what

- **Me:** built the scoring model, made the prioritisation calls, ran the customer council, delivered the refusal, and made the four month delay on the alternative.
- **My team:** three engineers built the connectors. The retry and error handling pattern that made them maintainable was theirs, and it is why six was possible rather than four.
- **Other functions:** the account team supplied the request data and disagreed with the model, which was a useful pressure test even though I did not change it.

---

## Honest boundary

> I owned the prioritisation and the customer relationship. I did not build the connectors and did not work out how to make them cheap to maintain. If you ask why six was achievable in a year, the honest answer is that two engineers built a shared error handling pattern first, and that decision was theirs, not mine.

---

## Likely follow ups

**"What was your scope: team size, budget, decision rights?"**
Three engineers and a shared designer on the integrations surface, inside a team of nine. No budget authority. Decision rights: I set connector priority and could decline a request without escalation, which is the one that matters. I could not change headcount or the release calendar. The refusal was mine alone, and I told my manager after the council, not before.

**"Was the 19 percent actually yours?"**
Partly. Six things shipped that year and connectors were one of them. What I would defend is the timing pattern: account growth inside a given customer clustered in the weeks after a connector for that customer's stack landed. The clean version is that connectors were the largest single contributor and I cannot isolate the number.

**"What would you have done if your manager had overruled the refusal?"**
Built it, and said so to the council myself rather than letting it look like the decision had never been mine. I would have written down the expected maintenance cost and asked to revisit in two quarters, which is roughly what I did the one time I lost a similar argument on a different connector.

---

## Reflection

The refusal was right and the way I held it afterward was wrong. A no with no alternative attached reads as a dismissal no matter how well reasoned, and four months is long enough for the relationship damage to become what people remember instead of the decision. Now, when I decline something significant, I name the nearest thing I will do in the same conversation, even if it is smaller and not ready.

---

## Variant framings

**For a scope and level question:** open with the three engineers, the decision rights line, and being able to decline without escalation. *Use when:* the question is "what was the scope of your last role."

**For a question about a hard conversation:** open on the customer council refusal and the two customers who told me afterward what they had assumed. *Use when:* the question is about difficult stakeholder moments rather than about roadmap mechanics.

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
