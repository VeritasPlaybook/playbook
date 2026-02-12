>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

For Table of Contents, click **Outline** button on the right ----------------------------------------------------------------------------------------------^

# What this is

**The problem:** Automated AI research tools (Perplexity Deep Research, ChatGPT o3, Claude Max) are fast but opaque black boxes. You get an answer in 10 minutes, but you don't see what contradictions they smoothed over, which sources are weak, or what they missed. For high-stakes decisions—investment research, product strategy, academic work, major purchases—that's not good enough.

**The solution**: This workflow implements MIT's Recursive Language Model (RLM) principles manually: decompose complex questions, gather evidence in parallel, verify before synthesizing, and use the right AI model for each task. You trade speed (60–90 min vs 10 min) for transparency and control. You'll know exactly what evidence supports each claim, where sources disagree, and what remains uncertain.

**Who this is for:** People doing research where they'll be questioned on their sources and reasoning. Not for "good enough" exploratory work—use automated tools for that. Use this when stakes are high, sources will disagree, or you need to defend your conclusions.

---
# Setup (5 minutes)

**What you need:**

- AI platform with multiple models: Perplexity Pro ($20/mo), ChatGPT Plus, Claude Projects, or API access    
- Fast retrieval model (Gemini Pro, GPT-4o mini, Claude Haiku)    
- Strong reasoning model (Claude Sonnet 4.5, o1, DeepSeek-R1)    
- Markdown note system (Notion, Obsidian, Google Docs)    

**Create your Master Document:**

```
# [Project Name] - Research

## Research Objective
[Fill after Phase 1]

## Sub-Questions (Priority Order)
[Fill in Phase 1]

## Phase 2: Evidence Collected
[Phase 2 findings]

## Phase 4: Quality Check
[Phase 4 verification]

## Phase 5: Final Report
[Phase 5 output]

## Sources & Citations
[All sources]
```
---
# Phase 1: Decompose Into 6–8 Sub-Questions

**Model:** Reasoning (Sonnet 4.5 Thinking, o1, DeepSeek-R1)  
**Key move:** Break your vague question into specific, answerable sub-questions with clear dependencies. Don't start searching randomly—map first, execute second.

## Prompt Template

```
# [Project Name] - Research

## Research Objective
[Fill after Phase 1]

## Sub-Questions (Priority Order)
[Fill in Phase 1]

## Phase 2: Evidence Collected
[Phase 2 findings]

## Phase 4: Quality Check
[Phase 4 verification]

## Phase 5: Final Report
[Phase 5 output]

## Sources & Citations
[All sources]
```

**Then force critique:**

```
Critique this research plan:
1. Are there blind spots? What angles am I missing?
2. Are any sub-questions too broad or too narrow?
3. Are dependencies correctly identified?
4. Would a different structure be more effective?
5. Are there biases (e.g., only positive sources, ignoring risks)?

Provide refined version with explanations for changes.
```

**Copy refined plan into Master Document using this format:**

```

## Research Objective
[Main question]

## Sub-Questions (Priority Order)

### Sub-Question 1: [Question text]
- Info needed: [What you're looking for]
- Source types: [Where to look]
- Dependencies: None / Requires SQ[#]
- Priority: 1
- Status: ⬜ Not started

[Repeat for all 6-8 questions]
```

## Decision Check

🟢 **Proceed to Phase 2 if:**

- 6–8 sub-questions, each specific and answerable    
- Dependencies clear (know which to research first)    
- Can explain why each question matters    

🟡 **Refine if:**

- More than 10 questions (too granular—merge)    
- Questions overlap significantly (consolidate)    
- Not sure how to search for answers (make more specific)    

🔴 **Start over if:**

- Sub-questions don't answer your objective    
- Objective itself is unclear    
- Circular dependencies (Q3 needs Q5, which needs Q3)

---
# Phase 2: Collect 30–50 Sources in Parallel 

**Model:** Fast retrieval (Gemini Pro, Perplexity Search, ChatGPT w/ browsing)  
**Key move:** Launch 3–4 searches in separate tabs simultaneously. While one runs, copy results from another. Parallelization turns a 2-hour sequential task into 30–45 minutes.
## Prompt Template (one per sub-question)

```
Research Sub-Question: [Exact sub-question from Phase 1]

Context from planning:
- Type of information needed: [From your Phase 1 plan]
- Preferred sources: [From your Phase 1 plan]
- Geographic/temporal scope: [If applicable, or "no constraints"]

Task: Find 5-7 authoritative sources that answer this question

For each source provide:
1. Full citation (Title, Author, Publication/Organization, Date, URL)
2. Key findings (3-5 bullet points of relevant facts/data)
3. Direct quotes or data points (with page numbers if PDFs)
4. Credibility assessment (peer-reviewed / industry expert / news outlet / company filing / government data)
5. Relevance score (High/Medium/Low for answering our specific question)

Prioritize:
- Recency (prefer sources from [date range, e.g., "2024-2026" or "last 2 years"])
- Authority (established organizations, credentialed experts, primary sources)
- Specificity (direct answers over tangential mentions)

Output format: Provide results in markdown using this exact structure so I can copy-paste into my Master Document:

### Sub-Question [#]: [Question text]
Status: ✅ Search complete

#### Source 1: [Title]
- **Citation:** [Full citation with URL]
- **Key findings:**
  - [Finding 1]
  - [Finding 2]
  - [Finding 3]
- **Best quote:** "[Direct quote]"
- **Credibility:** [Assessment]
- **Relevance:** [High/Medium/Low]

#### Source 2: [Title]
[Same format]

[Continue for 5-7 sources]

Search web for current information.
```

**Execution strategy:**

1. Start with high-priority, independent questions (no dependencies)    
2. Launch 3–4 searches in separate tabs    
3. Copy first completed result to Master Document while others run    
4. Don't start dependent questions until you've reviewed prerequisite findings    

**Optional but recommended:** After every 2–3 sub-questions, run quick verification to catch gaps early instead of after all 40+ sources.

## Decision Check

🟢 **Proceed to Phase 3 if:**

- 5–7 sources per sub-question (30–50 total)    
- Most marked "High" or "Medium" relevance    
- Complete citations with working URLs    
- Multiple perspectives (not all bullish or all bearish)    

🟡 **Run targeted follow-ups if:**

- 2–3 questions only have 3–4 sources    
- Multiple questions flagged contradictions needing more sources    
- Several sources marked "Low" relevance    
- All sources same type (e.g., only news, no primary data)    

🔴 **Revisit Phase 1 if:**

- Consistently can't find 5+ sources per question    
- Search results completely off-topic    
- Core objective changed based on what you learned

---
# Phase 3: Deep Dive on Complex Sub-Questions

**Model:** Reasoning (Sonnet 4.5 Thinking, o1, DeepSeek-R1)  
**Key move:** Only 2–3 sub-questions need deep analysis—the ones where sources contradict or require synthesis. Don't deep-dive everything; flag complexity in Phase 2, resolve in Phase 3.

**A sub-question needs deep dive if:**

- ✓ Sources significantly contradict each other    
- ✓ Requires synthesis across multiple sources    
- ✓ Information quality questionable    
- ✓ Unexpected complexity emerged    
- ✓ Critical context missing    

## Prompt Template
```
Context: [Your overall research objective]

Sub-question requiring deep analysis: [Specific question]

Sources gathered in Phase 2:
[Paste all findings from Phase 2 for this sub-question—include sources, quotes, key findings, credibility assessments]

Task: Perform analytical synthesis

1. **Gap Analysis:**
   - What critical information is still missing?
   - Where do sources directly contradict?
   - What claims lack sufficient evidence?
   - What additional context needed to interpret properly?

2. **Source Quality Assessment:**
   - Which sources most credible and why?
   - Methodological issues with any studies/reports?
   - Obvious bias or conflicts of interest?
   - How current is the data (anything outdated)?

3. **Preliminary Synthesis:**
   - What can we conclude with high confidence?
   - What remains uncertain or contested?
   - What patterns emerge across sources?
   - Are contradictions reconcilable or fundamental?

4. **Additional Search Strategy:**
   - What specific searches would resolve most important gaps/contradictions?
   - What alternative sources should we explore?
   - Primary sources (filings, gov data) to consult?

Show reasoning step-by-step. Assign confidence levels (High/Medium/Low) to each conclusion.
```

**Then run 1–2 targeted follow-up searches** based on gap analysis. Use fast retrieval model with laser-focused queries for specific missing pieces.

**Update Master Document:**

```
#### Deep Dive Analysis:

**Key Contradictions:**
- [Contradiction 1 and explanation]

**Confidence Assessments:**
- **High confidence:** [Claims with strong evidence] | Sources: [#, #, #]
- **Medium confidence:** [Moderate evidence/minor contradictions] | Caveat: [What's uncertain]
- **Low confidence:** [Weak/contradictory evidence] | Issue: [Why unreliable]

**Remaining Gaps:**
- [Gap 1 - Critical/Nice-to-have]
```

## Decision Check

🟢 **Proceed to Phase 4 if:**

- Major contradictions explained or resolved    
- Confidence assessments documented    
- Remaining gaps "nice-to-have" not "critical"    

🟡 **More searches if:**

- Critical gaps remain (can't answer sub-question at all)    
- New contradictions need one more source    

🔴 **Revisit Phase 1 if:**

- Fundamentally wrong question (uncovered after deep analysis)    
- Need to reframe entirely

---
# Phase 4: Cross-Verify Everything

**Model:** Reasoning (Sonnet 4.5, o1, DeepSeek-R1) with long context  
**Key move:** Holistic verification across all findings before writing. This catches single-source claims, contradictions you missed, and tells you if you're 90% done or need more research.

## Prompt Template

```
I've completed evidence gathering across [#] sub-questions for this research objective:

[State your research objective]

Here are all findings from Phases 2-3:

[Paste everything from Master Document: all sub-questions, all sources, all deep dive analyses]

Task: Comprehensive quality check

Analyze holistically and provide:

1. **Single-Source Risk:**
   - Which claims rely on only one source?
   - Which of these are critical vs nice-to-have?
   - Should we find corroboration?

2. **Contradictions:**
   - Where do sources disagree (that I haven't already flagged)?
   - Are these reconcilable or fundamental disagreements?
   - Which contradictions matter most?

3. **Evidence Quality:**
   - Strongest evidence (primary sources, peer-reviewed, multiple corroboration)
   - Weakest evidence (opinion, outdated, questionable methodology)
   - Any sources I'm over-relying on?

4. **Coverage Assessment:**
   - What aspects of my objective are well-covered?
   - What's under-researched?
   - Any blind spots or perspectives missing?

5. **Bias Check:**
   - Do sources skew in one direction (all bullish/bearish, all from one industry segment)?
   - Am I missing contrarian or alternative viewpoints?

6. **Gaps:**
   - What would strengthen this research most?
   - What's critical vs nice-to-have?

7. **Completeness Rating:**
   - On a scale of 1-100%, how complete is this research for answering the objective?
   - What would get us to 90%+ if we're not there?

Be ruthlessly honest. I want to know weaknesses before I write the report.
```

## Decision Check

🟢 **Proceed to Phase 5 if:**

- Completeness rating 85–90%+    
- Critical gaps addressed or documented as unknowable    
- Major contradictions resolved or acknowledged    
- Confident you can write defensible report    

🟡 **Run 2–3 more searches if:**

- Completeness 70–84%    
- 1–2 critical single-source claims need corroboration    
- One major perspective missing    

🔴 **Major revision needed if:**

- Completeness <70%    
- Fundamental gaps in multiple sub-questions    
- Realized you're answering wrong question

---
# Phase 5: Draft Report Section-by-Section

**Model:** Reasoning (Sonnet 4.5, o1, DeepSeek-R1)  
**Key move:** Draft section-by-section, not all at once. Maintain quality and ensure every claim traces to sources. Match confidence language to Phase 4 assessments.

## Prompt Template

```
I'm writing a research report. Here's my objective and all findings:

**Research Objective:** [Your question]

**All Evidence:**
[Paste Master Document: sub-questions, sources, deep dives, Phase 4 verification]

Task: Draft the report structure and first section

1. First, propose a report structure with:
   - Section headings (4-6 sections that logically answer the objective)
   - What each section will cover
   - Recommended order

2. Then draft Section 1: [Section name]

For each section:
- Open with key finding (1-2 sentences)
- Support with evidence from sources
- Use proper inline citations [Source #]
- Match confidence to evidence:
  - High confidence: "X is Y" or "Data shows X"
  - Medium confidence: "Evidence suggests X" or "X appears to be Y"
  - Low confidence: "Limited evidence indicates X" or "Some sources suggest X"
- Acknowledge contradictions/uncertainty where they exist
- 300-500 words per section

After I approve structure, I'll ask you to draft remaining sections one at a time.
```

Then for each subsequent section:

```
Draft Section [#]: [Section name]

Use same guidelines: key finding, evidence, citations, confidence-matched language, 300-500 words.
```

**What you're doing:** Giving the model everything it needs to write one focused section - the findings, the quality assessment, the structure requirements. This maintains quality and keeps you in control.

**After all sections drafted:**

```
Now draft Executive Summary (write this last)

- 150-250 words
- Direct answer to research objective
- 3-5 key findings with confidence levels
- Major caveats or limitations
- Don't introduce new information not in main sections
```

**Copy complete report into Master Document under "Phase 5: Final Report"**

## Decision Check

🟢 **Proceed to Phase 6 if:**

- Report flows logically objective to conclusion    
- Every factual claim properly cited    
- Confidence language matches evidence quality    
- Contradictions/uncertainty acknowledged    

🟡 **Revise if:**

- Logical gaps between sections    
- Missing citations for key claims    
- Overstating confidence on weak evidence

---
# Phase 6: Adversarial Review

**Model:** DIFFERENT reasoning model than Phase 5 (fresh perspective)  
**Key move:** Use a new model to ruthlessly critique your own work. This separates thoughtful research from AI-generated content. You're too close to see gaps.

## Prompt Template

```
You are an adversarial reviewer. Your job is to find flaws, not be supportive.

Here's a research report I wrote:

[Paste complete Phase 5 report]

Task: Ruthless critique

1. **Logical Flaws:**
   - Where does reasoning not hold up?
   - Where are conclusions stronger than evidence supports?
   - Any circular reasoning or unsupported leaps?

2. **Evidence Issues:**
   - Where am I over-relying on weak sources?
   - Where are citations missing or vague?
   - Where did I cherry-pick evidence that fits conclusion?

3. **Missing Perspectives:**
   - What counter-arguments am I ignoring?
   - What alternative interpretations exist?
   - Who would disagree with this analysis and why?

4. **Structure & Clarity:**
   - Where is the argument unclear or disorganized?
   - What would strengthen the narrative flow?
   - Where am I being unnecessarily verbose or vague?

5. **Blind Spots:**
   - What did I fail to consider entirely?
   - What assumptions am I making without stating them?
   - What risks or limitations am I downplaying?

For each issue, rate severity:
- **Critical:** Undermines core argument or credibility
- **Important:** Weakens specific claims or sections
- **Minor:** Polish issues that don't affect conclusions

Be harsh. I need to know real problems before sharing this.
```

Review the critique, then discuss disagreements:

```
I disagree with [issue #X] for the following reason:

[Your explanation]

Is this a valid counterargument, or am I being defensive?
```

**Export final critique with severity ratings for Phase 7**

## Decision Check

🟢 **Proceed to Phase 7 if:**

- You have complete critique with severity ratings    
- Ready to address valid criticisms    

🟡 **Run another round if:**

- Critique revealed fundamental issues    
- Need model to elaborate on specific critiques
 
---
# Phase 7: Incorporate Critiques & Finalize

**Model:** Same as Phase 5 (original draft model)  
**Key move:** Address Critical and Important issues surgically. Don't rewrite everything; revise strategically. Update Executive Summary last.

## Prompt Template

```
Here's my research report and the adversarial critique I received:

**Original Report:**
[Paste Phase 5 report]

**Critique Received:**
[Paste Phase 6 critique with severity ratings]

Task: Revise to address valid criticisms

Priority:
1. Address all **Critical** issues first
2. Then **Important** issues
3. Skip or quickly fix **Minor** issues if time-limited

Guidelines:
- Revise surgically (fix specific issues, don't rewrite everything)
- Integrate caveats naturally (not tacked-on disclaimers)
- Strengthen weak claims with better evidence or hedge language
- Add missing perspectives where they matter
- Maintain core argument unless critique proves it wrong

Start with Critical issues. Show me proposed revisions one at a time.
```

After all revisions:

```
Update Executive Summary to reflect revisions made.
```

**Why one at a time:** Trying to fix 5 issues simultaneously leads to incoherent output. Fix, verify, move to next.
**Final steps:**

1. Copy revised report into Master Document    
2. Do final coherence check (read start to finish)    
3. Archive all threads and sources used    
4. Export final report    

## Decision Check

🟢 **Ship it if:**

- Critical and Important issues addressed    
- Executive Summary updated    
- Report defensible and well-cited    

🟡 **One more pass if:**

- Revisions introduced new inconsistencies    
- Executive Summary doesn't match revised body    

---

## What You've Built

You now have:

- **30–50 authoritative sources** organized by sub-question    
- **Documented evidence quality** (high/medium/low confidence for each claim)    
- **Resolved contradictions** with explanations    
- **Adversarially tested** report that stands up to scrutiny    
- **Complete audit trail** (every claim traces to sources)    

**Time invested:**

- First time: 2–4 hours (learning the system)    
- After practice: 60–90 minutes for complex research    
- vs automated tools: 10–15 minutes (but opaque)    

**Trade-off:** You sacrificed speed for transparency, control, and defensibility. For high-stakes decisions, it's worth it.

---

## When to Adapt

- **Simple research:** Skip Phase 3 (no deep dives needed) and Phase 6 (no adversarial review)    
- **Time-limited:** Do Phase 4 as rolling verification during Phase 2 instead of separate phase    
- **Low-stakes:** Use automated tools instead; this workflow is overkill    

**For full methodology with examples, troubleshooting, platform-specific tips, and RLM research background:**

→ [Complete Guide on GitHub](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/A%20Practical%20RLM-Inspired%20Workflow%20for%20Deep%20Research%20with%20AI.md#appendix-a-rlm-research-background)

---

# License & Attribution

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/).

**You are free to:**
- **Share** — Copy and redistribute the material in any medium or format
- **Adapt** — Remix, transform, and build upon the material for any purpose, even commercially

**Under the following terms:**
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

## How to Attribute

If you use or adapt this guide, please include:

Based on "An AI-Powered Resume Workflow" by VeritasPlaybook
Original: [https://github.com/VeritasPlaybook/playbook/blob/main/career-workflow/resume-workflow/An%20AI-Powered%20Resume%20Workflow.md](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Complete%20Manual%20Deep%20Research%20Guide%20for%20Perplexity%20Pro.md)
License: CC BY 4.0

# Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- 💼 [LinkedIn](https://www.linkedin.com/in/malocilja/?view=public)
- 🐙 [Veritas Playbook - GitHub](https://github.com/VeritasPlaybook/playbook)
- 📊 [Investment Research](https://github.com/Veritas-Research/investment-research)

---

*If you found this valuable, star ⭐ the repo to help others find it.*