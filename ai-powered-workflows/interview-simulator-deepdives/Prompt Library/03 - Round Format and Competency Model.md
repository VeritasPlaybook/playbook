>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# 03: Round Format and Competency Model

The first two prompts research the company and the people. This one researches the process: how this company runs interviews for this level and function, what shape the loop takes, and above all what the panel is scoring you against.

That last part is why this prompt exists. Most interview panels use a scorecard. You almost never see it, but you can usually reconstruct it from the company's published values or leadership model, the job posting's requirements, and the norms of the function. A reconstructed scorecard turns preparation from "practise answering questions" into "make sure I have evidence for all nine things they will tick."

Run it in a deep research tool. Ten to twenty minutes. The output becomes the competency section of `Company and Role Brief.md` and the scoring rubric inside your simulator.

---

# When to run this

Run it after prompt 01, before or in parallel with prompt 02. Run it once per company and level, then reuse it across every round in the loop, adding a note per round on which competencies that round is likely to weight. If the company publishes a values framework, a leadership model, or an engineering career ladder, this prompt is high value. If it is a fifteen-person startup with no published process, run it anyway but expect mostly inference, and lean harder on prompt 05 to get the format from a human.

---

# The prompt

```
You are a research analyst. I need to understand how this company actually runs its interview process for this level and function, and then reconstruct the scorecard the panel is likely using.

CONTEXT
Company: [COMPANY]
Role title: [ROLE TITLE]
Level: [LEVEL]
Function: [FUNCTION, for example product management, backend engineering, data science, sales]
Round I am preparing for: [ROUND NAME AS THE RECRUITER DESCRIBED IT]
Round length and format as I understand it: [LENGTH, LIVE OR TAKE HOME, PANEL OR ONE ON ONE]
Job posting: [PASTE THE JOB DESCRIPTION]

WHAT I CURRENTLY BELIEVE ABOUT THE PROCESS (refute this if it is wrong)
1. I believe the loop is: [YOUR BELIEF ABOUT THE FULL LOOP]
2. I believe this round is assessed on: [YOUR BELIEF]
3. I believe the decision this round makes is: [SCREEN OUT / DEEP ASSESSMENT / FINAL APPROVAL]
Treat these as hypotheses to test, not as background facts. If public evidence contradicts any of them, say so directly and show the evidence. If you find nothing either way, say "no evidence found, your belief is untested" rather than agreeing.

RULES
1. Cite every factual claim with a link and a date.
2. Separate VERIFIED (sourced) from INFERRED (reasoned, with the reasoning shown). Never blend them.
3. Candidate-reported information from review sites, forums, and social posts is useful but low reliability. Label it CANDIDATE REPORTED, note how old it is, and note when reports disagree with each other. Interview processes change, so a report older than two years should be marked stale.
4. If you cannot find something, write "searched, not found" plus what you searched. Do not invent a plausible loop structure and present it as fact.

DELIVER THESE SIX SECTIONS

1. PUBLISHED PROCESS
Anything the company says about its own hiring: careers page descriptions of the interview process, recruiter blog posts, engineering blog posts about hiring, published rubrics or take-home policies, statements about structured interviewing. Quote and link. If there is nothing published, say so plainly.

2. VALUES, LEADERSHIP MODEL, OR COMPETENCY FRAMEWORK
If the company publishes values, principles, a leadership model, or a career ladder, reproduce the actual list with their exact wording and link the source. For each item, tell me in one line what behaviour a panel would accept as evidence of it. If there is no published framework, say so and note what the company culture pages emphasise instead.

3. CANDIDATE-REPORTED EXPERIENCE
What candidates for this or an adjacent role have publicly described: number of rounds, who they met, question types, take-home content, timing between stages, and anything about how offers or rejections were communicated. Include actual reported questions where you can find them, with the source and the date. Flag contradictions between reports. Say how many independent reports you found, because two reports is an anecdote and fifteen is a pattern.

4. LIKELY LOOP STRUCTURE
Lay out the most probable end-to-end loop for this role and level: stage by stage, who typically runs each stage, approximate length, and what decision each stage makes. Mark each stage VERIFIED or INFERRED. Then place my round inside it and tell me what the stages before and after mine imply about what mine is for. If a stage is commonly a silent screen-out, say so.

5. THE COMPETENCY MODEL (the main deliverable)
Infer the eight to ten competencies a panel would score against for this specific role, level, and function. Build them from three inputs: the published values or leadership model, the actual requirement lines in the job posting, and the standard scoring dimensions for this function and level. Do not give me generic soft skills. Every competency must be traceable to one of those three inputs, and you must name which.

Return them as a table with exactly these columns:

| Competency | What it actually tests | How a candidate demonstrates it |

Guidance for each column. Competency: their language if they have published language, otherwise plain function-standard language. What it actually tests: the underlying judgement or capability, phrased as what a skeptical panellist is trying to find out, not as a virtue. How a candidate demonstrates it: the concrete shape of an answer that satisfies it, including what kind of evidence, what level of specificity, and what scope of ownership.

After the table, rank the competencies by how heavily my specific round is likely to weight them, and say which two or three are effectively pass or fail gates at this level.

6. CONFIDENCE AND GAPS
Which parts are sourced, which are inference, what you searched for and could not find, and the specific questions I should put to the recruiter because no public source can answer them.
```

---

# What good output looks like

The competency table is the test. Reject it if the competencies are generic virtues (communication, teamwork, ownership) with no traceability to the posting or the published values. Reject it if the "how a candidate demonstrates it" column restates the competency instead of describing the shape of a satisfying answer. Reject it if candidate-reported material is presented at the same confidence as the company's own published process, or if stale reports are not dated.

A useful row looks like this. For a payments product role at the fictional Northwind Payments, the competency is "operates under regulatory constraint," what it tests is whether you can ship inside rules you cannot negotiate away without freezing or ignoring them, and a candidate demonstrates it with one specific decision where a compliance constraint changed the design, what was traded off, and who signed off.

---

# What to do with the output

Paste sections one through four into `Company and Role Brief.md` under a **Process** heading. The competency table goes two places: into the brief, and into your simulator as the scoring rubric, so grades come back mapped to the same dimensions the real panel uses rather than invented ones.

Then run the coverage check that makes this prompt pay off. Put the competencies down one side and your Story Bank cards across the top, and mark which story covers which competency. Every uncovered competency is either a story you still need to write or a gap to name out loud in the room. That grid is usually the most useful artifact in the kit.

Any process claim from a single candidate report is one to test in `04 - Cross-Validation and Reconciliation` or to ask the recruiter about in `05 - Recruiter Intake`.

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

Based on "03: Round Format and Competency Model," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
