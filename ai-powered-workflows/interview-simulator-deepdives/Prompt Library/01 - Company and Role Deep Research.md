>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# 01: Company and Role Deep Research

This is the first research pass and the widest. It answers four questions: what this company does, what this job is, where you honestly fit, and what they are likely to make you solve in the room.

Run it in a deep research tool: Claude with research or web search enabled, ChatGPT with deep research, Perplexity, Gemini, or whatever you already pay for. It takes five minutes to fill in and ten to thirty minutes to run. You will spend another fifteen minutes editing the output, because the first draft of any research contains confident sentences with nothing behind them and your job is to find them.

The output becomes `Company and Role Brief.md` in your round folder, feeding the simulator's world model and about half of your cheat sheet.

---

# When to run this

Run this first, before the interviewer research and before any story card. Everything downstream depends on knowing what the company sells and what the role owns. Run it once per company, not once per round: company facts do not change between your recruiter screen and your final panel, so later rounds reuse this file and add to it. If you interviewed here within the last six months, update the old brief instead of starting over.

---

# The prompt

Replace every bracketed placeholder. Do not delete the instructions about citation and the verified versus inferred split: those are what make the output usable.

```
You are a research analyst preparing me for a job interview. Accuracy matters more than completeness. I would rather have six sourced facts than twenty confident sentences.

CONTEXT
Company: [COMPANY]
Role title: [ROLE TITLE]
Level: [LEVEL, for example senior individual contributor, manager, director]
Job posting: [PASTE THE JOB DESCRIPTION IN FULL]
Location and work model: [LOCATION, REMOTE / HYBRID / ONSITE]

ABOUT ME
Current title: [YOUR CURRENT TITLE]
Background in three sentences: [YOUR BACKGROUND]
What I think my strongest match to this role is: [YOUR STRONGEST MATCH]
What I think my biggest gap is: [YOUR BIGGEST GAP]

Be blunt with me about fit. A flattering assessment is worthless to me. If my gap is disqualifying, say so and tell me what would compensate for it.

RULES THAT APPLY TO THE ENTIRE OUTPUT
1. Every factual claim carries an inline source link. No link, no claim.
2. Split everything into two clearly labelled categories:
   VERIFIED: I found this stated in a source. Give the link and the date of the source.
   INFERRED: I am reasoning from evidence. Show the reasoning chain and name the evidence it rests on.
   Never blend the two into one narrative paragraph.
3. If you searched for something and found nothing, write "searched, not found" and say what you searched. Do not fill the gap with a plausible guess.
4. Do not invent numbers, funding rounds, customer counts, or product names. If a number appears in a source, quote it and link it. If it does not, say so.
5. Prefer primary sources: the company's own site, engineering blog, filings, press releases, product documentation, and job postings. Use news coverage second. Use aggregator and career-advice sites last, and label them as low confidence.

DELIVER THESE NINE SECTIONS IN THIS ORDER

1. WHAT THE COMPANY ACTUALLY DOES AND HOW IT MAKES MONEY
Plain description in under two hundred words. Who pays them, for what, how often, and roughly at what scale if that is public. Name the business model explicitly (subscription, transaction fee, marketplace take rate, licence, services, advertising, or a mix). If revenue mix is not public, say so.

2. THE PRODUCT SURFACE RELEVANT TO THIS ROLE
Not the whole product catalogue. The specific surface this role touches: the users, the workflow, the adjacent systems, and the metrics that surface is probably judged on. If the product is self-serve, give me the exact steps a new user takes so I can go try it myself.

3. THEIR OWN VOCABULARY
This is important and often skipped. List ten to fifteen terms the company uses for its own core concepts, exactly as they spell them, each with the source where they use it and a short definition. Include internal-sounding names for teams, tiers, customer segments, product lines, and processes. Flag any term where their usage differs from industry-standard usage, because using the industry word when they use a house word marks me as an outsider.

4. RECENT PUBLIC MOVES, LAST EIGHTEEN MONTHS
Funding, acquisitions, launches and sunsets, pricing changes, layoffs or hiring surges, executive arrivals and departures, regulatory or legal events, notable outages. Reverse chronological, each dated and linked. Say plainly if the last eighteen months look quiet.

5. COMPETITIVE SET AND HONEST WEAKNESSES
Three to five real competitors with one line on how each one differs. Then the uncomfortable part: where this company is genuinely behind, what customers complain about in public reviews and forums, and what structural problem the person in this role would inherit. Cite the complaints; do not editorialise.

6. THE JOB DESCRIPTION DECODED
Go through the posting responsibility line by line. For each line, tell me what it means operationally: what the person would do in a normal week, who they would need to influence, and what would make it hard. Flag lines that read like the role is a rewrite of an existing failed role, a backfill, or a newly created scope. Flag any requirement that looks like a hard filter versus a wish.

7. HONEST FIT ASSESSMENT
Given my background above, score my fit against the posting's real requirements. Give me: three places I am genuinely strong and the evidence from my background that proves it, two places I am thin and what a hiring panel would probe there, and one place I am likely to be rejected on unless I address it directly. For each gap, give me the specific compensating argument I could make and tell me whether it is credible or a stretch.

8. THREE REALISTIC CASE OR SCENARIO PROMPTS
Write three prompts a candidate for this exact role and level could plausibly be given, grounded in the company's actual product and actual problems, not generic ones. For each: the prompt as an interviewer would say it, what it is really testing, what a strong answer covers (five to seven bullets), and the most common way candidates fail it.

9. CONFIDENCE AND GAPS
Close with a short note: which sections you are confident in and why, which sections are thin, what you searched for and could not find, and the three questions I should ask a human (recruiter or contact) because no public source can answer them.
```

---

# What good output looks like

Reject the output and re-ask if any of this is true. A blended narrative where you cannot tell sourced fact from inference. Claims without links, especially numbers. A vocabulary section full of generic industry terms rather than the company's own words. A fit assessment that calls you a strong candidate without naming a single gap. Case prompts that would work for any company in the sector, which means the tool did not read the product. Silence about what it failed to find.

The re-ask is usually one line: "Sections three, seven, and eight are not company-specific. Redo them using only the company's own site, documentation, and blog, and cite each term or claim."

---

# What to do with the output

Save it as `Company and Role Brief.md` in your round folder, next to `_STATE.md`. Then do three things by hand. Move every unsourced claim into a **Do not assert** section at the bottom with a safe substitute phrasing beside it, so you never say a made-up fact out loud in a room. Copy the vocabulary list into your cheat sheet: mirroring their words is the cheapest credibility you will ever buy. Carry the three case prompts from section eight into the simulator as seed material for a product or case round.

The load-bearing claims also get pasted into `04 - Cross-Validation and Reconciliation` for the second-tool check.

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

If you use or adapt this guide, please include:

Based on "01: Company and Role Deep Research," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
