>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

For Table of Contents, click **Outline** button on the right ----------------------------------------------------------------------------------------------^

# Intro

Perplexity did something recently that is just… perplexing to me; and regardless of where you sit on the debate; losing close to unlimited deep research has been a huge blow for a lot of us. It’s been a huge blow to me; so much so that I have to go back and rewrite a couple of guides that I recently put together, which relied on this flow.

In fact, some of my best recent published worked fully utilized Deep Research as a core component of my workflow. For those who are curious; that is:

- [AI Powered Resume Workflow](https://github.com/VeritasPlaybook/playbook/blob/main/career-workflow/resume-workflow/An%20AI-Powered%20Resume%20Workflow.md)
- [The Memory Play - AI Memory Investment Thesis](https://github.com/Veritas-Research/investment-research/blob/main/theses/The%20Memory%20Play%20-%20Why%20AI's%20Future%20Runs%20on%20HBM%2C%20Not%20Hype.md)

Why did Perplexity do this? Probably cost and profit. Agentic iteration is expensive, and with tech companies now focusing on profitability (rightfully so), the age of subsidized near-unlimited power is ending. It was good while it lasted.

What frustrates me most isn't the change itself, it's the lack of transparency around query limits. I'm flying blind now.

Instead of staying sad or getting angry, I did what any good PM would do: I built a solution.

This is my manual deep research guide, using only Perplexity Pro and the best models available to it.

---
# Overview: The Seven-Phase System

This requires 7 major steps:

- Decomposition - breaking down the what and why; segmenting the questions and planning how to tackle
- Gather information - parallel searches
- Deep diving into gathered info
- Cross-verification and Gap analysis
- Synthesis and generation
- Adversarial Review and verification
- Incorporate Critiques & Finalize

Is this a lot of steps? Yes. Does this require way more work than it used to? Yes. Will you get same or better answers? Probably.

💡 **Why This Works:** This workflow mirrors MIT's recent research on [**Recursive Language Models**](https://arxiv.org/html/2512.24601v1), which showed massive improvements by decomposing complex queries, processing in parallel, validating, and synthesizing. We're applying that approach manually.

---
# Pre-requisites

**Tools:**

- **Perplexity Pro** (yes, I know, the irony), but we'll leverage multiple models:
	- Claude Sonnet 4.5 + Thinking
    - Gemini 3 Pro
    - ChatGPT 5.2 + Thinking
- **Notepad/Document app**
    - I use Notion and Obsidian (though exporting to Notion needs to be easier, it's actually really annoying)
    - You can also use Google Docs, which now has decent markdown support (you need to enable it in settings)

**Why three different models?** Each excels at different tasks. Sonnet for reasoning and analysis, Gemini for fast web searches, GPT for adversarial review. Using the right model for each phase dramatically improves quality and speed.

---
# Concept

Here's what we're doing and why it works.

Traditional Deep Research was essentially an AI agent running autonomously. It would break down your question, search multiple times, synthesize findings, iterate on gaps, and compile everything into a report. We're replicating that process manually, but with a crucial advantage: **you control every decision point**.

Think of it like cooking. Perplexity Deep Research was a meal kit delivered to your door, convenient but you don't learn the recipe or understand why ingredients are combined in a specific order. This workflow is learning to cook. It takes longer, but you understand the technique, can adapt it to different dishes, and eventually don't need the recipe anymore.

Here's how each phase works and why it matters:

## 1. Decomposition (Planning)

**What it does:** Transforms your vague question into 6-8 specific, answerable sub-questions with clear priorities and dependencies. This is like creating a blueprint before building a house. You can't just start hammering, you need to know what rooms you're building and in what order.

**Why it matters:** Without decomposition, you're searching randomly and hoping you cover everything. With it, you have systematic coverage and know exactly what you're looking for. This is where most research fails.

## 2a. Gather Information (Parallel Searches)

**What it does:** Runs 3-4 searches simultaneously across your sub-questions, collecting 5-7 authoritative sources for each. This is like sending multiple scouts in different directions instead of one person walking the entire perimeter. Parallelization saves massive time.

**Why it matters:** This is raw material collection. Speed matters here because you need breadth before depth. Gemini excels at fast retrieval, so we use it to gather quickly while maintaining quality.

## 2b. Deep Diving (Analytical Synthesis)

**What it does:** Takes complex sub-questions where sources contradict or require interpretation, and performs rigorous analysis to extract meaningful insights. This is moving from reading headlines to reading the full article and comparing multiple perspectives. Some questions can't be answered with quick searches, they require thinking.

**Why it matters:** This separates surface-level research from deep understanding. Not every question needs this, but the ones that do are usually your most important findings.

## 3. Cross-Verification (Quality Control)

**What it does:** Analyzes all gathered research holistically, identifies single-source claims, contradictions, evidence quality, and gaps. This is like fact-checking a news story by comparing multiple outlets and looking for what they all agree on versus where they differ.

**Why it matters:** This is your bullshit detector. AI models will confidently cite bad sources or miss contradictions. This phase catches those issues before they become conclusions. It also tells you if you're 90% done or need more research.

## 4. Synthesis (Report Generation)

**What it does:** Transforms all your research into a coherent narrative with proper structure, citations, and confidence levels for each claim. This is taking all your construction materials and actually building the house. You have the blueprint (Phase 1) and materials (Phases 2-3), now you assemble them properly.

**Why it matters:** Research isn't useful until it's communicated clearly. This phase drafts section-by-section to maintain quality and ensure every claim traces back to sources.

## 5. Adversarial Review (Red Team)

**What it does:** Uses a fresh model to ruthlessly critique your report, finding logical flaws, missing evidence, alternative interpretations, and blind spots. This is like having a colleague who disagrees with everything review your work. Annoying but invaluable. You'll go back and forth with the model until you agree on what's actually worth fixing, then export the final critique as markdown.

**Why it matters:** You're too close to your own research. You'll miss obvious gaps, over-rely on favorite sources, or state conclusions more confidently than evidence supports. GPT's fresh perspective catches what you can't see. This phase is technically optional, but it's what separates thoughtful research from AI-generated slop.

## 6. Incorporate Critiques & Finalize

**What it does:** Takes the markdown critique from Phase 5 and iteratively refines your report with Sonnet, addressing valid issues while maintaining your core arguments. This is the final polish, where you incorporate hard-won feedback and transform good research into excellent research.

**Why it matters:** The critique is useless if you don't act on it. This phase forces you to confront weaknesses, strengthen evidence, and acknowledge uncertainty where appropriate. Combined with Phase 5, this is what makes your research 99% better than the poorly generated content flooding the internet. When you're satisfied with revisions, export in whatever format you need.

---

**The key insight:** Each phase uses the AI model that's best at that specific task. Sonnet excels at reasoning and structured thinking. Gemini excels at fast web searches. GPT excels at finding flaws in your logic. By manually orchestrating these models, you get better results than any single model running autonomously, because you're making strategic decisions at every transition point.

You can stop after Phase 5 and have solid research. But Phases 5 and 6 are what transform solid research into work that stands out.

---
# How to actually do this

## Phase 1: Research Decomposition & Planning

**Model: Claude Sonnet 4.5 Thinking**

Sonnet 4.5 Thinking excels at systematic reasoning and structured decomposition. It scores 80.2% on complex reasoning benchmarks and maintains consistency across long analytical tasks. More importantly, it shows its thinking process, so you can see _how_ it's breaking down your question, not just the output. We use it for planning because bad decomposition ruins everything downstream. The main limitation: it's slower than other models, but for planning that's a feature, not a bug. You want it to think carefully here.

---
### **Step 1.1 - Create Planning Thread**

1. Open Perplexity in new browser window
2. Start fresh thread
3. Enable **Sonnet 4.5 Thinking** model
4. Name thread: "[Project Name] - Phase 1: Planning"

💡 **Pro tip:** Name your threads clearly from the start. When you're juggling 10+ threads across phases, "New Thread (7)" is useless but "SK Hynix - Phase 1: Planning" tells you exactly what you're looking at.

---
### **Step 1.2 - Initial Decomposition Prompt**

**What this prompt does:** Forces Sonnet to break your broad question into specific, searchable sub-questions with clear structure. The key is asking for dependencies and priorities, not just a list of questions. This prevents you from searching for information you can't interpret yet because you're missing foundational context.

Copy and paste this template, filling in your specifics:

```
Research Objective: [Your main question - be specific]

Context:

- Purpose: [Why you need this research - e.g., investment decision, product strategy, market analysis]
- Scope: [Geographic region, time period, industry constraints]
- Depth needed: [Surface overview vs deep analysis]
- Key stakeholders/audience: [Who will use this research]

Task: Create a comprehensive research plan

Break this into 6-8 sub-questions that together fully answer the objective. For each sub-question:

1. Specific information requirements (quantitative data, expert opinions, case studies, etc.)
2. Likely authoritative sources (academic papers, industry reports, government data, etc.)
3. Dependencies (which questions must be answered before others)
4. Search difficulty estimate (easy/moderate/hard)
5. Priority ranking (1-8, with 1 being highest priority)

Output format:

- Numbered list of sub-questions
- For each: [Information needed] | [Source types] | [Dependencies] | [Difficulty] | [Priority]
- Final section: Research sequence (order to tackle questions based on dependencies)
```

⚠️ **Common mistake:** Being too vague in "Research Objective." "Tell me about AI" is useless. "What are the key revenue drivers for AI infrastructure companies in 2026?" is specific and searchable.

---
### **Step 1.3 - Review and Refine**

**What this prompt does:** Catches planning mistakes before you waste time searching. Sonnet's first pass is usually 80% right, but it misses angles or creates sub-questions that are too broad. This forces it to critique its own work, which consistently improves output quality.

Sonnet will provide structured output. Review it and ask:

```
Critique this research plan:

1. Are there blind spots? What angles am I missing?
2. Are any sub-questions too broad or too narrow?
3. Are dependencies correctly identified?
4. Would a different question structure be more effective?
5. Are there biases in this approach?

Provide your refined version with explanations for changes.
```

💡 **What to look for in the output:** Pay attention to sub-questions that would generate 100+ sources (too broad) or only 1-2 sources (too narrow). Good sub-questions should yield 5-10 high-quality sources each.

---
### **Step 1.4 - Finalize Research Plan**

1. Copy the refined plan into a master document (Notion, Obsidian, Google Docs)
2. Create this markdown structure in your document:

```
# [Project Name] Research

## Research Objective

[Your main question]

## Sub-Questions (Priority Order)

1. [Sub-question 1]
    
    - Info needed:
    - Sources:
    - Status: ⬜ Not started
2. [Sub-question 2]
    
    - Info needed:
    - Sources:
    - Status: ⬜ Not started

[Continue for all 6-8 questions]

## Phase 2 Findings

[Leave blank for now]

## Phase 3 Analysis

[Leave blank for now]

## Phase 4 Final Report

[Leave blank for now]
```

**Why this structure matters:** The checkboxes give you progress tracking. The "Findings" sections give you a place to dump information as you gather it. Research gets chaotic fast, this keeps you organized.

📋 **Real example:** For the [SK Hynix research](https://github.com/Veritas-Research/investment-research/blob/main/theses/The%20Memory%20Play%20-%20Why%20AI's%20Future%20Runs%20on%20HBM%2C%20Not%20Hype.md#expected-returns-methodology), Sub-Q1 was "What is SK Hynix's current market position in HBM?" (foundational, priority 1, no dependencies). Sub-Q4 was "How do HBM margins compare to legacy DRAM?" (requires understanding market position first, priority 4, depends on Sub-Q1).

---
## Phase 2: Parallel Information Gathering

**Model: Gemini 3 Pro**

Why Gemini?

Gemini 3 Pro is optimized for speed and breadth in web retrieval. It's significantly faster than Sonnet at pulling sources across news, industry reports, academic papers, and blogs, which is exactly what you need in this phase. You're gathering raw material, not analyzing it yet. Think of this as casting a wide net, you'll sort the fish later. The main limitation is that Gemini sometimes "smooths over" contradictions or paraphrases too loosely, but that's fine here because you'll verify everything in Phase 3. For initial gathering where you need 30-50 sources quickly, Gemini's speed advantage is worth the tradeoff.

---
### **Step 2A.1 - Create Search Threads (One per Sub-Question)**

For each sub-question in your plan:

1. Open **new Perplexity thread**
2. Select **Gemini 3 Pro** model
3. Name thread: "[Project Name] - Sub-Q[#]: [Short description]"

**Example:** "SK Hynix Analysis - Sub-Q1: Market Position"

💡 **Pro tip:** Open 3-4 threads immediately and queue them up. While Gemini searches one question, you're copying results from another. This parallel workflow is how you compress hours of research into 45 minutes.

---

### **Step 2A.2 - Information Gathering Prompt Template**

**What this prompt does:** Transforms Gemini from a summarizer into a research assistant. By asking for sources first, then findings, then credibility assessment, you force it to show its work rather than giving you a blended answer with vague attribution. The "relevance score" prevents Gemini from padding results with tangentially related sources.

Use this structure for **each sub-question thread**:

```
Research Sub-Question: [Exact sub-question from Phase 1]

Context from planning:

- Type of information needed: [From Phase 1 plan]
- Preferred sources: [From Phase 1 plan]
- Geographic/temporal scope: [If applicable]

Task: Find 5-7 authoritative sources that answer this question

For each source provide:

1. Full citation (Title, Author, Publication/Organization, Date, URL)
2. Key findings (3-5 bullet points of relevant facts/data)
3. Direct quotes or data points (with page numbers if available)
4. Credibility assessment (peer-reviewed, industry expert, news outlet, etc.)
5. Relevance score (High/Medium/Low for answering our specific question)

Prioritize:

- Recency (prefer sources from [date range])
- Authority (established organizations, credentialed experts)
- Specificity (direct answers over tangential mentions)

Output format: Provide results in markdown format exactly as shown below. This allows me to copy-paste directly into my master document.

### Sub-Question [#]: [Question text]

Status: ✅ Initial search complete

#### Source 1: [Title]

- Citation: [Full citation]
- Key findings:
    - [Finding 1]
    - [Finding 2]
    - [Finding 3]
- Best quote: "[Direct quote]"
- Credibility: [Assessment]
- Relevance: [High/Medium/Low]

#### Source 2: [Title]

- Citation: [Full citation]
- Key findings:
    - [Finding 1]
    - [Finding 2]
    - [Finding 3]
- Best quote: "[Direct quote]"
- Credibility: [Assessment]
- Relevance: [High/Medium/Low]

[Continue this format for all 5-7 sources]

Search web for current information.
```

⚠️ **Common mistake:** Accepting Gemini's first response if it gives you a summary without clear source separation. If you're seeing "According to multiple sources..." instead of "Source 1: [Title]", stop and ask: "Provide 5-7 distinct sources with full citations before any synthesis."

📋 **Real example:** For "[What is SK Hynix's HBM market share](https://github.com/Veritas-Research/investment-research/blob/main/theses/The%20Memory%20Play%20-%20Why%20AI's%20Future%20Runs%20on%20HBM%2C%20Not%20Hype.md#expected-returns-methodology)?", good sources are analyst reports with specific numbers, earnings transcripts with revenue breakdowns, and industry data from TrendForce. Bad sources are general semiconductor news articles that mention HBM once in passing.

---
### **Step 2A.3 - Execute Parallel Searches**

**Critical:** Run 3-4 sub-question searches simultaneously in different browser tabs/windows

**Time management:**

- High priority questions: Start first
- Independent questions: Run in parallel
- Dependent questions: Wait for prerequisite data

**What "parallel" actually looks like:**

1. Launch Sub-Q1 search in Thread 1
2. While it's running, launch Sub-Q2 in Thread 2
3. While both are running, launch Sub-Q3 in Thread 3
4. By the time you launch Thread 4, Thread 1 is probably done
5. Copy Thread 1 results to master doc while Threads 2-4 finish

This is where your Phase 1 decomposition pays off. You're not "researching a topic", you're executing a queue of specific searches that you know don't depend on each other.

💡 **Dependency management:** If Sub-Q5 depends on Sub-Q1 (e.g., "How does HBM pricing compare to GDDR6?" depends on understanding what HBM actually is), don't start Sub-Q5 until you've reviewed Sub-Q1 findings. You might need to refine the question based on what you learned.

---
### **Step 2A.4 - Compile Findings**

As each Gemini thread completes:

1. Copy the formatted output directly into your master document under the appropriate sub-question
2. Quick quality scan:
    - Is the markdown formatting intact?
    - Are citations complete with working URLs?
    - Do you have 5-7 sources as requested?
3. Mark the sub-question status from ⬜ Not started to ✅ Initial search complete

💡 **Pro tip:** Don't reformat, clean up, or verify quality deeply yet. Just copy-paste and keep moving through your sub-questions. You'll do rigorous quality verification in Phase 3. Right now, speed and breadth matter more than perfection.

⚠️ **If Gemini didn't follow the format:** Go back to that thread and say "Please reformat your response using the markdown structure I specified in my prompt." Copy the corrected version.

**What your master document should look like after Phase 2A:**

Each sub-question section should have the exact structure Gemini provided:

- Sub-question header with ✅ status
- 5-7 sources with complete citation, findings, quotes, credibility, relevance
- Ready to use in Phase 3 without additional formatting

---
### **Step 2A.5 - Quick Quality Check**

After completing all sub-questions, scan your master document and ask:

**Quantity check:**

- Do you have 5-7 sources per sub-question? (30-50 total sources across all questions)
- Are all citations complete with working URLs?
- Did any Gemini threads give you fewer sources than requested? (If yes, go back and ask for more)

**Quality check:**

- Scan source credibility assessments: Are there obvious low-quality sources (random blogs, AI-generated content farms, severely outdated sources)?
- Do relevance scores make sense? (Sources marked "High relevance" should directly answer the sub-question)
- Are there sub-questions where most sources are marked "Medium" or "Low" relevance? (This suggests the sub-question might need refinement)

**Complexity check:**

- Which sub-questions have sources that directly contradict each other?
- Which sub-questions revealed unexpected complexity or nuance you didn't anticipate in Phase 1?
- Which sub-questions feel adequately covered by straightforward facts vs. which require interpretation or analysis?

Flag complex/contradictory/thin sub-questions for Phase 2B. Not every sub-question needs a deep dive. Some are straightforward fact-gathering ("When was the company founded?"). Others are analytical ("How sustainable is their competitive advantage?"). Phase 2B is for the latter.

📋 **Decision rule:** If you can answer the sub-question with high confidence just from reading the sources Gemini found, skip Phase 2B for that question. If sources disagree, if claims lack evidence, or if the question requires synthesis across multiple sources to form a coherent answer, flag it for Phase 2B.

💡 **Time management tip:** Most research projects have 2-3 sub-questions that need deep dives, not all 6-8. If you're flagging more than half your sub-questions for Phase 2B, your Phase 1 decomposition might have been too ambitious. Consider whether some sub-questions can be answered "good enough" with Phase 2A findings alone.

---
## Phase 2B: Deep Dives on Complex Sub-Questions

**Model: Sonnet 4.5 Thinking**

Why back to Sonnet?

This is where you need reasoning, not retrieval. Sonnet 4.5 Thinking excels at analytical synthesis, spotting contradictions, and assessing evidence quality. It maintains consistency over long contexts (you'll paste 5-7 sources worth of findings), and crucially, it shows its reasoning process so you can see how it's evaluating conflicting claims. Gemini would give you a smoothed-over answer, Sonnet shows you the mess and helps you think through it. The limitation is speed, but you only do deep dives on 1-3 sub-questions, not all of them, so the time cost is manageable.

---
### **Step 2B.1 - Identify Questions Needing Deep Analysis**

Review Phase 2A findings. Move to Phase 2B if:

- Sources contradict each other significantly
- Question requires analytical synthesis (not just fact-gathering)
- Initial search revealed complexity not anticipated in Phase 1
- Information quality is low or sources are questionable

**You're looking for mess.** If everything is clean, skip this step for that sub-question.

---
### **Step 2B.2 - Create Deep Analysis Threads**

For each flagged sub-question:

1. Open **new Perplexity thread**
2. Select **Sonnet 4.5 Thinking**
3. Name thread: "[Project Name] - Deep Dive: [Sub-Q#]"

💡 **Pro tip:** Even if you only have one sub-question needing deep analysis, keep it in a separate thread. Don't pollute your Phase 2A Gemini threads with Sonnet analysis. Clean thread organization = clean thinking.

---
### **Step 2B.3 - Deep Analysis Prompt Template**

**What this prompt does:** Asks Sonnet to do four things you can't easily do yourself: identify what's missing, assess source quality rigorously, synthesize with explicit confidence levels, and recommend next searches. This is analytical triage. You're not accepting Sonnet's synthesis as final, you're using it to figure out what additional research would actually move you forward.

```
Context: [Your overall research objective]

Sub-question requiring deep analysis: [The specific question]

Sources gathered so far: [Paste all findings from Phase 2A for this sub-question - include sources, quotes, data]

Task: Perform deep analytical synthesis

1. Gap Analysis:
    
    - What critical information is still missing?
    - Where do sources contradict each other?
    - What claims lack sufficient evidence?
    - What additional context is needed?
2. Source Quality Assessment:
    
    - Which sources are most credible and why?
    - Are there methodological issues with any studies/reports?
    - Do any sources show obvious bias?
3. Preliminary Synthesis:
    
    - What can we conclude with high confidence?
    - What remains uncertain or contested?
    - What patterns emerge across sources?
4. Additional Search Strategy:
    
    - What specific searches would resolve gaps/contradictions?
    - What alternative sources should we explore?
    - Are there primary sources we should consult?

Show your reasoning process step-by-step. Assign confidence levels (High/Medium/Low) to each conclusion.
```

📋 **Real example:** For "How does China's AI boom impact HBM demand?", Phase 2A sources ranged from "China will dominate AI" to "Export controls will crater Chinese demand." Sonnet's deep dive identified that the contradiction stems from different timeframes (2025 vs 2027) and different definitions of "AI chips" (training vs inference). That insight tells you to split the question into short-term and long-term dynamics.

---
### **Step 2B.4 - Execute Targeted Follow-Up Searches**

Based on Sonnet's gap analysis:

1. Return to Gemini 3 Pro (new threads)
2. Run targeted searches for identified gaps
3. Use Sonnet's recommended search strategies

**Follow-up search prompt:**

```
Targeted search based on gap analysis:

Gap identified: [Specific gap from Sonnet's analysis]

Recommended search strategy: [From Sonnet's output]

Task: Find 2-3 high-quality sources specifically addressing this gap

[Use same source documentation format as Phase 2A.2]
```

💡 **Pro tip:** Don't get stuck in infinite research loops. If Sonnet identifies 8 gaps, prioritize the 2-3 that actually matter for your research objective. Some gaps are interesting but not critical.

---
### **Step 2B.5 - Update Master Document**

Add Deep Dive findings to your master document:

```
### Sub-Question [#]: [Question] Status: ✅ Deep analysis complete

[Previous Phase 2A sources]

#### Deep Analysis Notes (Sonnet 4.5 Thinking):

- Key contradictions: [List]
- Confidence assessments:
    - High confidence: [Claims with strong evidence]
    - Medium confidence: [Claims with moderate evidence]
    - Low confidence: [Uncertain or contested claims]
- Gaps identified: [List]
- Follow-up sources: [Additional sources found]
```

**Why this matters:** Phase 3 (Cross-Verification) needs to know which claims you're confident about and which are shaky. Documenting it here prevents you from overstating weak claims in your final report.

---
## **Phase 3: Cross-Verification & Gap Analysis**

**Model: Sonnet 4.5 Thinking**

Why back to Sonnet?

This is quality control on everything you've gathered. Sonnet 4.5 Thinking excels at maintaining coherence over very long contexts (you'll paste 30-50 sources worth of findings), and it's the most reliable at spotting contradictions without hallucinating connections that don't exist. Gemini would smooth over problems, GPT would find issues but might introduce its own biases. Sonnet is methodical and conservative, which is exactly what you want when verifying evidence quality. The key advantage here is its 1M token context window, you can dump everything and it won't lose track of what source said what.

---
### **Step 3.1 - Create Master Synthesis Thread**

1. Open **new Perplexity thread**
2. Select **Sonnet 4.5 Thinking**
3. Name thread: "[Project Name] - Phase 3: Cross-Verification"

💡 **Pro tip:** This is one of the most important threads in your entire workflow. Save the URL in your master document. You'll reference this verification output constantly when writing your final report.

---
### **Step 3.2 - Compile All Research**

From your master document, create one comprehensive compilation:

```
Research Objective: [Main question]

Complete findings from Phases 2A & 2B organized by sub-question:

## Sub-Question 1: [Question]

[All sources, findings, quotes, deep analysis]

## Sub-Question 2: [Question]

[All sources, findings, quotes, deep analysis]

[Continue for all sub-questions]

Total sources reviewed: [Count] High-quality sources: [Count of highly credible sources] Date range: [Oldest to newest source]
```

**Why this format matters:** You're giving Sonnet the full picture. Partial context leads to partial verification. This is the one time in the workflow where you want everything in one place.

⚠️ **Common mistake:** Only pasting summaries instead of actual source details. Sonnet needs the full citations, quotes, and credibility assessments to verify properly. If you've been maintaining your master doc structure from Phase 2, this is just a copy-paste of everything under "Phase 2 Findings."

---
### **Step 3.3 - Comprehensive Verification Prompt**

**What this prompt does:** Forces Sonnet to act as an adversarial fact-checker on your own research. The seven-part structure catches different failure modes: single-source risks, contradiction handling, evidence strength assessment, coverage gaps, bias detection, remaining research needs, and overall completeness. This isn't asking "is my research good?", it's asking "where are the specific weaknesses and what would fix them?"

```
I've completed comprehensive research on [topic]. Here are all findings:

[Paste your complete compilation above]

Task: Perform rigorous cross-verification and gap analysis

1. Single-Source Claims (High Risk):
    
    - Identify claims appearing in only 1 source
    - Assess: Should we verify or discard?
    - Flag for additional searching if critical
2. Contradictions Analysis:
    
    - Where do sources directly contradict?
    - Which sources are more credible on contested points?
    - Can contradictions be reconciled or must we present both views?
3. Evidence Quality Assessment:
    
    - Strong evidence (multiple credible sources, primary data): [List claims]
    - Moderate evidence (2-3 sources, secondary data): [List claims]
    - Weak evidence (single source, opinion-based): [List claims]
4. Coverage Completeness:
    
    - Which sub-questions are thoroughly answered?
    - Which sub-questions remain partially answered?
    - What new questions emerged from research?
    - What unexpected findings appeared?
5. Blind Spots & Biases:
    
    - Are certain perspectives over/under-represented?
    - Are sources geographically/temporally biased?
    - What assumptions underlie our research approach?
6. Additional Research Needs:
    
    - Critical gaps requiring more research: [Prioritized list]
    - Nice-to-have additional information: [List]
    - Questions that can't be answered with available information: [List]
7. Overall Completeness Assessment:
    
    - Rate research completeness: [0-100%]
    - Justification for rating
    - What would move us to 90%+ completeness?

Organize output with clear sections and confidence indicators.
```

📋 **Real example:** In the SK Hynix research, Sonnet flagged that all HBM demand projections came from sell-side analysts (bullish bias), and zero sources covered potential substitutes or technology shifts that could disrupt HBM. That insight led to targeted searches on "HBM alternatives" and "chiplet memory architectures", which uncovered risks no analyst was discussing.

---
### **Step 3.4 - Decision Point**

Review Sonnet's completeness assessment:

**If 90%+ complete:** Proceed to Phase 4 (Synthesis)

**If 70-89% complete:**

- Address only critical gaps identified
- Run 2-3 targeted Gemini searches for highest-priority gaps
- Update master document
- Re-run verification (shorter version focusing on gap resolution)

**If below 70%:**

- Significant gaps exist
- Return to Phase 2A/2B for additional research on weak sub-questions
- Consider whether research objective needs refinement (maybe you're asking the wrong question)

💡 **Practical guidance:** Don't chase 100% completeness. Diminishing returns hit hard after 85%. The question is "can I answer my research objective with this?" not "have I found every possible source?"

⚠️ **Common mistake:** Ignoring the completeness rating because you're tired of researching. If you're at 60% and Sonnet says you're missing critical information, your final report will be weak. Either do the work or narrow your research objective.

---
### **Step 3.5 - Update Master Document**

Add verification results:

```
## Phase 3: Verification Results

**Completeness:** [X]%

### High-Confidence Findings:

- [Finding 1] (Sources: [3], [7], [12])
- [Finding 2] (Sources: [4], [9])

### Moderate-Confidence Findings:

- [Finding 3] (Sources: [6], [14] - some contradiction with [8])

### Low-Confidence / Uncertain:

- [Finding 4] (Single source: [11] - needs verification)

### Key Contradictions:

1. [Topic]: Source [X] claims [A], but Source [Y] claims [B]
    - Resolution: [Which is more credible and why]

### Remaining Gaps:

- [Gap 1] - Impact: High/Medium/Low
- [Gap 2] - Impact: High/Medium/Low

### Unexpected Findings:

- [Discovery 1]
- [Discovery 2]
```

**Why this section is critical:** This becomes your roadmap for Phase 4. When you're drafting your report, you'll know exactly which claims to state confidently, which to hedge, and which contradictions to acknowledge. It prevents you from accidentally overstating weak evidence.

📋 **Real example structure:** "High-confidence: SK Hynix has 50%+ HBM3 market share (confirmed by 4 independent analyst reports). Moderate-confidence: HBM margins are 2-3x DRAM margins (claimed by 2 sources, but methodologies unclear). Low-confidence: China HBM demand will collapse in 2026 (single opinion piece, no data)."

---
## Phase 4: Synthesis & Report Generation

**Model: Sonnet 4.5 Thinking**

Why Sonnet again?

This is where everything comes together. Sonnet 4.5 Thinking excels at structured long-form writing with consistent voice and proper citation hygiene. It won't fabricate sources or misattribute claims, which is critical when you're drafting a report that will be read and potentially acted upon. The thinking mode helps maintain logical flow across sections, you can see when it's connecting ideas versus just concatenating facts. The main advantage over GPT or Gemini here is citation accuracy and ability to maintain tone across thousands of words. The limitation is that it can be overly cautious, sometimes hedging when you don't need to, but that's fixable in revisions.

---
### **Step 4.1 - Create Report Structure**

In your master document, create this outline:

```
# [Research Project Title]

## Executive Summary
[2-3 paragraphs - write LAST]

## Research Objective & Methodology
### Primary Question
### Sub-Questions Investigated
### Sources & Methodology
### Limitations

## Key Findings
### [Sub-Question 1 Topic]
### [Sub-Question 2 Topic]
### [Continue for all sub-questions]

## Analysis & Synthesis
### Cross-Cutting Themes
### Contradictions & Uncertainties
### Confidence Assessment

## Conclusions
### High-Confidence Conclusions
### Moderate-Confidence Conclusions
### Areas Requiring Further Research

## Appendix: Source List

[All citations organized]
```

**Why this structure matters:** It mirrors how decision-makers actually read research. Executive summary for the impatient, methodology for the skeptical, findings for the detail-oriented, analysis for strategic thinkers, conclusions for action-takers. You can rearrange based on your audience, but this covers all bases.

💡 **Pro tip:** Notice the Executive Summary says "write LAST." You can't summarize what doesn't exist yet. Drafting it first leads to vague platitudes. Draft it last and it will be sharp.

---
### **Step 4.2 - Create Report Generation Thread**

1. Open **new Perplexity thread**
2. Select **Sonnet 4.5 Thinking**
3. Name thread: "[Project Name] - Phase 4: Report Generation"

⚠️ **Critical decision:** You will draft ONE section at a time in this thread. Do not ask Sonnet to draft the entire report at once. It will either hit context limits, lose coherence halfway through, or give you surface-level content. Section-by-section maintains quality.

---
### **Step 4.3 - Section-by-Section Drafting**

**What this approach does:** Breaks a daunting 3,000-5,000 word report into manageable 300-600 word chunks. You maintain quality control at each step, can pivot based on what's working, and avoid the "AI exhaustion" problem where output quality degrades in longer generations. You're also building iteratively, each section informs the next.

**Prompt Template for Each Section:**

```
Context: I'm writing a comprehensive research report on [topic]

Research objective: [Main question]

All research findings: [Paste relevant findings for this section]

Verification results: [Paste Phase 3 confidence assessments for claims in this section]

Task: Draft the following section of my report

Section: [Section name - e.g., "Key Findings: Market Size Analysis"]

Requirements:

- Length: [Specify - e.g., 400-600 words, 3-4 paragraphs]
- Tone: Analytical, professional, objective
- Citation style: Inline citations [source: X] format
- Include data/quotes from sources where relevant
- Flag uncertain claims explicitly with confidence levels
- Acknowledge contradictions between sources
- Structure with clear topic sentences

Specific elements to include:

- [Element 1 - e.g., market size data from 3+ sources]
- [Element 2 - e.g., growth projections with confidence levels]
- [Element 3]

Draft this section now. Maintain consistent voice throughout.
```

📋 **Real example for SK Hynix:** "Section: Key Findings: HBM Market Position. Requirements: 500-600 words. Include: Current market share with citations, competitive positioning vs Samsung/Micron, technology advantages (if any), contract status with major customers. Flag any disputed claims."

---
### **Step 4.4 - Iterative Section Development**

For each section:

1. Get Sonnet's initial draft
2. Review for accuracy against your Phase 3 verification results
3. If needed, refine with follow-up:

```
Refinement needed on [section]:

Issues:

- [Issue 1 - e.g., Missing key data point from Source 14]
- [Issue 2 - e.g., Tone too assertive given medium confidence on this claim]
- [Issue 3 - e.g., Citation needed for claim in paragraph 2]

Revise section addressing these issues.
```

1. Copy approved section into master document
2. Move to next section

💡 **Quality check between sections:** After drafting 2-3 sections, read them in sequence. Do they flow logically? Is the voice consistent? Are you repeating information? Catch structural issues early before you've drafted 10 sections.

---
### **Recommended drafting order:**

1. **Research Objective & Methodology** (easiest, sets context, 200-300 words)
2. **Key Findings sections** (one sub-question at a time, bulk of the report)
3. **Analysis & Synthesis** (requires full context from findings, 600-800 words)
4. **Conclusions** (builds on analysis, 400-500 words)
5. **Executive Summary** (write LAST, summarizes everything, 250-400 words)
6. **Appendix: Source List** (organizational task, can be templated)

**Why this order:** You build from concrete (findings) to abstract (conclusions). Executive summary only works once you know what you're summarizing. Source list is mechanical and can be done whenever.

⚠️ **Common mistake:** Jumping around between sections because you're excited about different findings. This creates voice inconsistencies and logical gaps. Resist the urge. Write linearly through Key Findings, then do Analysis, then Conclusions.

---
### **Step 4.5 - Executive Summary (Write Last)**

Once all other sections complete:

**What this prompt does:** Forces Sonnet to distill your full report into decision-ready format. The stakeholder context matters because it changes what you emphasize. An executive summary for a CFO highlights financial implications, for a product team it highlights market dynamics and competitive threats.

```
Context: I've completed a comprehensive research report on [topic]

Full report text: [Paste your complete report minus executive summary]

Task: Draft Executive Summary

Requirements:

- Length: 250-400 words (2-3 paragraphs)
- Structure: Paragraph 1: Research objective, scope, methodology summary Paragraph 2: Key high-confidence findings (top 3-5) Paragraph 3: Main conclusions and implications
- Tone: Concise, actionable, decision-oriented
- Include only high-confidence findings
- Mention key limitations/uncertainties briefly

This will be read by [stakeholder] who needs [specific decision/insight].

Draft executive summary now.
```

📋 **Real example context:** "This will be read by portfolio managers deciding whether to initiate a position in SK Hynix. They need to understand the bull case, key risks, and confidence level on the thesis."

💡 **Pro tip:** If your executive summary is bland or vague, your full report probably is too. A sharp executive summary with specific claims and clear conclusions indicates solid underlying research.

---
### **Step 4.6 - Source List & Citation Cleanup**

**What this prompt does:** Organizes your 30-60 sources into a usable bibliography with clear categorization. Academic sources carry more weight for some claims, industry reports for others. Organizing by type helps readers quickly assess your source mix.

Create comprehensive source list:

```
Task: Organize all sources into formatted bibliography

Sources used in report: [Paste all source citations from Phases 2A/2B]

Format each as: [#] Author/Organization. "Title." Publication. Date. URL

Organize by:

1. Academic/peer-reviewed sources
2. Industry reports & market research
3. Government/regulatory sources
4. News & media
5. Other

Alphabetize within each category.
```

**Why categorization matters:** A report citing 40 news articles and 2 industry reports reads differently than one citing 30 industry reports and 12 academic papers. The source mix tells a story about research rigor.

⚠️ **Common mistake:** Citing sources in the text that don't appear in your source list, or vice versa. Before you call Phase 4 done, search your report for "[source:" and verify every citation has a corresponding entry in your source list.

---
## Phase 5: Adversarial Review & Verification

**Model: GPT-5.2 (with thinking mode enabled)**

Why GPT?

This is where you need a completely fresh perspective. GPT-5.2 with thinking mode excels at finding logical flaws and alternative interpretations because it approaches your research with zero prior context or investment in your conclusions. Sonnet helped you build the argument, GPT tears it apart to see if it holds up. The thinking mode is critical here, it shows you GPT's reasoning process as it critiques, so you can see whether critiques are substantive or nitpicky. The main advantage is adversarial distance, it hasn't seen your research process and won't give you credit for effort, only for quality. The limitation is that GPT can sometimes over-critique or suggest changes that would weaken rather than strengthen arguments, which is why you triage its feedback rather than accepting everything.

---
### **Step 5.1 - Create Review Thread**

1. Open **new Perplexity thread**
2. Select **GPT-5.2**
3. **Enable thinking mode** (toggle in interface)
4. Name thread: "[Project Name] - Phase 5: Adversarial Review"

💡 **Pro tip:** The thinking mode toggle matters. Without it, GPT gives you conclusions. With it, you see its reasoning, which helps you decide whether to accept or reject specific critiques.

---
### **Step 5.2 - Comprehensive Critique Prompt**

**What this prompt does:** Transforms GPT into a hostile reviewer whose job is to find problems, not validate your work. The six-part structure catches different failure modes: logical errors, evidence issues, alternative interpretations, blind spots, presentation problems, and concrete suggestions for improvement. You're not asking "is this good?", you're asking "what's wrong with this and how would you exploit those weaknesses if you disagreed with my conclusions?"

```
Role: You are a rigorous, skeptical research reviewer tasked with finding flaws

Context: I've completed deep research and written a comprehensive report

Research report: [Paste your complete Phase 4 report including all sections]

Original sources used: [Paste source list with key details]

Task: Provide adversarial critique

1. Logical Flaws & Reasoning Errors:
    
    - Unsupported leaps in logic
    - Correlation mistaken for causation
    - Over-generalization from limited data
    - Confirmation bias in source selection or interpretation
2. Citation & Evidence Issues:
    
    - Claims lacking sufficient citations
    - Misrepresentation of source material
    - Cherry-picking data that supports conclusion while ignoring contradictory evidence
    - Over-reliance on low-quality sources
3. Alternative Interpretations:
    
    - What different conclusions could be drawn from the same evidence?
    - What counter-arguments exist to my main conclusions?
    - What have I potentially misunderstood or misinterpreted?
4. Blind Spots & Missing Perspectives:
    
    - What important angles/stakeholders are not represented?
    - What geographic/temporal/demographic biases exist in sources?
    - What assumptions underlie the analysis that may not be valid?
5. Structural & Presentation Issues:
    
    - Unclear or ambiguous statements
    - Inconsistent confidence levels
    - Poor organization that obscures key points
    - Conclusions not supported by findings sections
6. Suggestions for Strengthening:
    
    - What additional evidence would make conclusions more robust?
    - What hedging language should be added where certainty is overstated?
    - What sections need expansion or clarification?
    - What should be removed as tangential or unsupported?

Be ruthlessly critical. Your job is to find problems, not validate my work.

Show your reasoning process for each critique.
```

📋 **Real example:** In the HBM thesis, GPT flagged that I was treating "HBM demand growth" as a given without addressing potential demand destruction from more efficient memory architectures or AI model compression techniques. Valid critique, led to adding a risks section on technology substitution.

---
### **Step 5.3 - Review GPT-5.2 Output Carefully**

**What you're looking for:** GPT will show its thinking process. Pay attention to:

- Issues flagged as "High priority" or "Significant"
- Specific paragraphs or claims called out
- Alternative interpretations you hadn't considered
- Valid critiques vs. nitpicking (use your judgment)

**Go back and forth with GPT in this thread.** Don't accept the first critique as gospel. If GPT says "This claim is unsupported," respond with "I cited three sources for this claim, here they are again. Do you still think it's unsupported or did you miss the citations?" Sometimes GPT is right, sometimes it's wrong, the dialogue surfaces which is which.

💡 **Pro tip:** The best critiques make you uncomfortable. If you're reading GPT's output and thinking "yeah, I kind of knew that was weak," that's a critique worth addressing. If you're thinking "that completely misses the point," push back and make GPT explain its reasoning.

---
### **Step 5.4 - Triage Critiques**

After your back-and-forth with GPT settles, ask it to output a final markdown file with prioritized critiques:

```
Based on our discussion, create a final critique summary in markdown format with three priority levels:

**Must Fix (Impacts Core Conclusions):**

- [Issue with specific section reference]
- [Issue with specific section reference]

**Should Fix (Improves Quality):**

- [Issue with specific section reference]
- [Issue with specific section reference]

**Consider (Minor Improvements):**

- [Issue with specific section reference]
- [Issue with specific section reference]

For each issue, include:

- What's wrong
- Why it matters
- Specific suggestion for fix
```

**Why markdown format matters:** You'll paste this directly into Phase 6, where you'll work through fixes systematically. Having it structured and prioritized prevents you from spending an hour fixing a typo while ignoring a logical flaw.

⚠️ **Common mistake:** Treating all critiques equally. GPT will find 15 things "wrong" with your report. Maybe 3 actually matter. Triage ruthlessly based on impact to your core argument.

---
### **Step 5.5 - Export the Critique**

Copy GPT's final markdown critique summary and save it. You'll need it for Phase 6.

**You can also add your own notes:**

```
**Must Fix (Impacts Core Conclusions):**

- [GPT's issue]
    - My assessment: [Agree/Disagree and why]
    - Action: [What I'll do about it]

**Disagree / Not Addressing:**

- [GPT's issue]
    - Why I'm not fixing this: [Your reasoning]
```

This creates an audit trail. If someone later asks "why didn't you address X?", you have documented reasoning.

📋 **Real example disagreement:** GPT suggested adding a section on memory alternatives to HBM. I agreed it was a gap but decided it was out of scope for a focused HBM thesis. Documented that decision so I don't second-guess it later.

---
### **Why Phase 5 is "optional but not really":**

You can stop after Phase 4 and have a solid, well-researched report. But Phase 5 is what catches the stuff you can't see because you're too close to your own work. It's the difference between "this is good research" and "this is bulletproof research."

The reports that stand out, the ones people actually trust and reference? They've been through adversarial review. The ones that get dismissed as "AI slop" or "biased analysis"? They skipped this step.

---
## Phase 6: Incorporate Critiques & Finalize

**Model: Sonnet 4.5 Thinking**

Why back to Sonnet?

You're returning to the model that drafted your report because it maintains the voice and structure you've already established. Sonnet understands the original argument flow and can revise specific sections without breaking the overall narrative. GPT identified the problems, but Sonnet fixes them while maintaining consistency. The thinking mode helps you see how it's balancing your original intent with the critique's suggestions, you can verify it's not over-correcting or losing your core argument. The main advantage is continuity, you're refining the existing work, not rewriting from scratch.

---
### **Step 6.1 - Return to Your Phase 4 Thread**

Go back to your "[Project Name] - Phase 4: Report Generation" thread where you drafted the report.

**Why same thread:** You want Sonnet to have full context of how the report was constructed. Starting a new thread means re-explaining everything. This thread already has the conversation history of each section's development.

---
### **Step 6.2 - Systematic Revision Prompt**

**What this prompt does:** Feeds GPT's critique to Sonnet section by section with clear instructions on what to fix and what to preserve. You're not asking Sonnet to "make it better," you're giving it specific issues to address while maintaining your core argument and voice.

For each section that needs revision:

```
I received adversarial review on this report. I need to revise [specific section name].

Current version: [Paste current section text from your report]

Critique to address: [Paste relevant critiques from Phase 5 markdown for this section]

Original source material: [Paste relevant sources if needed for fact-checking or adding citations]

Task: Revise this section addressing the valid critiques while maintaining:

- Original argument structure
- Consistent voice and tone
- Proper citations for all claims
- Explicit confidence levels where appropriate

Do not:

- Completely rewrite or change the core argument
- Add fluff or padding to address word count
- Remove important nuance to "simplify"

Show me the revised section.
```

💡 **Pro tip:** Start with "Must Fix" items from your Phase 5 triage. Don't waste time polishing minor issues if you still have fundamental problems to address.

---
### **Step 6.3 - Iterative Refinement**

**What this looks like in practice:**

1. Paste critique + section to Sonnet
2. Review Sonnet's revision
3. If it addresses the issue without breaking anything: accept and move to next section
4. If it over-corrected or lost important nuance: push back

**Example push-back:**

```
This revision addresses the citation gap, but now the argument feels too hedged. The original said "HBM demand will likely grow 40-50% annually" (medium confidence, 3 sources). Your revision says "HBM demand may potentially grow" which is too weak given our evidence.

Revise to: properly cite the 3 sources, maintain medium confidence level, but keep the assertive tone. The evidence supports the claim.
```

You're having a conversation, not accepting the first output. Go back and forth until the revision works.

⚠️ **Common mistake:** Accepting every Sonnet revision without reading carefully. Sometimes it "fixes" a critique by removing the claim entirely rather than supporting it better. That's not a fix, that's avoidance.

---
### **Step 6.4 - Update Master Document as You Go**

After each section is revised and approved:

1. Replace the old version in your master document with the revised version
2. Mark it as complete in your critique tracking

**Why incremental updates matter:** If you wait until the end to update everything, you'll lose track of what's been revised and what hasn't. Update as you go, maintain one source of truth.

📋 **Progress tracking example:**

```
**Must Fix (Impacts Core Conclusions):**

- ✅ Market size section lacks citation for 40-50% growth claim - FIXED
- ⬜ Competitive analysis doesn't address Samsung's new HBM4 capabilities - IN PROGRESS
- ⬜ Conclusion overstates confidence on margin expansion - NOT STARTED
```
---
### **Step 6.5 - Final Quality Pass**

Once all priority revisions are complete, do one final check with Sonnet:

```
I've addressed all major critiques from adversarial review. Here's the revised report:

[Paste complete updated report]

Changes made:

- [Change 1]
- [Change 2]
- [Change 3]

Task: Final quality check

1. Consistency: Does the voice and tone remain consistent across all sections?
2. Citations: Is every major claim properly cited?
3. Flow: Do sections connect logically, or did revisions create awkward transitions?
4. Confidence levels: Are they appropriate and consistently applied?
5. Completeness: Does the report still answer the original research objective?

Brief assessment (3-4 paragraphs) covering these five areas.
```

**What you're looking for:** Sonnet should confirm that revisions improved quality without breaking anything. If it flags new issues introduced by revisions, fix those before calling it done.

💡 **Pro tip:** Read your revised report out loud or at least slowly start to finish. Your eyes will catch awkward phrasing or logical gaps that you missed when reviewing section-by-section.

---
### **Step 6.6 - Export Final Version**

Once you're satisfied:

1. **Save your master document** in your preferred format (Markdown, PDF, Google Doc)
2. **Export relevant sections** if you need different versions for different audiences (exec summary only, full report, findings deck)
3. **Save your Perplexity thread URLs** in case you need to reference the research process later

**Format options based on use case:**

- **Internal decision memo:** Markdown or Google Doc with full citations
- **Stakeholder presentation:** Distill to key findings with supporting data
- **Published research:** PDF with proper formatting and table of contents
- **Personal reference:** Keep in Notion/Obsidian with links to source threads

---
## **What separates good research from excellent research:**

Phases 1-4 get you to "solid research." Phase 5 identifies weaknesses. Phase 6 is where you actually fix them. Most people skip Phase 6 because they're tired or convinced their first draft was fine. That's how you end up with research that has obvious holes.

The reports that get cited, referenced, and trusted? They went through this refinement cycle. Often multiple times.

---
# Footnotes & Further Reading

I was planning to write a full analysis on how to apply recursive reasoning patterns to everyday research workflows, but this guide took priority. Once I finish testing these concepts more rigorously, I'll publish that research. If you found this guide useful, you might also enjoy my other work:

- [**An AI-Powered Resume Workflow**](https://github.com/VeritasPlaybook/playbook/blob/main/career-workflow/resume-workflow/An%20AI-Powered%20Resume%20Workflow.md) - How to build a resume system that actually works with AI
- [**The Memory Play: Why AI's Future Runs on HBM, Not Hype**](https://github.com/Veritas-Research/investment-research/blob/main/theses/The%20Memory%20Play%20-%20Why%20AI's%20Future%20Runs%20on%20HBM%2C%20Not%20Hype.md) - Investment thesis on the semiconductor memory market (built using Deep Research before it was nerfed)

More research, workflows, and investment theses coming soon at [**github.com/VeritasPlaybook**](https://github.com/VeritasPlaybook) and [**github.com/Veritas-Research**](https://github.com/Veritas-Research).

---
# Quick Reference Cheatsheet

I know this was a lot, and maybe overwhelming. But if you want to take anything away as a cheatsheet, this is the one you print out or link someone to.

---
## Phase 1: Decomposition & Planning

**Model:** Sonnet 4.5 Thinking

**Why:** Best at systematic reasoning and structured thinking

**What to do:**

1. Create planning thread, enable Sonnet Thinking
2. Use decomposition prompt to break question into 6-8 sub-questions
3. Ask Sonnet to critique and refine the plan
4. Copy refined plan to master document with status checkboxes

**Key output:** Prioritized list of sub-questions with dependencies identified

---
## Phase 2A: Parallel Information Gathering

**Model:** Gemini 3 Pro

**Why:** Fastest at web retrieval, good breadth across sources

**What to do:**

1. Open separate thread for each sub-question
2. Use gathering prompt to find 5-7 sources per question
3. Run 3-4 searches in parallel
4. Copy all findings to master doc with citations
5. Quality check: Do you have 30-50 total sources?

**Key output:** 5-7 cited sources per sub-question in master document

---
## Phase 2B: Deep Dives (When Needed)

**Model:** Sonnet 4.5 Thinking

**Why:** Best at analytical synthesis and handling contradictions

**When to use:** Sources contradict, question needs analysis, info quality is weak

**What to do:**

1. Create deep dive thread for flagged sub-questions only
2. Paste Phase 2A findings, ask for gap analysis and synthesis
3. Run targeted follow-up searches based on gaps identified
4. Document confidence levels (High/Medium/Low) in master doc

**Key output:** Preliminary synthesis with explicit confidence assessments

---
## Phase 3: Cross-Verification & Gap Analysis

**Model:** Sonnet 4.5 Thinking

**Why:** Maintains coherence over long contexts, best at spotting contradictions

**What to do:**

1. Create verification thread
2. Paste ALL findings from Phases 2A and 2B
3. Use comprehensive verification prompt (7-part structure)
4. Get completeness rating (0-100%)
5. Address critical gaps if below 90%

**Key output:** Completeness rating + prioritized list of high/medium/low confidence findings

**Decision point:** 90%+ complete? Move to Phase 4. Below 70%? Return to Phase 2.

---
## Phase 4: Synthesis & Report Generation

**Model:** Sonnet 4.5 Thinking

**Why:** Best at structured writing, maintains voice, accurate citations

**What to do:**

1. Create report structure in master doc
2. Create report generation thread
3. Draft ONE section at a time using section prompt
4. Review and refine each section before moving to next
5. Write executive summary LAST
6. Organize source list by category

**Key output:** Complete research report with proper structure and citations

**Drafting order:** Methodology → Key Findings → Analysis → Conclusions → Exec Summary

---
## Phase 5: Adversarial Review (Highly Recommended)

**Model:** GPT-5.2 with thinking mode enabled

**Why:** Fresh perspective, finds logical flaws you can't see

**What to do:**

1. Create review thread, enable thinking mode
2. Paste complete report + source list
3. Use adversarial critique prompt (6-part structure)
4. Go back and forth with GPT to clarify critiques
5. Ask GPT to output final markdown with prioritized issues
6. Export the critique markdown

**Key output:** Prioritized critique in markdown (Must Fix / Should Fix / Consider)

**This is optional, but it's what separates good research from excellent research.**

---
## Phase 6: Incorporate Critiques & Finalize

**Model:** Sonnet 4.5 Thinking

**Why:** Maintains voice and structure from original draft

**What to do:**

1. Return to Phase 4 thread
2. Address "Must Fix" items first
3. Use revision prompt for each section needing changes
4. Go back and forth with Sonnet until revision works
5. Update master doc as you complete each revision
6. Final quality pass on complete revised report
7. Export in needed format

**Key output:** Final polished report ready for delivery

---
## Model Quick Reference

|**Phase**|**Model**|**Why This Model**|
|---|---|---|
|1. Planning|Sonnet 4.5 Thinking|Systematic reasoning, shows thinking process|
|2A. Gathering|Gemini 3 Pro|Fast retrieval, good breadth|
|2B. Deep Dives|Sonnet 4.5 Thinking|Analytical synthesis, handles contradictions|
|3. Verification|Sonnet 4.5 Thinking|Long context, spots contradictions|
|4. Report Writing|Sonnet 4.5 Thinking|Structured writing, citation accuracy|
|5. Adversarial Review|GPT-5.2 + Thinking|Fresh perspective, finds logical flaws|
|6. Refinement|Sonnet 4.5 Thinking|Maintains voice, preserves structure|

---
## Key Reminders

**Thread Organization:**

- One thread per phase or sub-question
- Name threads clearly: "[Project] - Phase X: [Description]"
- Use Collections to group related threads

**Master Document is Your Source of Truth:**

- Always pull findings out of threads into your doc
- Update continuously, don't wait until the end
- Use status checkboxes to track progress

**Quality Over Speed:**

- Don't skip Phase 3 verification (catches bad sources)
- Don't draft entire report at once (section-by-section maintains quality)
- Don't skip Phase 5+6 if you want work that stands out

**When to Stop:**

- Phase 3 completeness at 90%+ means you're ready for Phase 4
- You can stop after Phase 4 and have solid research
- Phases 5+6 are what make research excellent vs. good

**Common Mistakes:**

- Running everything in one thread (loses organization)
- Accepting first AI output without verification
- Forgetting to cite sources properly
- Skipping adversarial review because you're tired

---

**You just learned to manually replicate Deep Research. Now go build something that matters.**

---













# Addendum
If you made it this far - then here is some more (experimental) material.
## Speed Optimizations (Advanced)

Perplexity is finicky with making exportable and downloadable markdown, so proceed with caution. I've been experimenting with ways to streamline and compress this workflow. This addendum covers some things I found that work and might speed up the process, but they come with downsides and overhead (file management, cross-copying between tools, less hands-on engagement with sources). If I find ways to make this better, I will update this section.

**What you're trading:** The main workflow is designed to make you "touch" every source, which builds familiarity and helps you spot patterns. These optimizations reduce that engagement for speed. Use them only if you understand the concepts and have run the full workflow at least once.

**Overhead to expect:** Exporting files, organizing them in folders, uploading multiple files to threads, troubleshooting when Perplexity's export doesn't work consistently. If this sounds like more work than copy-pasting, stick to the main workflow.

---
## Proven Optimizations

### Rolling Verification (Phase 3 Alternative)

**What it does:** Instead of compiling ALL Phase 2 findings into one massive paste for Phase 3 verification, you verify in smaller batches of 2-3 sub-questions at a time.

**Why this helps:** Reduces cognitive load, easier to manage, catches issues earlier before you've gathered everything.

**How to do it:**

1. Create your Phase 3 verification thread as usual (Sonnet 4.5 Thinking)    
2. Instead of the comprehensive verification prompt, use this iterative approach:    

**First batch (Sub-Questions 1-3):**

```
I'm verifying research quality in batches to keep things manageable. 

Batch 1: Sub-Questions 1-3 findings: 
[Paste findings for Q1, Q2, Q3 from your master doc] 

Task: Focused verification for these questions only: 

1. Single-Source Claims: Which claims appear in only 1 source? 
2. Contradictions: Where do sources disagree? 
3. Evidence Quality: Rate each major claim (High/Medium/Low confidence) 
4. Coverage: Are these questions thoroughly answered or do they need more research? 
   
Organize findings by sub-question with confidence levels.
```

3. Review Sonnet's output, address any critical gaps if needed    
4. Move to next batch (Sub-Questions 4-6), repeat    
5. After all batches complete, ask for cross-cutting analysis:    

```
I've now verified all sub-questions in batches. 

Give me: 

1. Overall Completeness Rating: [0-100%] 
2. Cross-Cutting Contradictions: Issues that span multiple sub-questions 
3. Blind Spots: What perspectives or angles are missing across the entire research? 
4. Critical Gaps: Prioritized list of what would most improve completeness 
   
Based on all batches, should I proceed to Phase 4 or address gaps first?
```

**Trade-offs:**

- ✅ Pro: Easier to manage than one giant paste, less overwhelming    
- ✅ Pro: Spot issues earlier when they're cheaper to fix    
- ❌ Con: Might miss patterns that only emerge when viewing all findings together    
- ❌ Con: Adds 10-15 min to Phase 3 (multiple prompts vs one)    

**When to use:** If you have 8+ sub-questions or if comprehensive verification feels overwhelming.

---
## Reference Phase 3 Instead of Re-Pasting Sources (Phase 4 Alternative)

**What it does:** In Phase 4 report drafting, instead of pasting all source details for each section, you paste only the Phase 3 confidence assessments and tell Sonnet to ask if it needs specific citations.

**Why this helps:** Eliminates repetitive pasting of the same sources across multiple Phase 4 sections. Phase 3 already synthesized everything, so Sonnet just needs confidence levels, not raw sources again.

**How to do it:**

**Modified Phase 4.3 section prompt:**

```
Context: I'm writing a comprehensive research report on [topic] 

Section: [Section name - e.g., "Key Findings: Market Size Analysis"] 

Phase 3 confidence assessment for this section: [Paste ONLY the relevant confidence-rated findings from Phase 3 output] 

Example: 
- High confidence: SK Hynix holds 50%+ HBM3 market share (verified by 4 analyst reports) 

- Medium confidence: HBM margins are 2-3x DRAM margins (2 sources, methodologies unclear) 

- Low confidence: Demand will collapse in 2026 (single opinion piece) 
  
Full source details are in my master document. If you need specific citations for any claim, ask me. 

Task: Draft this section 

Requirements: 
- Length: [400-600 words, 3-4 paragraphs] 
- Tone: Analytical, professional, objective 
- Use inline citations [source: X] for claims, I'll provide details if you need them 
- Flag uncertain claims with appropriate confidence language 
- Acknowledge contradictions where they exist 
  
Draft now, maintaining consistent voice.
```

**When Sonnet asks for citations:** Go to your master doc, find the relevant source, paste just that citation.

**Trade-offs:**

- ✅ Pro: Saves 15-20 minutes across Phase 4 (less pasting)    
- ✅ Pro: Forces you to rely on Phase 3's rigorous verification    
- ❌ Con: Sonnet has less context, might ask for citations more often    
- ❌ Con: Requires Phase 3 output to be well-organized (if your verification was sloppy, this won't work)    

**When to use:** If you did thorough Phase 3 verification and trust those confidence assessments.

---
## Experimental: Multi-File Workflow

**Status:** Perplexity's markdown export is inconsistent. Sometimes it generates downloadable files, sometimes it gives you text blobs, sometimes it fails entirely. This workflow is experimental and might not work reliably for you.

**The concept:** Export each Phase 2 thread as markdown, upload all files to Phase 3 verification thread, let Sonnet read multiple files at once instead of you copy-pasting everything.

---
## How to Export from Perplexity (When It Works)

After each Phase 2A thread completes:

1. Look for export/share button in the thread (usually top-right)    
2. Select "Export as Markdown" or similar option    
3. **If it downloads a .md file:** Save it with clear naming: `SubQ1-Market-Position.md`, `SubQ2-Competitive-Analysis.md`, etc.    
4. **If it gives you text blob:** Copy-paste into a text editor, save manually as .md file    
5. **If export fails:** Fall back to manual copy-paste from main workflow    

Store all exported files in a project folder: `[Project Name]/Phase2-Findings/`

**Troubleshooting:**

- If markdown formatting breaks during export, you'll need to manually fix headers, bullets, code blocks    
- Some users report Perplexity's export loses citations or URLs, always spot-check the file    
- Export might work better on desktop vs mobile    

---

## How to Use Multi-File Upload in Phase 3

Once you have all Phase 2 files exported:

1. Create Phase 3 verification thread (Sonnet 4.5 Thinking)    
2. Upload all Phase 2 markdown files at once (Perplexity supports up to 10 files)    
3. Use this modified verification prompt:    

```
I've uploaded markdown files containing all my Phase 2 research findings (one file per sub-question). Research Objective: [Your main question] Task: Read all uploaded files and perform comprehensive verification 1. Single-Source Claims: Identify claims appearing in only 1 source across all files 2. Contradictions: Where do sources contradict (within files or across files)? 3. Evidence Quality: Rate major claims as High/Medium/Low confidence 4. Coverage Completeness: Which sub-questions are thoroughly answered vs partially answered? 5. Blind Spots: What perspectives are missing across all research? 6. Overall Completeness: Rate 0-100% with justification Organize output by sub-question, then provide cross-cutting analysis at the end.
```

4. Sonnet will (theoretically) read all files and synthesize    
5. Review its output, proceed to Phase 4    

**What to do if file upload doesn't work:**

- Try uploading 3-4 files at a time instead of all 10    
- Fall back to Option A (rolling verification)    
- Fall back to main workflow (copy-paste compilation)    

---

## Trade-offs of Multi-File Approach

**Pros:**

- ✅ Saves 20-30 minutes if it works (no copy-paste, no reformatting)    
- ✅ Keeps findings organized in separate files for future reference    
- ✅ Cleaner master document structure    

**Cons:**

- ❌ Perplexity export is unreliable, might waste time troubleshooting    
- ❌ File management overhead (naming, organizing, ensuring no data loss)    
- ❌ Less engagement with sources (you're not reading as you copy)    
- ❌ If Sonnet misses something in the files, you won't catch it as easily    
- ❌ Harder to annotate or add notes during gathering phase    

**Additional overhead:**

- Creating folder structure for project    
- Naming files consistently    
- Verifying exports didn't lose data    
- Re-exporting if markdown formatting breaks    
- Managing multiple files instead of one master doc    

**When to experiment with this:** If you're doing 5+ research projects and want to test whether the file-based workflow is worth the setup cost. Not recommended for your first 2-3 projects.

---

## When to Use What

**Use the main workflow if:**

- This is your first 1-2 times through the process    
- You want maximum engagement with sources    
- You don't want to deal with file management    
- Perplexity export isn't working reliably for you    

**Use Option A (Rolling Verification) if:**

- You have 8+ sub-questions and Phase 3 feels overwhelming    
- You want to catch issues early    
- You're comfortable with the core workflow but want Phase 3 to be more manageable    

**Use Option B (Reference Phase 3) if:**

- You did thorough Phase 3 verification and trust it    
- You want to save time in Phase 4 report drafting    
- You're okay with less source context during writing    

**Experiment with Multi-File if:**

- You're doing this regularly (5+ projects)    
- Perplexity export is working consistently for you    
- You're comfortable troubleshooting file issues    
- You value file-based organization over hands-on engagement    

**My recommendation:** Start with main workflow. After 2-3 projects, try Option A or B. Only experiment with multi-file if you're committed to making this a regular practice and have confirmed Perplexity export works for you.



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
- 💼 [LinkedIn]([https://github.com/Veritas-Research/investment-research](https://www.linkedin.com/in/malocilja/?view=public))
- 🐙 [Veritas Playbook - GitHub]([https://github.com/VeritasNotes](https://github.com/VeritasPlaybook/playbook))
- 📊 [Investment Research](https://github.com/Veritas-Research/investment-research)

---

*If you found this valuable, star ⭐ the repo to help others find it.*