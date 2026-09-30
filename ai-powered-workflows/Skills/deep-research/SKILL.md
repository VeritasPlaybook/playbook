---
name: deep-research
description: "A tiered, evidence-based research method for Claude. Plans once, fans out to isolated sub-agents that return compressed briefs, verifies load-bearing claims against primary sources, checks for retractions, counts independent sources, then synthesizes. Three tiers (Scan, Standard, Deep) so effort matches the question, and when the user has not named a tier it runs a cheap Scan first and recommends whether to go deeper. Trigger on \"deep research\", \"/deep-research\", \"research this properly\", \"do a deep dive on\", \"what does the literature say about\", or any request where the user expects sourced findings rather than an answer from memory. Do NOT auto-fire on casual lookups (\"what is X\", \"look this up\", \"who is Y\"); answer those plainly. Offer the skill when a question clearly needs it, but never start a run without the user saying yes."
---

# Deep Research

A research method for getting better answers for fewer tokens. Built from a literature review of deep research agent design (August 2026), cross-validated against an independent second research engine, with load-bearing figures checked against primary sources. Revised in September 2026 (see `CHANGELOG.md`).

**Why this exists.** Naive deep research is expensive and often wrong in ways that look right. Anthropic's own write-up of its multi-agent research system reports that agents use about 4x the tokens of a chat, and multi-agent systems about 15x, and that token usage alone explained 80% of the performance variance on their browsing evaluation. The same system beat a single agent by 90.2% on their internal research eval, so the spend buys something real ("How we built our multi-agent research system", Anthropic Engineering, June 2025). The job of this skill is to keep what the extra agents buy and cut what they waste. Every rule below traces to a measured finding, and the evidence grade is stated so nothing is followed on faith.

---

## THE FOUR RULES THAT DO THE WORK

**1. Plan once. Do not re-plan after every observation.**
ReWOO (arXiv:2305.18323) measured 5x token efficiency and a 4 point accuracy gain on HotpotQA by deciding the whole research plan up front, then executing it, rather than rethinking after each tool result. This is the only technique found that improves quality and cuts cost at the same time. Grade: verified against primary source.

**2. Raw text never enters the orchestrator context.**
Sub-agents read pages in their own context windows and return a compressed brief. The orchestrator sees briefs, never page dumps. This is what keeps a sixty source run from bloating the main session. Why it matters: models degrade as context grows. GPT-4o drops from 99.3% accuracy on short contexts (under 1,000 tokens) to 69.7% at 32,000 tokens on retrieval that requires inference rather than literal matching (NoLiMa, arXiv:2502.05167), and information placed mid-context is used far less reliably than information at the start or end (Lost in the Middle, arXiv:2307.03172, TACL 2024). Grade: the degradation findings are well established; the token saving from isolation specifically is architectural reasoning, not an isolated measurement.

**3. Better retrieval beats more searching.**
On BrowseComp-Plus (arXiv:2508.06600, ACL 2026), swapping a keyword retriever (BM25) for a dense one raised an o3 agent's accuracy from 49.3% to 63.5% while *lowering* cost from about $836 to $741 across 830 queries, because the agent needed fewer calls. Agents over-search to compensate for bad retrieval. When results are thin, write a better query; do not run more queries. Grade: peer reviewed.

**4. Never self-review. Verify against the source instead.**
When GPT-4 was asked to review and correct its own answers without outside feedback, GSM8K accuracy fell from 95.5% to 91.5% (Huang et al., "Large Language Models Cannot Self-Correct Reasoning Yet", arXiv:2310.01798, ICLR 2024). Models also show a documented "self-correction blind spot": they fix an error when it is shown to them as someone else's, but miss the same error in their own output (Self-Correction Bench, arXiv:2507.02778). Verification means re-opening the cited source and checking it says what the report claims, done by a separate agent. Grade: peer reviewed for the first finding, preprint for the second.

---

## PHASE 0: CONFIRM BEFORE RUNNING

**Never start a run without the user confirming.** A run costs real budget, and the most expensive failure is researching the wrong question well.

Proportional to tier:

- **Scan**: one confirmation. Restate the question neutrally, name the tier, wait for yes.
- **Standard and Deep**: a short question set before planning. Cover: the decision the research feeds, any existing position the user wants tested, scope boundaries and timeframe, which sources count for this topic, and output shape.

Ask them as a short numbered list. Give each question a recommended default and the reason for it, so the user can reply "defaults" and move on. Then stop. Do not generate the plan in the same message as the questions.

### Restate the question neutrally first

Models accept the user's framing far more readily than people do. In the ELEPHANT benchmark, models accepted the framing of a user's question 90% of the time against 60% for humans, and offered emotional validation at more than three times the human rate (arXiv:2505.13995). Applied here, the user's wording biases what comes back.

So before planning, restate the question in neutral terms and show the restatement. If the phrasing presupposes an answer ("why is X better than Y"), say so and offer the neutral version ("how do X and Y compare").

### When the user has not named a tier, climb the ladder

**If the user names a tier**, by asking for a deep dive, a scan, a proper research run, or anything else that picks the depth, they have made the call. Honour it, ask the question set for that tier, and go.

**If they have not named one, do not ask them to pick blind.** Offer a Scan, and once they say yes, run it. Then come back with:

- The rough shape of the answer, in three or four lines
- What turned out to be contested, and what turned out to be settled
- Whether the question as asked is the right question, or whether the Scan surfaced a better one
- A tier recommendation with its reason, and specifically what going up a tier would buy that the Scan did not already deliver

Then stop and let the user choose.

**Why this order.** A tier is a bet on how hard a question is, and that is exactly the thing nobody knows before looking. Guessing it from the wording of the request is guessing from mood rather than stakes: "what's the deal with X" and "evaluate whether X holds up" can want identical depth, because stakes live in the decision attached to the question, not in the sentence. A Scan is a small fraction of the cost of a Standard run, so the ladder adds a little to a run that was going to happen anyway, and it saves the entire cost on the two occasions that matter: when the Scan shows the question was wrong, and when it shows the answer was simple.

Grade: reasoning, not a measured finding. The underlying claim, that effort should follow evidence rather than precede it, is not something anyone has benchmarked.

### Choosing the tier

| | Scan | Standard | Deep |
|---|---|---|---|
| Use when | Orienting, checking a fact, is this worth pursuing | A real question with a decision attached | High stakes, contested, or expensive to get wrong |
| Sub-agents | 0 to 1 | 3 to 4 | 5 to 8 |
| Search rounds | 1 | 2 | 2, gather then targeted gap-fill |
| Sources scanned | ~10 | ~30 | ~60 |
| Sources read fully | 3 to 5 | 8 to 12 | 15 to 20 |
| Adversarial searches, minimum | 1 | 3 | 5 |
| Citation graph expansion | No | Yes | Yes |
| Coverage matrix | No | Yes | Yes |
| Verification pass | No | Load-bearing claims | Load-bearing claims |
| Mid-run checkpoint | No | No | Yes |
| Output | Chat answer | Markdown file | Markdown file |

If the question does not match the tier asked for, say so and recommend the right one. Talking the user down to a Scan when a Scan will do is one of the most useful things this skill does.

**Deep does not mean a bigger pile.** The evidence that more retrieval helps is weak and partly points the other way. One study found fact-check accuracy dropped by about 42% as tool calls scaled from 2 to 150 (arXiv:2605.06635), and retrieval-augmented generation work shows that irrelevant but high-scoring documents in the prompt hurt answers (The Power of Noise, arXiv:2401.14887, measured on short-answer question answering only, so grade this as indicative not settled). Depth buys **better sources, more sub-questions, and harder verification**, not more reading.

---

## PHASE 1: PLAN ONCE

Write the complete plan before any searching. The plan states:

1. **The neutral question**, plus 3 to 6 sub-questions. Keep sub-questions loosely coupled. Decomposition helps on structured topics but can fragment multi-hop questions, so if answering requires chaining facts together, decompose less. Grade: a caution from limited evidence, not a law.
2. **Source routing per sub-question**, from the table below.
3. **What would change the answer.** Name in advance what evidence would overturn the expected result, and assign a sub-agent to look for it. This is the countermeasure to sycophancy and to settling early on a wrong framing.

   Give this a count, not only an owner. The tier table sets a minimum number of searches that must go hunting for the case against, and they are searches rather than intentions: "criticism of X", "limitations of X", "why X does not work", "X replication failure", "X was wrong". A named intention gets quietly dropped once the first three results agree with the expectation, because nothing makes the omission visible. An unmet count is visible. Adversarial queries also surface a different class of page than breadth searching reaches, so this is a coverage argument as much as a bias one.
4. **The stopping condition**, meaning what "enough" looks like for this run.

Show the user the plan on Standard and Deep. Then execute it. Do not silently re-plan mid-run. If the plan turns out to be wrong, stop, say so, and re-plan explicitly with the user.

### Before executing, check the plan against the question

On Standard and Deep, write a four column table, one row per substantive noun phrase in the user's original wording:

| Phrase from the question, verbatim | Which sub-question covers it | Is the scope the same | Gap? |

Flag any row where the plan has quietly narrowed, broadened, or dropped something. If the user asked about "supplements" and the plan says "creatine", that is a gap and not a detail. If they asked about "the last five years" and the plan has no date bound, that is a gap. Fix the plan and redo the table before any searching. Do not proceed with a known gap.

**Why this is worth the two minutes.** Scope drift at the planning stage is the most expensive error available, because everything downstream executes faithfully against the narrowed question and nothing later in the run can notice. Verification checks whether claims are true, not whether they answer what was asked, so a perfectly verified report on the wrong question passes every other check in this skill. The matrix runs before any money is spent, and it is the only place this class of error is catchable.

Show the table to the user alongside the plan.

Grade: adapted from the coverage matrix in the open source Hyperresearch harness (see Credits), not independently measured. The reasoning above is the case for it.

---

## SOURCE ROUTING

Two separate questions: **where to look**, and **whether what you found is any good**.

### Where to look, by domain

| Domain | Primary | Then | Notes |
|---|---|---|---|
| Artificial intelligence, machine learning, computer science | arXiv (cs.CL, cs.AI, cs.IR, cs.LG, cs.MA) | Semantic Scholar and OpenAlex for citation expansion, then conference proceedings (NeurIPS, ICML, ICLR, ACL, EMNLP, SIGIR), then lab engineering write-ups | arXiv is not peer reviewed. Say so every time. Lab engineering posts often carry the cost and deployment numbers papers omit |
| Medicine, health, nutrition, pharmacology | PubMed, Cochrane | Systematic reviews and meta-analyses before individual trials | Grade by study design. Community sources are lead generation here, never evidence |
| Finance, legal, regulatory | Primary filings, regulator publications, statute and case text | Reputable financial press for context only | Never a secondary summary where the primary document is reachable |
| Consumer products, tools, pricing, practical how-to | Independent testing organisations, then aggregated user reports | Specialist forums, Reddit | See the community sources section below |
| News and current events | Primary reporting, multiple independent outlets | Wire services | Check whether outlets are independent or all sourced from one origin |
| Anything else | The quality checklist below | | |

**Always include a general web fallback, even on scholarly topics.** Scholarly search interfaces alone under-cover the literature. A journals-only hierarchy is a mistake. Grade: directionally consistent with the recall finding below, not separately measured here.

**Follow bibliographies on Standard and Deep.** On a 250 paper literature search benchmark, plain scholarly search API queries topped out near 15% recall, while a pipeline that expands breadth-first along the reference lists of papers already found exceeded 80% (Sahu, Charlin and Pal, arXiv:2605.29234). Searching the obvious way finds a small fraction of what is there.

Also from that paper, worth remembering: human reference lists are not a gold standard. A neutral judge rated only 51% of human citations as moderately relevant or better, versus 86 to 88% for the strongest AI rerankers, and humans were 2.5 times more likely to cite a direct collaborator.

### Whether the source is any good

Assess on two axes, derived from SourceBench (arXiv:2602.16942), a single preprint evaluated on 100 queries and about 4,000 sources. **Use it as a checklist, not a validated instrument.** No empirically validated cross-domain source quality taxonomy was found in two independent research runs.

**Content signals**: relevance to the actual question, factual accuracy where checkable, objectivity and whether the source has something to sell.

**Provenance signals**: freshness, who owns the site, whether a named accountable author exists, domain authority, whether methodology is stated, primary versus secondary, and peer review status.

One counterintuitive finding worth honouring: giving a model the page text made its authority judgements *worse*, because authority and polished writing are separable and models conflate them (AuthorityBench, arXiv:2603.25092, preprint). **So judge provenance from metadata before reading the content, not after.** Well-written marketing outranks a badly formatted primary source on style alone.

### Community and lived-experience sources

The position below is the author's stated reasoning, not evidence. No study compares community reports with curated expert lists, and two independent research runs confirmed the gap. The reasoning: aggregated community reports resist commercial capture better than a single loud blogger or a marketed "best of" list, and for questions academic literature has never touched, they are often the only real evidence available.

Apply it this way:

- **Valid as evidence** where no academic literature exists, or where the question is about lived practice: does this product hold up, is this neighbourhood any good, what actually happens when you do this.
- **Never as evidence** for medical, pharmacological, or safety-critical questions. Lead generation only.
- **Always labelled as anecdote**, never presented as a study.
- **Prefer moderated communities** that require sources over general ones.
- **Check the known failure modes** before relying on agreement: herding, meaning once people see existing votes their contributions stop adding independent information; astroturfing and review fraud; popularity bias; and the platform's demographic skew.

The failure to avoid runs both directions: treating a forum thread as science, and refusing forum evidence on a question science has never studied.

---

## PHASE 2: FAN OUT

Spawn sub-agents per the tier table, in parallel, in a single message.

Each sub-agent gets: one sub-question, its source routing, a hard cap on searches and fetches, and this output contract:

> Return a compressed brief, maximum 900 words. Do not dump raw page text or long quotes. Every quantitative claim carries a citation with title, first author, identifier or venue, year, and link. Flag anything you could not verify as "unverified" rather than reporting it as fact. State plainly what you could not find. An honest gap beats a confident guess.

Sub-agents run on a cheaper model than the orchestrator where the platform allows it. Reserve the expensive model for planning and synthesis.

**Do not use browser automation for research.** Web search and page fetching cover arXiv, PubMed, journals, government sites, and most news. A browser is the exception handler for pages that need JavaScript to render, login-gated content, and sites that block fetching.

### Checkpoint (Deep tier only)

After fan-out, before synthesis, stop. Show the user the findings, what surprised you, what contradicts what, and the decisions the synthesis will turn on. Gathering is cheap and synthesis is where the spend goes, so this is where an approval is worth asking for.

---

## PHASE 3: VERIFY

Run before synthesis, on Standard and Deep.

**Why this is not optional.** Across 14 models, citation links worked more than 94% of the time and were topically relevant more than 80% of the time, but were factually accurate to what the source actually said only 39% to 77% of the time (Onweller et al., "Cited but Not Verified", arXiv:2605.06635). A report can pass inspection and still misstate its sources. This skill has caught it in its own construction twice: once in a cross-validation run that returned four misattributed or over-generalised claims, and again when a verification pass on this published version fixed three citation problems carried over from the private draft (see `CHANGELOG.md`).

**What to verify.** Not every sentence. Verify claims that carry a number, and claims doing real load-bearing work in the conclusion.

**How.** Spawn a separate verification sub-agent. Give it the specific claims. Its job is to open the primary source and confirm or correct, not to gather anything new. Instruct it to be blunt and tell it that finding errors is success. Also have it confirm each identifier resolves to a real paper with the claimed title, because fabricated identifiers are exactly what this pass exists to catch.

### Check for retractions

Have the same sub-agent check every cited paper carrying a Digital Object Identifier (DOI) or an arXiv identifier against OpenAlex or Semantic Scholar for a retraction or an expression of concern, and report any hit as a correction. Both are free and need no key.

**Why this cannot be folded into the check above.** A retracted paper still says exactly what the report claims it says. Opening it, reading it, and confirming the quote all pass cleanly, and the finding is still dead. This is the one failure the rest of Phase 3 is structurally unable to see, because every other check asks whether the report represents the source faithfully and this one asks whether the source is still standing.

More than 10,000 research papers were retracted in 2023 alone (Nature news, December 2023), and retracted work keeps being cited for years afterwards, since the citation was made before the withdrawal and nobody goes back.

### Count independent sources, do not just check for echo

Where several sources agree, work out whether they are independent or all trace back to one origin: the same wire story rewritten, the same press release reprinted, the same preprint summarised five times.

**Return this as a number, not a reassurance.** For each load-bearing claim, state how many independent sources support it after collapsing duplicates, and name the clusters you collapsed.

Three tells, in rough order of how often they bite:

- Two sources sharing most of their wording, or one obviously rewritten from the other
- Wire service markers near the top of the text: PR Newswire, Business Wire, GlobeNewswire, Reuters, Associated Press
- Several sources all citing one upstream paper or dataset without adding evidence of their own

**Why a count rather than a check.** In a Standard run reading eight to twelve sources fully, three copies of one wire story is a quarter of the evidence and reads on the page as independent confirmation. An instruction to "check for echo" produces nothing whose absence can be noticed; a count does. This matters more each year as model-generated content accumulates on the web and gets cited back.

---

## PHASE 4: SYNTHESIZE AND DELIVER

Synthesis reads the briefs and the verification results. Never raw sources.

Structure the output as:

- **What the evidence supports**, graded high, medium, or low confidence, each with a citation
- **Where sources disagree**, and whether the disagreement is about interpretation or about evidence
- **What nobody has studied**, stated plainly. Gaps are findings
- **What this means for the decision** that prompted the run

Grade honestly. Distinguish peer reviewed from preprint from vendor-reported from anecdote. Where a claim rests on one unreviewed study, say so in the same sentence as the claim, not in a footnote.

**Never soften a finding because it contradicts what the user expected.**

**Output**: Scan answers in chat. Standard and Deep write a markdown file named `YYYY-MM-DD-[topic-slug]-research.md` to the user's working folder, plus a short summary in chat.

**Close with a one line cost note**: tier used, sub-agents spawned, approximate tokens consumed. This builds the user's sense of what each tier actually costs.

---

## WHEN NOT TO USE THIS

Casual lookups get plain answers. "What is X", "look this up", "who is Y", "what time is it in Tokyo" are not research runs. Auto-firing on those is how the token problem comes back.

Offer the skill when a question clearly needs it, but never start without the user saying yes.

---

## CUSTOMIZING

This skill is meant to be forked. The common changes:

- **Save Deep runs somewhere durable.** A Deep run is expensive enough that losing it is the worst outcome for the budget. If you keep a notes app or knowledge base Claude can reach, add a line to Phase 4 telling it to file Deep tier reports there too.
- **Add your own domains** to the source routing table, with the primary sources you trust in your field.
- **Add your house style** (question format, banned punctuation, how to define acronyms) as a short list under Phase 4.
- **Tune the tier table** once the cost notes show you what each tier actually costs you.

---

## CREDITS

The coverage matrix, the minimum count of adversarial searches, the independent source count, and the retraction check were adapted in September 2026 after a head to head against **Hyperresearch** by Jordan Gibbs (github.com/jordan-gibbs/hyperresearch, MIT licence), an open source harness that turns Claude Code into a much heavier research pipeline. The Scan-first ladder is original to this skill.

---

## EVIDENCE GRADES FOR THIS SKILL'S OWN CLAIMS

Verified against primary sources: ReWOO's efficiency figures; Anthropic's 4x, 15x, 80%, and 90.2% figures; the NoLiMa and Lost in the Middle degradation results; the GSM8K self-correction result; BrowseComp-Plus retrieval accuracy and cost; the citation accuracy range; the citation expansion recall figures; the ELEPHANT framing figures.

Indicative but not settled, treat as a working assumption: optimal document counts and where returns flatten; SourceBench's metric framework; AuthorityBench's authority finding; the value of a general web fallback.

Reasoned rather than measured, and labelled as such where they appear: the Scan-first ladder; the coverage matrix; the adversarial search minimums; counting independent sources rather than checking for echo. The case for each is written next to it, and none rests on a benchmark.

Known to have no evidence either way: community sources versus curated expert lists. That one is stated reasoning, and it is labelled as such wherever it is applied.
