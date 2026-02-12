>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

For Table of Contents, click **Outline** button on the right ----------------------------------------------------------------------------------------------^

# Why This Guide Exists

I originally set out to write this guide after discovering recent MIT research on Recursive Language Models (RLMs). The principles were powerful, but inaccessible - they required code execution and programmatic context management that most people couldn't implement.

Then Perplexity changed their Deep Research limits. People I'd recommended the platform to were suddenly stuck, and I needed a solution fast. So I pivoted: I published a [Perplexity-specific guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Complete%20Manual%20Deep%20Research%20Guide%20for%20Perplexity%20Pro.md) quickly to help people who needed an alternative approach right away, and to solve my own research workflow problems.

That guide worked. People used it for investment research, product decisions, academic work. But they came back asking for three things: make it platform-agnostic so it works with any AI tool, make it more robust with lessons learned from real use, and create a shorter reference version for experienced users.

**This is that guide.** It's what I originally planned to write, now improved with real-world testing and community feedback. The Perplexity version still works great if you're committed to that platform, but this one gives you flexibility and incorporates everything I've learned about what actually works in practice.

---
# The RLM Foundation

The methodology is grounded in [MIT research on Recursive Language Models](https://arxiv.org/html/2512.24601v1), which demonstrated something powerful: AI systems perform dramatically better on complex tasks when they decompose problems, process information in parallel, verify outputs, and synthesize findings - rather than trying to ingest everything at once in a single prompt.

**This guide implements RLM principles manually through structured prompting.** You get the power of recursive AI reasoning with the control of human oversight at every decision point.

---
# What makes this different from automated research tools?

Automated research (Perplexity Deep Research, ChatGPT's o3, Claude's Max) are powerful but opaque black boxes. They're optimized for speed and convenience - you get an answer in 5-15 minutes, but you don't see how they arrived at it, what contradictions they smoothed over, or what gaps they missed.

This workflow trades speed for transparency and control:

- **Automated tools:** Fast, opaque, good for exploratory research and well-established topics
    
- **This workflow:** Slower, transparent, better for high-stakes decisions where you need to understand contradictions, assess evidence quality, and defend your conclusions

---
# What makes this different from automated research tools?

Automated research (Perplexity Deep Research, ChatGPT's o3, Claude's Max) are powerful but opaque black boxes. They're optimized for speed and convenience - you get an answer in 5-15 minutes, but you don't see how they arrived at it, what contradictions they smoothed over, or what gaps they missed.

This workflow trades speed for transparency and control:

- **Automated tools:** Fast, opaque, good for exploratory research and well-established topics    
- **This workflow:** Slower, transparent, better for high-stakes decisions where you need to understand contradictions, assess evidence quality, and defend your conclusions

---
# When to use this workflow

**Use this when:**

- Stakes are high (investment decisions, product strategy, academic research, major purchases)    
- You need to understand contradictions and evidence quality, not just get an answer    
- Sources are likely to disagree or be biased    
- The topic is rapidly evolving or controversial    
- You'll be questioned on your sources and reasoning    
- You want to learn the research methodology, not just consume results    

**Use automated tools when:**

- Exploratory research or general learning    
- Well-established topics with broad consensus    
- Time-sensitive delivery (need answer in minutes, not hours)    
- Low-stakes decisions where "good enough" is truly good enough    

---
# What you'll learn

This guide teaches you a **7-phase research methodology** that mirrors how professional researchers, analysts, and investigators actually work—but supercharged with AI at each step:

1. **Build Your Map** - Break down your question into answerable sub-questions with clear dependencies    
2. **Collect Evidence** - Gather sources in parallel using fast retrieval models    
3. **Deep Dive** - Analyze complex contradictions that need reasoning, not just retrieval    
4. **Check Quality** - Cross-verify claims, spot contradictions, assess evidence strength    
5. **Write Report** - Synthesize findings into a coherent narrative with proper citations    
6. **Stress Test** - Red-team your own work to find logical flaws and blind spots    
7. **Polish** - Incorporate critiques and finalize    

Each phase uses AI models strategically—fast models for retrieval, reasoning models for analysis, fresh models for critique—while you make the critical decisions at transition points.

---
# What you'll need

**AI platform with multi-model access:**

- **Recommended:** Perplexity Pro ($20/month) - gives you Claude, Gemini, GPT, and built-in web search    
- **Alternatives:** Claude Projects, ChatGPT Plus, Poe, or API access with separate search tool    
- **Required capabilities:**    
    - Fast retrieval model (Gemini Pro, GPT-4o mini, Claude Haiku)        
    - Strong reasoning model (Claude Sonnet 4.5, o1, DeepSeek-R1)        
    - Web search access (built-in or separate)        

**Document management:**

- Markdown-capable note system (Notion, Obsidian, Google Docs with markdown enabled)    
- This will be your **Master Document**, the central/primary document where all findings live    

**Time investment:**

- **First time:** 2-4 hours (you're learning the system)    
- **After practice:** 60-90 minutes for complex research    
- **Quick version:** 30-45 minutes (I'll release a separate Quick Guide)    

---
# A note on RLM terminology

Throughout this guide, you'll see references to "RLM principles" or "recursive patterns." You don't need to understand the technical details of Recursive Language Models to use this workflow effectively. Just know that:

- **Decomposition** = Breaking big questions into smaller ones you can actually answer    
- **Parallel processing** = Working on multiple sub-questions at once instead of sequentially    
- **Verification** = Checking your work as you go, not just at the end    
- **Synthesis** = Combining everything back together in a way that makes sense    

If you're curious about the research behind this, see the [RLM Appendix](XXXX) at the end.
  
---
## How This Guide is Organized

Each of the 7 phases follows the same structure:

1. **What it does** - The purpose of this phase in plain language    
2. **Why it matters** - What goes wrong if you skip this    
3. **Model selection** - Which AI models work best (with Best/Good/Budget options)    
4. **Step-by-step instructions** - Exactly what to do, including copy-paste prompt templates    
5. **Decision points** - Traffic light checks (🟢 proceed / 🟡 fix / 🔴 rethink)    
6. **Real examples** - How this looks in practice    
7. **Common mistakes** - What to avoid    

**Pro tip:** Your first time through, follow the instructions exactly. Once you understand the pattern, you can adapt it to your specific needs and tools.

---
# Overview: The Seven-Phase System

This workflow has **7 phases** that mirror how professional researchers actually work - but supercharged with AI at each step. Here's what each phase does and why it matters:

## Phase 1: Build Your Map (Decomposition & Planning)

**What it does:** Transforms your broad question into 6-8 specific, answerable sub-questions with clear dependencies and priorities.

**Why it matters:** Without decomposition, you're searching randomly and hoping you cover everything. With it, you have systematic coverage and know exactly what you're looking for. Most research fails here - you can't fix bad planning with good execution.

---
## Phase 2: Collect Evidence (Parallel Information Gathering)

**What it does:** Runs 3-4 searches simultaneously across your sub-questions, collecting 5-7 authoritative sources for each.

**Why it matters:** This is raw material collection. Speed matters because you need breadth before depth. Parallelization saves massive time - you're sending multiple scouts in different directions instead of one person walking the entire perimeter.

---
## Phase 3: Deep Dive (Analytical Synthesis)

**What it does:** Takes complex sub-questions where sources contradict or require interpretation, and performs rigorous analysis to extract meaningful insights.

**Why it matters:** This separates surface-level research from deep understanding. Some questions can't be answered with quick searches - they require thinking. Not every question needs this (you'll decide which ones do), but the ones that do are usually your most important findings.

---
## Phase 4: Check Quality (Cross-Verification & Gap Analysis)

**What it does:** Analyzes all gathered research holistically, identifies single-source claims, contradictions, evidence quality, and gaps.

**Why it matters:** This is your bullshit detector. AI models will confidently cite bad sources or miss contradictions. This phase catches those issues before they become conclusions. It also tells you if you're 90% done or need more research.

---
## Phase 5: Write Report (Synthesis & Generation)

**What it does:** Transforms all your research into a coherent narrative with proper structure, citations, and confidence levels for each claim.

**Why it matters:** Research isn't useful until it's communicated clearly. This phase drafts section-by-section to maintain quality and ensure every claim traces back to sources.

---
## Phase 6: Stress Test (Adversarial Review)

**What it does:** Uses a fresh model to ruthlessly critique your report, finding logical flaws, missing evidence, alternative interpretations, and blind spots.

**Why it matters:** You're too close to your own research. You'll miss obvious gaps, over-rely on favorite sources, or state conclusions more confidently than evidence supports. A fresh perspective catches what you can't see. This is what separates thoughtful research from AI-generated content.

---
## Phase 7: Polish (Incorporate Critiques & Finalize)

**What it does:** Takes the critique from Phase 6 and iteratively refines your report, addressing valid issues while maintaining your core arguments.

**Why it matters:** The critique is useless if you don't act on it. This phase forces you to confront weaknesses, strengthen evidence, and acknowledge uncertainty where appropriate. Combined with Phase 6, this makes your research stand out.

---
## The Complete Flow

Phase 1: Build Your Map (Planning)
           ↓
Phase 2: Collect Evidence (Parallel searches)
           ↓
    🚦 Decision Point: Any contradictions or complexity?
           ↓
Phase 3: Deep Dive (If needed - only for complex sub-questions)
           ↓
Phase 4: Check Quality (Verification)
           ↓
    🚦 Decision Point: 90%+ complete?
           ↓
Phase 5: Write Report (Synthesis)
           ↓
Phase 6: Stress Test (Adversarial review)
           ↓
Phase 7: Polish (Final refinement)
           ↓
        ✅ Done

**Key insight:** Each phase uses the AI model that's best at that specific task. Fast models for retrieval, reasoning models for analysis, fresh models for critique. By manually orchestrating these models, you get better results than any single model running autonomously, because you're making strategic decisions at every transition point.

**Flexibility:** Not every research project needs all 7 phases at full depth. Simple questions might skip Phase 3 entirely. Low-stakes research might skip Phase 6. But for high-stakes work where you need to defend your conclusions, all 7 phases pay off.

---
# Phase 1: Build Your Map

## What This Phase Does

Transforms your broad, vague question into 6-8 specific, answerable sub-questions with clear priorities and dependencies. This is your research blueprint - you can't just start searching randomly and hope you cover everything.

## Why It Matters

Without proper decomposition, you'll:

- Search for information you can't interpret yet (asking about "HBM margins" before you know what HBM is)    
- Miss critical angles because you didn't think to ask    
- Waste time on tangential research that doesn't answer your core question    
- Get stuck when sources contradict because you didn't plan for verification    

Good planning here makes everything downstream easier. Bad planning ruins even perfect execution.

## Model Selection

You need a **reasoning model** that shows its thinking process, not just outputs.

**Best:**

- Claude Sonnet 4.5 with Thinking mode    
- o1 or o3 (if available)    
- DeepSeek-R1    

**Good:**

- Claude Sonnet 3.5    
- Gemini Pro 1.5 (with extended reasoning)    
- GPT-4o    

**Budget/Single-model path:**

- Use whatever reasoning model you have access to, but check its work carefully

**Why reasoning over retrieval:** You're not gathering facts yet - you're structuring how to think about the problem. Models with extended reasoning catch planning mistakes (circular dependencies, questions that are too broad/narrow, blind spots).

# Step-by-Step Instructions

## Step 1.1: Set Up Your Master Document

Before you start planning, create your **Master Document** (your central/primary document where everything lives).

**Platform options:**

- Notion (easiest for linking and organization)    
- Obsidian (best for power users who want local files)    
- Google Docs (enable markdown support in settings)    
- Any markdown-capable note system    

**Create this structure:**

```
# [Your Project Title] - Research

## Research Objective
[Your main question - fill in after planning]

## Sub-Questions (Priority Order)
[Will be populated in Step 1.4]

## Phase 2: Evidence Collected
[Leave blank for now]

## Phase 4: Quality Check Results
[Leave blank for now]

## Phase 5: Final Report
[Leave blank for now]

## Sources & Citations
[Leave blank for now]
```

**Why this structure matters:** You'll be copying information into this document throughout the workflow. Having the skeleton ready prevents chaos later.

## Step 1.2: Create Planning Thread

Open your AI platform and start a fresh conversation:

1. Select your **reasoning model** (Sonnet 4.5 Thinking recommended)    
2. Name the thread: "[Project Name] - Phase 1: Planning"    

**Pro tip:** Clear thread naming matters when you're juggling 5-10 threads across phases. "New Thread (7)" is useless; "SK Hynix Analysis - Planning" tells you exactly what it is.

## Step 1.3: Run Initial Decomposition

Use this prompt template, filling in your specifics:

```
Research Objective: [Your main question - be specific]

Context:
- Purpose: [Why you need this research - e.g., investment decision, product strategy, market analysis, major purchase]
- Scope: [Geographic region, time period, industry constraints, or "no constraints"]
- Depth needed: [Surface overview / Moderate depth / Deep analysis]
- Key stakeholders/audience: [Who will use this research, or "just for me"]

Task: Create a comprehensive research plan

Break this into 6-8 sub-questions that together fully answer the objective. For each sub-question:

1. Specific information requirements (quantitative data, expert opinions, case studies, etc.)
2. Likely authoritative sources (academic papers, industry reports, government data, company filings, etc.)
3. Dependencies (which questions must be answered before others - be explicit)
4. Search difficulty estimate (easy/moderate/hard)
5. Priority ranking (1-8, with 1 being highest priority)

Output format:
- Numbered list of sub-questions
- For each: [Information needed] | [Source types] | [Dependencies] | [Difficulty] | [Priority]
- Final section: Recommended research sequence (order to tackle questions based on dependencies)
```

**Common mistake:** Being too vague in "Research Objective."

❌ Bad: "Tell me about AI"  
✅ Good: "What are the key revenue drivers for AI infrastructure companies in 2026?"

❌ Bad: "Should I buy this stock?"  
✅ Good: "Is SK Hynix's HBM business defensible enough to justify current valuation?"

## Step 1.4: Critique and Refine the Plan

The model's first pass is usually 80% right, but it misses angles or creates sub-questions that are too broad. Force it to critique its own work:

```
Critique this research plan:

1. Are there blind spots? What angles am I missing?
2. Are any sub-questions too broad or too narrow?
3. Are dependencies correctly identified?
4. Would a different question structure be more effective?
5. Are there biases in this approach (e.g., only looking at positive sources, ignoring risks)?

Provide your refined version with explanations for changes.
```

**What to look for in the output:**

🟢 **Good sub-questions:**

- Yield 5-10 high-quality sources each    
- Have clear success criteria (you'll know when you've answered it)    
- Can be researched independently (or dependency is explicit)    

🔴 **Bad sub-questions:**

- Would generate 100+ sources (too broad)    
- Would only generate 1-2 sources (too narrow)    
- Require answering 3+ other questions first (too dependent)    

## Step 1.5: Finalize and Document

Copy the refined plan into your Master Document under "Sub-Questions."

Use this format:

```
## Research Objective
[Your main question from the refined plan]

## Sub-Questions (Priority Order)

### Sub-Question 1: [Question text]
- Info needed: [What you're looking for]
- Source types: [Where to look]
- Dependencies: None / Requires SQ[#]
- Priority: 1
- Status: ⬜ Not started

### Sub-Question 2: [Question text]
- Info needed: [What you're looking for]
- Source types: [Where to look]
- Dependencies: None / Requires SQ[#]
- Priority: 2
- Status: ⬜ Not started

[Continue for all 6-8 questions]
```

**Why the checkboxes:** You'll update status as you go. Gives you progress tracking and prevents you from losing track of what's done.

## Decision Point: Ready to Proceed?

Before moving to Phase 2, check:

🟢 **Proceed to Phase 2 if:**

- You have 6-8 sub-questions    
- Each question is specific and answerable    
- Dependencies are clear (you know which to research first)    
- You can explain why each question matters to your objective    

🟡 **Refine if:**

- You have more than 10 sub-questions (too granular - merge some)    
- Questions overlap significantly (consolidate them)    
- You're not sure how to search for answers to any question (make it more specific)    

🔴 **Start over if:**

- Sub-questions don't actually answer your objective (misalignment)    
- Your objective itself is unclear (spend time clarifying what you actually want to know)    
- Dependencies are circular (Question 3 requires Question 5, which requires Question 3)    

## Real Example

**Research Objective:** "Is SK Hynix's HBM business defensible enough to justify current valuation?"

**Refined sub-questions:**

1. **What is SK Hynix's current market position in HBM?** (foundational, priority 1, no dependencies)    
2. **Who are the major competitors and what are their capabilities?** (priority 2, no dependencies) 
3. **What are the key technology barriers to entry in HBM?** (priority 3, requires understanding Q1-Q2)    
4. **How do HBM margins compare to legacy DRAM?** (priority 4, requires Q1)    
5. **What is the demand trajectory for HBM over 3-5 years?** (priority 5, no dependencies)    
6. **How dependent is SK Hynix on specific customers (e.g., NVIDIA)?** (priority 6, requires Q1)    
7. **What risks could disrupt SK Hynix's HBM position?** (priority 7, requires Q1-Q3)    
8. **What valuation multiples are comparable companies trading at?** (priority 8, no dependencies)    

**Dependencies identified:**

- Q3, Q4, Q6, Q7 all require Q1 first (can't analyze technology barriers or margins without understanding current position)    
- Q2, Q5, Q8 can be researched in parallel with Q1    
- This means: Research Q1, Q2, Q5, Q8 first (in parallel) → Then Q3, Q4, Q6, Q7    

## Common Mistakes

**Mistake 1: Skipping dependency mapping**

- You research "HBM margins" before knowing what HBM actually is, then can't interpret the data    

**Mistake 2: Making questions too similar**

- "What is the market size?" vs "What is the TAM?" are the same question - merge them    

**Mistake 3: Creating research rabbit holes**

- "What is the history of semiconductor manufacturing?" sounds important but doesn't answer your objective    

**Mistake 4: Not specifying enough context**

- "What are the risks?" (to what? from what perspective? over what timeframe?)    

**Mistake 5: Perfectionism**

- Spending 45 minutes refining sub-questions - you'll discover gaps in Phase 4 anyway, just move forward
  
---

**Phase 1 Complete.** Save your Master Document. You now have a research roadmap.

Next: **Phase 2: Collect Evidence** (parallel information gathering).

---
# Phase 2: Collect Evidence

## What This Phase Does

Runs focused searches across your sub-questions to gather 5-7 authoritative sources for each. You're casting a wide net to collect raw material - speed and breadth matter more than deep analysis at this stage.

The key technique: **parallelization**. Instead of researching Question 1, then Question 2, then Question 3 sequentially, you launch multiple searches simultaneously and collect results while others are running.

## Why It Matters

This is your raw material collection phase. Without sufficient sources:

- You can't verify claims (single-source risks)    
- You can't spot contradictions (need multiple perspectives)    
- You can't assess evidence quality (need comparison points)    
- Your final report will be thin and unconvincing    

Speed matters because you need to cover all your sub-questions before moving to analysis. Parallelization turns a 2-hour sequential task into a 30-45 minute concurrent one.

## Model Selection

You need a **fast retrieval model** with web search access. Deep reasoning isn't required yet - you're gathering, not analyzing.

**Best:**

- Gemini Pro (fastest for web searches, good at structured output)    
- Perplexity Pro Search (any model, built-in web search)    
- ChatGPT with web browsing enabled    

**Good:**

- Claude with web search (via Anthropic API or integrated platforms)    
- GPT-4o mini (fast and cheap if using API)    

**Budget/Limited options:**

- Manual Google/Bing searches + paste results into any LLM for extraction    
- Use whatever model you have with search capability, prioritize speed over reasoning    

**Why retrieval over reasoning:** You're collecting sources, not synthesizing them yet. A fast model that can pull 5-7 sources in 2-3 minutes beats a slow reasoning model that takes 8 minutes per sub-question.

# Step-by-Step Instructions

## Step 2.1: Choose Your Search Approach

**Option A: Platform with built-in search (Easiest)**

If you're using Perplexity, ChatGPT with browsing, or similar:

- Each sub-question gets its own thread    
- The platform handles web search automatically    
- You just provide the search prompt    

**Option B: Manual search + LLM synthesis**

If you don't have built-in search:

- Use Google/Bing to find sources manually    
- Copy relevant content into your LLM    
- Use the LLM to extract and structure findings    

**Option C: API with web search**

If you're using Claude API or similar:

- Enable web search in API calls (~$10 per 1000 searches via Anthropic)    
- More control but higher cost    
- Best for power users who want maximum flexibility    

**For this guide, we'll write instructions for Option A (built-in search), with notes for Option B.**

## Step 2.2: Create Search Threads

For each sub-question in your plan, create a **new thread**:

1. Open new conversation in your AI platform    
2. Select your **fast retrieval model** (Gemini Pro recommended if available)    
3. Name thread: "[Project] - SQ[#]: [Short description]"    

**Example:** "SK Hynix - SQ1: Market Position"

**Pro tip:** Open 3-4 threads in separate browser tabs/windows right now. While one search runs, you'll be copying results from another. This is how you actually achieve parallelization.

## Step 2.3: Information Gathering Prompt Template

Copy this template into each thread, filling in the specifics for that sub-question:

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

**If using manual search (Option B):** Skip this prompt. Instead, search Google/Bing yourself, find 5-7 sources, copy the URLs and key excerpts into your LLM, then ask: "Extract key findings from these sources in the format above."

## Step 2.4: Execute Parallel Searches

**Launch searches in this order:**

1. Start with **high-priority, independent sub-questions** (no dependencies)    
2. While those run, launch 2-3 more in other tabs    
3. By the time you launch the 4th search, the 1st should be done    
4. Copy the 1st result to your Master Document while 2-4 finish    
5. Continue this pattern until all sub-questions have initial searches    

**Dependency management:**

- Don't start dependent sub-questions until you've reviewed the prerequisite findings    
- Example: Don't search "HBM margins vs DRAM" until you've read "What is HBM" results    

**Common mistake:** Starting all 8 searches at once without checking if early results change how you should phrase later questions. Check dependencies first.

## Step 2.5: Compile Findings in Master Document

As each search completes:

1. **Copy the formatted output** directly into your Master Document under "Phase 2: Evidence Collected"    
2. **Quick quality scan** (don't deep-read yet):    
    - Do you have 5-7 sources?        
    - Are citations complete with working URLs?        
    - Do relevance scores make sense?        
3. **Update status** in your sub-question checklist: ⬜ Not started → ✅ Search complete    

**Don't** reformat, clean up, or analyze deeply yet. Just copy-paste and keep moving. Phase 4 is for quality control.

## Step 2.6: Rolling Verification (Optional but Recommended)

If you have **6+ sub-questions**, consider verifying in batches instead of waiting until Phase 4.

**How it works:**

- After collecting evidence for 2-3 sub-questions, immediately run a mini-verification    
- Catch contradictions or gaps early while context is fresh    
- More manageable than verifying 40+ sources at once    

**When to use rolling verification:**

- Large research projects (8+ sub-questions)    
- Complex topics where early findings might change your approach    
- When you want to maintain quality without overwhelming cognitive load    

**Quick verification prompt** (use your reasoning model):

```
I've gathered initial sources for Sub-Questions [#-#]. Please do a quick verification:

[Paste findings for 2-3 sub-questions]

Check for:
1. Do sources agree or contradict on key facts?
2. Are there obvious gaps or missing perspectives?
3. Should I search for additional sources on any of these?
4. Are there any red flags (outdated data, questionable sources)?

Keep this brief - just flag issues, don't do deep analysis yet.
```

If issues are flagged, run targeted follow-up searches before moving to the next batch.

**Trade-off:** Rolling verification adds 5-10 minutes per batch but prevents you from discovering major gaps after collecting all 40+ sources.

## Decision Point: Evidence Collection Complete?

After collecting sources for all sub-questions, do a final check:

🟢 **Proceed to Phase 3 if:**

- You have 5-7 sources per sub-question (30-50 total sources)    
- Most sources are marked "High" or "Medium" relevance    
- Citations are complete with working URLs    
- You found sources from multiple perspectives (not all bullish or all bearish)    

🟡 **Run targeted follow-up searches if:**

- 2-3 sub-questions only have 3-4 sources (thin coverage)    
- Multiple sub-questions flagged contradictions that need more sources    
- Several sources are marked "Low" relevance (wrong search terms)    
- All sources are from the same type (e.g., only news articles, no primary data)    

🔴 **Revisit Phase 1 if:**

- You consistently can't find 5+ sources per sub-question (questions might be too narrow or poorly framed)    
- Search results are completely off-topic (sub-questions aren't searchable as written)    
- You realize your core objective changed based on what you learned    

## Real Example

**Sub-Question 1:** "What is SK Hynix's current market position in HBM?"

**Search results summary:**

- 7 sources found (2 analyst reports, 2 news articles, 1 earnings transcript, 1 industry data provider, 1 trade publication)    
- All marked "High" relevance    
- Key finding across sources: 50%+ market share in HBM3 (confirmed by 4 independent sources)  
- One contradiction: HBM2E market share varies between "~40%" and "60%" depending on source methodology    
- **Action:** Flagged for Phase 3 deep dive to reconcile the contradiction    

## Common Mistakes

**Mistake 1: Accepting vague citations**

- ❌ "According to industry reports..." (which reports?)    
- ✅ "TrendForce Q4 2025 HBM Market Report, published Dec 2025"    

**Mistake 2: Stopping at first 5 results**

- Models often front-load the most obvious sources    
- If all 5 sources say the same thing with no primary data, push for alternative perspectives    

**Mistake 3: Deep-reading sources now**

- You're gathering, not analyzing    
- Spending 20 minutes reading one source while 7 other sub-questions sit empty kills your momentum    

**Mistake 4: Not checking for date mismatches**

- A 2023 article about "future HBM demand" is speculation, not current data    
- Always check publication date vs the claims being made    

**Mistake 5: Ignoring the "Medium/Low relevance" flags**

- If the model itself flags something as low relevance, ask why it included it    
- Either clarify your search prompt or ask for replacements    

**Mistake 6: Copying the chat history instead of formatted output**

- Don't paste the entire conversation into your Master Document    
- Only copy the structured markdown output the model provided    

---

**Phase 2 Complete.** Your Master Document should now have 30-50 sources organized by sub-question.

Next: **Phase 3: Deep Dive** (analytical synthesis for complex sub-questions).

---
# Phase 3: Deep Dive

## What This Phase Does

Takes complex sub-questions where sources contradict each other or require interpretation, and performs rigorous analysis to extract meaningful insights. This is **selective** - not every sub-question needs a deep dive, only the ones that revealed mess in Phase 2.

You're moving from "here's what sources say" to "here's what this actually means."

## Why It Matters

Some questions can't be answered by just collecting sources. When expert opinions conflict, when data methodologies differ, when context is missing - you need analytical synthesis, not just retrieval.

Without this phase:

- You'll present contradictions without resolving them    
- You'll cite weak evidence as if it's strong    
- You'll miss critical context that changes interpretation    
- Your Phase 5 report will read like a list of sources, not an analysis    

This is what separates surface-level research from actual understanding.

## Model Selection

You need a **reasoning model** with strong analytical capabilities - same type as Phase 1.

**Best:**

- Claude Sonnet 4.5 with Thinking mode    
- o1 or o3    
- DeepSeek-R1    

**Good:**

- Claude Sonnet 3.5    
- Gemini Pro 1.5 with extended reasoning    
- GPT-4o    

**Why reasoning over retrieval:** You're not gathering new information (yet) - you're making sense of contradictions, assessing methodologies, and identifying what's actually missing. This requires analytical thinking, not search speed.

## Step-by-Step Instructions

## Step 3.1: Identify Which Sub-Questions Need Deep Dives

Review your Phase 2 findings. A sub-question needs a deep dive if:

✓ **Sources significantly contradict each other**

- Example: Source A says "50% market share," Source B says "35%"    

✓ **Question requires synthesis across multiple sources**

- Example: "Is the competitive advantage sustainable?" can't be answered by one source    

✓ **Information quality is questionable**

- Example: All sources are opinion pieces with no primary data    

✓ **Initial search revealed unexpected complexity**

- Example: You asked about "HBM demand" and discovered there are 4 different HBM types with different demand drivers    

✓ **Critical context is missing**

- Example: Sources cite numbers but don't explain methodologies    

**Rule of thumb:** Most research projects have 2-3 sub-questions needing deep dives, not all 6-8. If you're flagging more than half, your Phase 1 decomposition might have been too ambitious, or your Phase 2 searches weren't specific enough.

## Step 3.2: Create Deep Analysis Threads

For each flagged sub-question:

1. Open **new thread** in your AI platform    
2. Select your **reasoning model** (Sonnet 4.5 Thinking recommended)    
3. Name thread: "[Project] - Deep Dive: SQ[#]"    

**Example:** "SK Hynix - Deep Dive: SQ4 (HBM Margins)"

**Pro tip:** Keep these separate from your Phase 2 search threads. Clean thread organization prevents context pollution.

## Step 3.3: Deep Analysis Prompt Template

Use this prompt for each deep dive:

```
Context: [Your overall research objective]

Sub-question requiring deep analysis: [The specific question]

Sources gathered in Phase 2:
[Paste all findings from Phase 2 for this sub-question - include sources, quotes, key findings, credibility assessments]

Task: Perform analytical synthesis

1. **Gap Analysis:**
   - What critical information is still missing?
   - Where do sources directly contradict each other?
   - What claims lack sufficient evidence?
   - What additional context is needed to interpret this properly?

2. **Source Quality Assessment:**
   - Which sources are most credible and why?
   - Are there methodological issues with any studies/reports?
   - Do any sources show obvious bias or conflicts of interest?
   - How current is the data (is anything outdated)?

3. **Preliminary Synthesis:**
   - What can we conclude with high confidence?
   - What remains uncertain or contested?
   - What patterns emerge across sources?
   - Are contradictions reconcilable or fundamental disagreements?

4. **Additional Search Strategy:**
   - What specific searches would resolve the most important gaps/contradictions?
   - What alternative sources should we explore?
   - Are there primary sources (company filings, government data) we should consult?

Show your reasoning process step-by-step. Assign confidence levels (High/Medium/Low) to each conclusion.
```

**What you're looking for in the output:**

- Explicit identification of what's solid vs what's shaky    
- Explanations for why sources contradict (different timeframes? different definitions? different methodologies?)    
- Prioritized list of what additional research would actually help    

## Step 3.4: Execute Targeted Follow-Up Searches

Based on the model's gap analysis, run **focused searches** to fill critical gaps.

**Don't:** Start another broad search generating 5-7 sources  
**Do:** Run laser-focused searches for specific missing pieces

**Follow-up search prompt** (use your fast retrieval model):

```
Targeted search based on gap analysis:

Gap identified: [Specific gap from deep dive analysis]

Task: Find 2-3 high-quality sources specifically addressing this gap

[Paste the "Additional Search Strategy" recommendation from your deep dive]

Use the same structured output format as Phase 2.
```

**Example:**

- **Gap:** "Market share numbers vary because sources use different definitions (HBM2E vs HBM3 vs combined)"    
- **Targeted search:** "SK Hynix HBM market share breakdown by generation HBM2E HBM3 2025"   

**Stop rule:** Limit yourself to 2-3 follow-up searches per sub-question. If you're still confused after that, the question itself might need reframing.

## Step 3.5: Update Master Document

Add deep dive findings to your Master Document under the relevant sub-question:

```
### Sub-Question [#]: [Question]
Status: ✅ Deep analysis complete

[Phase 2 sources remain here]

#### Deep Dive Analysis:

**Key Contradictions:**
- [Contradiction 1 and explanation]
- [Contradiction 2 and explanation]

**Confidence Assessments:**
- **High confidence:** [Claims with strong, consistent evidence]
  - Sources: [#, #, #]
- **Medium confidence:** [Claims with moderate evidence or minor contradictions]
  - Sources: [#, #]
  - Caveat: [What's uncertain]
- **Low confidence:** [Claims with weak or contradictory evidence]
  - Sources: [#]
  - Issue: [Why this is unreliable]

**Remaining Gaps:**
- [Gap 1 - Critical/Nice-to-have]
- [Gap 2 - Critical/Nice-to-have]

**Follow-up Sources:**
[Any additional sources found, using same format as Phase 2]
```

**Why this structure matters:** Phase 4 (quality check) needs to know which claims you're confident about and which are shaky. Documenting it here prevents you from overstating weak claims in your final report.

## Decision Point: Deep Dives Complete?

After analyzing flagged sub-questions:

🟢 **Proceed to Phase 4 if:**

- Major contradictions are explained or resolved    
- You have confidence assessments for key claims    
- Remaining gaps are "nice-to-have" not "critical"    
- You can answer your sub-questions even if not perfectly    

🟡 **Run more targeted searches if:**

- Critical gaps remain (you can't answer the sub-question at all)    
- New contradictions emerged that need one more source    
- You found a much better source type you should have searched initially    

🔴 **Revisit Phase 1 if:**

- The sub-question is fundamentally unanswerable with available information    
- You realize the question itself was wrong based on what you learned    
- Dependencies were wrong (this question requires answering 3 others first)    

## Real Example

**Sub-Question 4:** "How do HBM margins compare to legacy DRAM?"

**Phase 2 problem:**

- 2 sources claimed "2-3x higher margins"    
- 2 sources claimed "comparable margins"    
- 1 source said "initially high but compressing"    

**Deep dive findings:**

- **Reconciliation:** Sources use different margin definitions (gross margin vs operating margin)    
- Analyst reports (gross margin): HBM is 2-3x DRAM    
- Company filings (operating margin): HBM is 1.5x DRAM after R&D costs    
- Trade publication (forward-looking): Margins compressing as competition increases    
- **Conclusion:** All sources are partially correct - depends on timeframe and margin definition    
- **High confidence claim:** "HBM gross margins are currently 2-3x legacy DRAM"    
- **Medium confidence claim:** "Operating margins are lower due to high R&D, roughly 1.5x"    
- **Low confidence claim:** "Margins will compress significantly by 2027" (only one forward-looking source)    

**Follow-up search:** Found SK Hynix investor presentation with margin guidance, added as 8th source for this sub-question

## Common Mistakes

**Mistake 1: Deep diving everything**

- Not every sub-question needs this    
- If 5 sources agree and provide clear evidence, move on    

**Mistake 2: Accepting "we can't know" too easily**

- Sometimes contradictions mean you need better sources, not that truth is unknowable    
- Try primary sources (company filings, government data) before giving up    

**Mistake 3: Getting stuck in infinite research loops**

- Each deep dive leads to 5 new questions    
- Stay focused on your original sub-question - note tangential questions but don't chase them    

**Mistake 4: Not documenting why sources contradict**

- "Sources disagree" is not analysis    
- "Sources disagree because A uses 2024 data and B uses 2025 projections" is analysis    

**Mistake 5: Ignoring source quality differences**

- Not all sources are equal    
- A company's own filing beats a blog post's speculation    

**Mistake 6: Deep diving too early**

- If you only have 3 sources for a sub-question, you probably need more sources (Phase 2), not deep analysis    

---

**Phase 3 Complete.** Your Master Document now has analytical synthesis for complex sub-questions, with confidence levels assigned to key claims.

Next: **Phase 4: Check Quality** (cross-verification and gap analysis across all sub-questions).

---

# Phase 4: Check Quality

## What This Phase Does

Analyzes all gathered research holistically to identify single-source claims, contradictions, evidence quality issues, and gaps. This is your quality control gate before you start writing.

You're stepping back from individual sub-questions to look at the complete picture: Do your findings actually answer your research objective? Where are the weak spots? What's missing?

## Why It Matters

Without cross-verification:

- Single-source claims slip through (high risk of error)    
- Contradictions between sub-questions go unnoticed    
- You overstate confidence on weak evidence    
- Critical gaps only become obvious after you've written the report    
- You waste time writing sections you'll need to rewrite    

This phase is your bullshit detector. It catches issues before they become conclusions.

## Model Selection

You need a **reasoning model with large context window** - you'll be pasting 30-50 sources worth of findings.

**Best:**

- Claude Sonnet 4.5 (200K context, conservative reasoning)    
- Gemini Pro 1.5 (1M context if you have massive source sets)    
- o1 or o3    

**Good:**

- Claude Sonnet 3.5    
- GPT-4o (128K context)    

**Why long context matters:** You need the model to hold all your findings in memory simultaneously to spot contradictions between Sub-Question 2 and Sub-Question 7. Short context windows force you to verify in smaller chunks, which misses cross-question issues.

## Step-by-Step Instructions

## Step 4.1: Create Master Verification Thread

1. Open **new thread** in your AI platform    
2. Select your **reasoning model** (Sonnet 4.5 recommended)    
3. Name thread: "[Project] - Phase 4: Quality Check"    

**Pro tip:** Save this thread URL in your Master Document. You'll reference this verification output constantly when writing your report.

## Step 4.2: Compile All Research

From your Master Document, create one comprehensive compilation:

```
Research Objective: [Your main question]

Complete findings from Phases 2 & 3, organized by sub-question:

## Sub-Question 1: [Question]
[All sources, findings, quotes, deep dive analysis if applicable]

## Sub-Question 2: [Question]
[All sources, findings, quotes, deep dive analysis if applicable]

[Continue for all sub-questions]

---
Total sources reviewed: [Count]
High-credibility sources: [Count]
Date range: [Oldest to newest source]
Sub-questions with deep dives: [List which ones]
```

**Just copy-paste everything from your "Phase 2: Evidence Collected" section.** Don't summarize or clean it up - the model needs full context.

## Step 4.3: Comprehensive Verification Prompt

Use this prompt to run the quality check:

```
I've completed comprehensive research on [topic]. Here are all findings:

[Paste your complete compilation from Step 4.2]

Task: Perform rigorous cross-verification and gap analysis

1. **Single-Source Claims (High Risk):**
   - Identify important claims appearing in only 1 source
   - Assess: Should we verify with additional searches or flag as uncertain?
   - Separate: "Critical to verify" vs "acceptable as single-source"

2. **Contradictions Analysis:**
   - Where do sources directly contradict on facts (not just opinions)?
   - Which sources are more credible on contested points and why?
   - Can contradictions be reconciled (different definitions, timeframes) or are they fundamental disagreements?
   - Are there contradictions *between* sub-questions (findings that don't align)?

3. **Evidence Quality Assessment:**
   - **Strong evidence** (multiple credible sources, primary data, recent): [List key claims]
   - **Moderate evidence** (2-3 sources, secondary data, or some age): [List key claims]
   - **Weak evidence** (single source, opinion-based, outdated): [List key claims]

4. **Coverage Completeness:**
   - Which sub-questions are thoroughly answered?
   - Which sub-questions remain partially answered?
   - Do our findings actually answer the original research objective?
   - What new questions emerged that we didn't anticipate?

5. **Blind Spots & Biases:**
   - Are certain perspectives over-represented or under-represented?
   - Are sources geographically or temporally biased (all from one region, all from one year)?
   - What assumptions underlie our research approach that might be wrong?
   - What alternative interpretations of the data exist?

6. **Additional Research Needs:**
   - **Critical gaps** (must fill before writing): [Prioritized list]
   - **Nice-to-have** (would strengthen but not essential): [List]
   - **Unanswerable** (can't be resolved with available information): [List]

7. **Overall Completeness Assessment:**
   - Rate research completeness: [0-100%]
   - Justification for rating
   - What would move us to 90%+ completeness?

Organize output with clear sections. Be ruthless - I need honest assessment, not reassurance.
```

**What you're asking the model to do:** Act as an adversarial fact-checker on your own research. The seven-part structure catches different failure modes systematically.

## Step 4.4: Decision Point - Completeness Rating

Review the model's completeness assessment:

🟢 **Proceed to Phase 5 if:**

- **90%+ completeness** rating    
- Critical gaps are addressed    
- Contradictions are explained or resolved    
- Evidence quality is sufficient for your objective    
- You can answer your research objective with confidence    

🟡 **Address critical gaps if:**

- **70-89% completeness** rating    
- 2-3 critical gaps identified that are researchable    
- Major contradictions need one more source to resolve    
- Evidence quality is weak on core claims (not tangential details)    

**Action:** Run targeted searches for highest-priority gaps only, then re-run a lighter verification:

```
I've addressed the following gaps from your analysis:
[List gaps + new sources found]

Quick re-check:
- Are these gaps sufficiently filled?
- Does this move us to 90%+ completeness?
- Any new issues introduced by these sources?
```

🔴 **Major revision needed if:**

- **Below 70% completeness** rating    
- Many sub-questions poorly answered    
- Research objective itself seems wrong based on findings    
- Fundamental contradictions can't be resolved    

**Action:** Return to Phase 2 for substantial additional research, or return to Phase 1 to reframe your objective.

## Step 4.5: Update Master Document with Verification Results

Add a new section to your Master Document:

```
## Phase 4: Quality Check Results

**Completeness Rating:** [X]%

**Research Status:** Ready for synthesis / Needs gap filling / Requires major revision

### High-Confidence Findings:
- [Finding 1] - Sources: [cite which ones]
- [Finding 2] - Sources: [cite which ones]

### Moderate-Confidence Findings:
- [Finding 3] - Sources: [cite which ones] - Caveat: [what's uncertain]
- [Finding 4] - Sources: [cite which ones] - Caveat: [what's uncertain]

### Low-Confidence / Uncertain:
- [Finding 5] - Source: [cite] - Issue: [why this is weak]

### Key Contradictions & Resolutions:
1. **[Topic]:** Source X claims [A], but Source Y claims [B]
   - **Resolution:** [Which is more credible and why, or how they're reconcilable]

2. **[Topic]:** [Another contradiction]
   - **Resolution:** [Explanation]

### Critical Gaps Addressed:
- [Gap 1] - Status: Filled / Acceptable to leave / Flagged in report

### Remaining Limitations:
- [Limitation 1] - Will acknowledge in report
- [Limitation 2] - Will acknowledge in report

### Unexpected Discoveries:
- [Discovery 1 - something interesting you didn't anticipate]
- [Discovery 2]
```

**Why this section is critical:** This becomes your roadmap for Phase 5. When drafting your report, you'll know exactly which claims to state confidently, which to hedge, and which contradictions to acknowledge explicitly.

## Decision Point: Ready to Write?

Before proceeding to Phase 5:

🟢 **Yes, proceed if:**

- You have clear confidence levels for all major claims    
- Contradictions are explained (even if not fully resolved)    
- You know what limitations to acknowledge    
- The completeness rating justifies moving forward    
- You can articulate your answer to the research objective    

🟡 **Do targeted gap-filling if:**

- 1-2 critical gaps are researchable and would significantly strengthen findings    
- One major contradiction needs resolution before you can take a position    
- A key sub-question is still too thin to write about    

🔴 **Don't proceed yet if:**

- You can't confidently answer your research objective    
- Multiple sub-questions remain poorly researched    
- You're uncertain which claims are reliable    

## Real Example

**Completeness Rating:** 85%

**High-confidence findings:**

- SK Hynix has 50%+ HBM3 market share (4 independent sources, all Q4 2025 data)    
- HBM gross margins are 2-3x legacy DRAM (3 analyst reports, 1 company filing)    
- NVIDIA is largest customer, ~40% of HBM revenue (2 sources + company disclosure)    

**Moderate-confidence findings:**

- HBM demand will grow 60% CAGR through 2027 (3 analyst projections, wide range 50-80%)    
- Technology barriers remain high for new entrants (supported by expert opinions, but not quantified)    

**Low-confidence/uncertain:**

- China HBM demand projections (only 1 source, highly speculative)    
- Impact of potential NVIDIA in-house memory development (mentioned in 1 article, no concrete plans)    

**Key contradiction:**

- HBM2E market share varies 40-60% depending on whether Korean or Taiwanese fabs are included in denominator    
- **Resolution:** Will specify "ex-China market share" in report    

**Critical gap addressed:**

- Added primary source (SK Hynix Q4 2025 earnings call) for margin guidance    

**Remaining limitation:**

- All margin projections are from sell-side analysts (potential bullish bias) - will acknowledge in report    

**Unexpected discovery:**

- SK Hynix is capacity-constrained, not demand-constrained (changes investment thesis implications)    

## Common Mistakes

**Mistake 1: Ignoring the completeness rating**

- Model says 60% complete, you proceed anyway because you're tired    
- Your final report will reflect that 60% quality    

**Mistake 2: Not documenting contradictions**

- You mentally reconciled them but didn't write it down    
- When writing Phase 5, you forget how you resolved it and get confused    

**Mistake 3: Treating all gaps equally**

- "Nice-to-have" gaps don't need filling    
- Only chase "critical" gaps that actually matter for your objective    

**Mistake 4: Skipping this phase entirely**

- "I verified as I went in Phase 2/3, I'm good"    
- Cross-question contradictions only emerge when you look at everything together    

**Mistake 5: Being too harsh or too lenient**

- Too harsh: "One source disagrees, everything is uncertain" (paralysis)    
- Too lenient: "Most sources agree, that one outlier doesn't matter" (overconfidence)    
- Balance: Assess evidence proportionally    

**Mistake 6: Not separating facts from interpretation**

- Facts: "Revenue was $X" (verifiable, can have high confidence)    
- Interpretation: "This means competitive advantage is strong" (analytical, inherently uncertain)    

---

**Phase 4 Complete.** Your Master Document now has a complete quality assessment with confidence levels, contradiction resolutions, and identified gaps.

Next: **Phase 5: Write Report** (synthesis and generation).

---
# Phase 5: Write Report

## What This Phase Does

Transforms all your research into a coherent narrative with proper structure, citations, and confidence levels for each claim. You're moving from raw findings to polished analysis that someone can actually read and act on.

The key technique: **section-by-section drafting**. You don't ask the AI to write a 3,000-word report in one shot. You draft one section at a time, maintaining quality control at each step.

## Why It Matters

Research isn't useful until it's communicated clearly. You've done the hard work of gathering and verifying - but if your report is poorly structured, buries key findings, or makes unsupported claims, that work is wasted.

Without structured synthesis:

- Key findings get lost in walls of text    
- Readers can't distinguish high-confidence claims from speculation    
- Citations are missing or vague    
- Contradictions are smoothed over instead of acknowledged    
- The logic doesn't flow (readers can't follow your reasoning)    

This phase is where research becomes actionable.

## Model Selection

You need a **reasoning model with strong writing capabilities** - same as Phase 1 and 3.

**Best:**

- Claude Sonnet 4.5 with Thinking mode (excellent at structured long-form writing with proper citations)    
- o1 or o3    
- GPT-4o    

**Good:**

- Claude Sonnet 3.5    
- Gemini Pro 1.5    
- DeepSeek-R1    

**Why reasoning over retrieval:** You're synthesizing complex information into logical arguments, not gathering new data. You need a model that maintains consistent voice, proper citation hygiene, and logical flow across multiple sections.

## Step-by-Step Instructions

## Step 5.1: Create Report Structure

In your Master Document, create this outline (customize based on your needs):

```
# [Research Project Title]

## Executive Summary
[Write this LAST - 2-3 paragraphs summarizing everything]

## Research Objective & Methodology
### Primary Question
### Sub-Questions Investigated
### Sources & Approach
### Limitations & Caveats

## Key Findings
### [Sub-Question 1 Topic]
### [Sub-Question 2 Topic]
### [Continue for all sub-questions]

## Analysis & Synthesis
### Cross-Cutting Themes
### Contradictions & Uncertainties
### Confidence Assessment by Claim

## Conclusions
### High-Confidence Conclusions
### Moderate-Confidence Conclusions
### Areas for Further Research

## Sources
[All citations organized]
```

**Why this structure:**

- Executive Summary for busy readers who want the answer now    
- Methodology for skeptics who want to assess your approach    
- Key Findings for detail-oriented readers    
- Analysis for strategic thinkers who want interpretation    
- Conclusions for decision-makers who need clear takeaways    

**Customize based on your audience.** Academic research needs different structure than investment analysis or product decisions.

## Step 5.2: Create Report Generation Thread

1. Open **new thread** in your AI platform    
2. Select your **reasoning model** (Sonnet 4.5 recommended)    
3. Name thread: "[Project] - Phase 5: Report Writing"    

**Critical:** You will draft **one section at a time** in this thread. Do not ask the model to draft the entire report at once - quality degrades in longer generations, and you lose control.

## Step 5.3: Section-by-Section Drafting

**Recommended drafting order:**

1. **Research Objective & Methodology** (easiest, sets context)    
2. **Key Findings sections** (one sub-question at a time, bulk of report)    
3. **Analysis & Synthesis** (requires full context from findings)    
4. **Conclusions** (builds on analysis)    
5. **Executive Summary** (write LAST, summarizes everything)    
6. **Sources** (organizational task, can be templated)    

**Prompt template for each section:**

```
Context: I'm writing a comprehensive research report on [topic]

Research objective: [Your main question]

Relevant findings for this section:
[Paste specific findings from your Master Document that relate to this section]

Phase 4 verification results for these findings:
[Paste confidence assessments, contradiction resolutions, limitations]

Task: Draft the following section of my report

Section: [Section name - e.g., "Key Findings: Market Position Analysis"]

Requirements:
- Length: [Specify - e.g., 400-600 words, 3-4 paragraphs]
- Tone: Analytical, professional, objective
- Citation style: Inline citations [Source #] format
- Include specific data/quotes from sources where relevant
- Flag uncertain claims explicitly (e.g., "estimates suggest..." or "limited data indicates...")
- Acknowledge contradictions between sources where they exist
- Structure with clear topic sentences

Specific elements to include:
- [Element 1 - e.g., current market share with specific numbers]
- [Element 2 - e.g., comparison to competitors]
- [Element 3 - e.g., trend over time]

Draft this section now. Use confidence language that matches the evidence quality from Phase 4.
```

**What you're doing:** Giving the model everything it needs to write one focused section - the findings, the quality assessment, the structure requirements. This maintains quality and keeps you in control.

## Step 5.4: Iterative Section Refinement

For each section draft:

1. **Review against Phase 4 verification results**    
    - Are confidence levels accurate?        
    - Are contradictions acknowledged?        
    - Are limitations mentioned?        
2. **Check citation quality**
    
    - Every factual claim has a citation?        
    - Citations are specific (not "multiple sources")?        
    - High-confidence claims cite multiple sources?        
3. **If refinement needed:**    

```
Refinement needed on [section name]:

Issues:
- [Issue 1 - e.g., Missing citation for claim in paragraph 2]
- [Issue 2 - e.g., Tone too assertive given "moderate confidence" rating in Phase 4]
- [Issue 3 - e.g., Contradiction between Source 3 and Source 7 not acknowledged]

Revise section addressing these issues.
```

4. **Copy approved section** into Master Document under "Phase 5: Final Report"    
5. **Move to next section**    

**Quality check between sections:** After drafting 2-3 sections, read them in sequence. Do they flow logically? Is voice consistent? Are you repeating information? Catch structural issues before you've drafted 10 sections.

## Step 5.5: Handle Contradictions and Uncertainty

**Good research acknowledges what it doesn't know.** Use confidence-appropriate language:

**High confidence (multiple credible sources agree):**

- "Data shows..."    
- "Analysis confirms..."    
- "[Specific number] according to [3 sources]..."    

**Moderate confidence (2-3 sources, or methodology questions):**

- "Available evidence suggests..."    
- "Most sources indicate..."    
- "Estimates range from X to Y..."    

**Low confidence (single source, opinion-based, contradictory):**

- "Limited data suggests..."    
- "One source claims... though this lacks independent verification..."    
- "Conflicting reports indicate..."    

**Contradictions that can't be resolved:**

- Don't pick a side arbitrarily    
- Present both perspectives with source quality context    
- Example: "Analyst reports estimate 60% market share [Sources 2, 5], while industry data providers suggest 45% [Source 8]. The discrepancy likely stems from different denominator definitions (global vs. ex-China market)."    

## Step 5.6: Write Executive Summary Last

After all other sections are complete:

```
I've completed my full research report (attached below).

[Paste entire report]

Task: Write a 2-3 paragraph Executive Summary

Requirements:
- First paragraph: Direct answer to the research objective
- Second paragraph: 3-4 most important supporting findings
- Third paragraph (optional): Key limitations/uncertainties and what they mean
- Length: 250-400 words total
- Tone: Confident where evidence is strong, appropriately cautious where uncertain
- No citations needed (they're in the full report)

This should work as a standalone summary - someone reading only this should understand your conclusion and key evidence.
```

**Why last:** You can't summarize what doesn't exist yet. Drafting executive summary first leads to vague platitudes. Draft it last and it will be sharp and specific.

## Decision Point: Report Quality Check

Before considering the report complete:

🟢 **Ready for Phase 6 if:**

- All sections written and flow logically    
- Every factual claim has proper citation    
- Confidence language matches Phase 4 assessments    
- Contradictions and limitations are acknowledged    
- Executive summary accurately reflects full report    
- You can give this to someone and they'd understand your findings    

🟡 **Needs revision if:**

- Sections feel repetitive (consolidate)    
- Citations are vague or missing in places (add specificity)    
- Tone is inconsistent between sections (standardize)    
- Key findings from Phase 4 missing from report (add them)    

🔴 **Major rewrite needed if:**

- Report doesn't actually answer your research objective (misalignment)    
- Findings contradict each other without explanation (logic failure)    
- Heavy reliance on low-confidence claims presented as facts (overstatement)    

## Real Example

**Section: Key Findings - Market Position**

**Draft excerpt:**

> SK Hynix currently holds the leading position in the high-bandwidth memory (HBM) market, with market share estimates ranging from 50-60% in HBM3 production as of Q4 2025 [Sources 2, 5, 8, 12]. This position is supported by the company's early investment in HBM technology and established relationships with major AI chip manufacturers, particularly NVIDIA, which accounts for approximately 40% of SK Hynix's HBM revenue [Source 12, Company Disclosure].
> 
> However, this market leadership faces increasing competitive pressure. Samsung has ramped HBM3 production capacity throughout 2025 and aims to capture 30% market share by end of 2026 [Sources 5, 9]. Micron entered the HBM market in Q2 2025, though current production volumes remain small [Source 14]. The market share data shows some variance depending on methodology - figures citing "global market share" typically show lower percentages for SK Hynix (45-50%) compared to those measuring "ex-China capacity" (55-60%), as Chinese domestic production is not included in most industry datasets [Sources 2, 8].

**What makes this good:**

- Specific numbers with multiple source citations    
- Acknowledges data variance and explains why    
- Moderate confidence language ("estimates ranging")    
- Context provided (why variance exists)    
- Both strengths and challenges mentioned    

## Step 5.7: Organize Sources Section

Create a clean, numbered source list at the end:

```
## Sources

1. [Author/Organization]. "[Title]." [Publication], [Date]. [URL]
2. [Author/Organization]. "[Title]." [Publication], [Date]. [URL]
[Continue for all sources]
```

**Match the source numbers to your in-text citations.** If you cited [Source 12] in the report, it should be #12 in this list.

## Common Mistakes

**Mistake 1: Writing the whole report in one shot**

- Quality degrades after ~1,000 words in a single generation    
- You lose control over structure and accuracy    
- Section-by-section is slower but produces better results    

**Mistake 2: Vague citations**

- ❌ "According to industry reports..."    
- ❌ "Multiple sources indicate..."    
- ✅ "According to TrendForce Q4 2025 report [Source 3] and Gartner analysis [Source 7]..."    

**Mistake 3: Overstating weak evidence**

- Phase 4 flagged something as "low confidence"    
- Phase 5 report presents it as established fact    
- Always match confidence language to evidence quality    

**Mistake 4: Burying the lede**

- Most important finding is in paragraph 5    
- Lead with the answer to your research objective    

**Mistake 5: Not acknowledging limitations**

- Every research project has limitations    
- Acknowledging them builds credibility, doesn't undermine it    

**Mistake 6: Copy-pasting entire chat history**

- Only paste the clean drafted sections into Master Document    
- Don't include the back-and-forth with the model    

**Mistake 7: Skipping executive summary**

- "The report speaks for itself"    
- Most readers will only read the executive summary - make it count    

---

**Phase 5 Complete.** Your Master Document now contains a complete, well-cited research report.

Next: **Phase 6: Stress Test** (adversarial review to find flaws before anyone else does).

---
# Phase 6: Stress Test

## What This Phase Does

Uses a fresh model to ruthlessly critique your report, finding logical flaws, missing evidence, alternative interpretations, and blind spots. This is red-teaming your own work - you want to find problems now, not after you've shared it.

The key: **adversarial perspective**. You're too close to your research. You'll miss obvious gaps, over-rely on favorite sources, or state conclusions more confidently than evidence supports. A fresh model catches what you can't see.

## Why It Matters

This phase separates thoughtful research from content that just looks good on first read.

Without adversarial review:

- Logical flaws slip through (conclusion doesn't follow from evidence)    
- Alternative interpretations go unconsidered    
- You're blindsided by questions your audience will obviously ask    
- Weak arguments that you rationalized get exposed later    
- Your work gets dismissed because of fixable issues you didn't catch    

**This is optional** - skip it for low-stakes research. But for high-stakes decisions (investment, strategy, major purchases, anything you'll be questioned on), this 15-20 minutes is what makes your work defensible.

## Model Selection

**Critical rule:** Use a **different model** than you used for Phase 5 writing.

If you wrote with Claude, critique with GPT or Gemini.  
If you wrote with GPT, critique with Claude.  
If you wrote with Gemini, critique with Claude or GPT.

**Why different models matter:** Each model has different biases, reasoning patterns, and blind spots. A fresh model perspective catches issues the writing model missed or smoothed over. It's like having a colleague review your work instead of rereading it yourself.

**Best critique models:**

- GPT-4o or o1 (excellent at finding logical inconsistencies)    
- Claude Sonnet 4.5 (conservative, catches overstatements)    
- Gemini Pro 1.5 (good at alternative perspectives)    

**Choose based on what you used for Phase 5:**

- Used Claude → Critique with GPT    
- Used GPT → Critique with Claude    
- Used Gemini → Critique with Claude or GPT    

## Step-by-Step Instructions

## Step 6.1: Create Adversarial Review Thread

1. Open **new thread** in your AI platform    
2. Select your **critique model** (different from Phase 5)    
3. Name thread: "[Project] - Phase 6: Adversarial Review"    

**Why new thread:** You want zero context from your previous work. The critic should see only the final report, not your research journey.

## Step 6.2: Adversarial Review Prompt

Paste your complete report from Phase 5, then use this prompt:

```
I need you to critique this research report ruthlessly. Your job is to find flaws, not reassure me.

[Paste complete report including executive summary, all sections, and sources]

Task: Adversarial review to identify weaknesses before this goes to stakeholders

1. **Logical Flaws:**
   - Do conclusions actually follow from the evidence presented?
   - Are there logical leaps or unsupported assumptions?
   - Does the executive summary accurately reflect the detailed findings?

2. **Evidence Quality Issues:**
   - Are claims stated more confidently than evidence warrants?
   - Are key claims supported by sufficient sources?
   - Are there outdated sources being treated as current?
   - Is evidence cherry-picked (only supporting one view)?

3. **Missing Perspectives:**
   - What counterarguments or alternative interpretations aren't addressed?
   - What questions would a skeptical reader immediately ask?
   - Are there obvious angles this analysis ignores?

4. **Structural & Clarity Issues:**
   - Is anything confusing or poorly explained?
   - Are sections repetitive or contradictory?
   - Does the report answer the stated research objective?

5. **Citation & Methodology Issues:**
   - Are citations specific enough to verify?
   - Are limitations and biases adequately acknowledged?
   - Is the methodology transparent?

For each issue you identify:
- Rate severity (Critical / Important / Minor)
- Explain why it's a problem
- Suggest how to fix it

Be specific. Instead of "needs more evidence," tell me exactly what claim needs what kind of evidence.

Organize output by severity: Critical issues first, then Important, then Minor.
```

**What you're doing:** Asking the model to act as your harshest critic, not your supporter. The severity ratings help you prioritize what actually needs fixing.

## Step 6.3: Review and Discuss the Critique

Read through the critique. You won't agree with everything - that's normal. Some "issues" are judgment calls or the model misunderstanding context.

**For issues you disagree with:**

```
I disagree with [issue #X] for the following reason:
[Your explanation]

Is this a valid counterargument, or am I being defensive?
```

Go back and forth until you reach agreement on what's actually a problem vs. what's acceptable.

**For issues you agree with:**

Mark them as:

- **Must fix** (critical issues that undermine credibility)    
- **Should fix** (important issues that strengthen the report)    
- **Nice to fix** (minor improvements, only if time permits)    

## Step 6.4: Export the Final Critique

Once you've discussed and agreed on issues:

```
Based on our discussion, provide the final critique list organized by priority:

**Must Fix:**
- [Issue 1 with explanation and fix suggestion]
- [Issue 2 with explanation and fix suggestion]

**Should Fix:**
- [Issue 3 with explanation and fix suggestion]

**Consider:**
- [Issue 4 with explanation and fix suggestion]

Format this in markdown so I can copy it into my working document.
```

Copy this formatted critique into your Master Document under a new section:

```
## Phase 6: Adversarial Review Results

### Must Fix:
- [Issue with fix approach]

### Should Fix:
- [Issue with fix approach]

### Consider (if time):
- [Issue with fix approach]

### Dismissed (with justification):
- [Issue you decided not to address and why]
```

**Why document dismissed issues:** When someone later asks "Did you consider X?", you can say "Yes, here's why I didn't include it" instead of "Oh, I didn't think of that."

## Decision Point: How Much to Fix?

🟢 **Proceed to Phase 7 if:**

- Critical issues identified (must be fixed)    
- Important issues identified that would strengthen report    
- You have specific action items for improvement    
- Or: No major issues found (rare but possible if Phase 4-5 were thorough)    

🟡 **Skip Phase 7 if:**

- Only minor issues identified    
- Low-stakes research where perfection isn't needed    
- Time constraints (acknowledge limitations in report instead)    

🔴 **Return to Phase 4 or 5 if:**

- Multiple critical logical flaws identified    
- Evidence quality issues are fundamental    
- Report doesn't actually answer research objective    
- Major restructuring needed    
## Real Example

**Critique excerpt for SK Hynix report:**

**Critical Issues:**

1. **Overconfident margin projection**    
    - Problem: Report states "HBM margins will remain 2-3x DRAM through 2027" as high confidence        
    - Evidence: Only 3 sources, all sell-side analysts with bullish bias, no company guidance beyond 2026        
    - Fix: Downgrade to medium confidence, add caveat about analyst bias, acknowledge compression risk        
    - **Severity: Critical** (could lead to bad investment decision)        
2. **Missing competitive threat analysis**    
    - Problem: Report focuses on Samsung/Micron but doesn't address risk of customers (NVIDIA, AMD) developing in-house memory        
    - Evidence: One source mentions this possibility but it's dismissed without analysis        
    - Fix: Add paragraph in risk section addressing vertical integration risk, even if probability is low        
    - **Severity: Critical** (obvious question stakeholders will ask)        

**Important Issues:**

3. **China market analysis is superficial**    
    - Problem: Report mentions China demand once but doesn't analyze impact of export controls        
    - Evidence: Multiple sources discuss this, but report doesn't synthesize        
    - Fix: Add 2-3 paragraphs on China impact (both demand destruction and domestic production threats)        
    - **Severity: Important** (material to investment thesis)        

**Minor Issues:**

4. **Repetitive explanation of HBM technology**    
    - Problem: HBM definition appears in 3 different sections        
    - Fix: Define once in methodology, reference thereafter        
    - **Severity: Minor** (readability issue, not accuracy)        

**Response:**

- Issues 1-3: Agreed, will fix in Phase 7    
- Issue 4: Agreed it's repetitive, but keeping for standalone section readability (different readers skip to different sections)  

## Common Mistakes

**Mistake 1: Using the same model you wrote with**

- Same model, same biases, same blind spots    
- You need a fresh perspective, not a consistency check    

**Mistake 2: Being defensive**

- "The critic doesn't understand my methodology"    
- Maybe, but if the critic is confused, your readers will be too    

**Mistake 3: Fixing everything the model mentions**

- Some "issues" are judgment calls    
- Discuss with the model, push back where appropriate    

**Mistake 4: Skipping this for "quick" research**

- Then finding out your boss or client has obvious questions you didn't consider    
- 20 minutes here saves hours of embarrassment later    

**Mistake 5: Not documenting dismissed issues**

- You'll forget why you decided something wasn't important    
- When questioned later, you'll look unprepared    

**Mistake 6: Running critique on partial draft**

- Critique needs the complete report to catch logical flow issues    
- If you're still drafting sections, finish Phase 5 first    

**Mistake 7: Treating all severity levels equally**

- "Critical" means "undermines core credibility" - must fix these    
- "Minor" means "nice improvement" - only if time allows    
- Prioritize ruthlessly    

---

**Phase 6 Complete.** You now have a prioritized list of improvements to make your report defensible.

Next: **Phase 7: Polish** (incorporate critiques and finalize).

---
# Phase 7: Polish

## What This Phase Does

Takes the critique from Phase 6 and iteratively refines your report, addressing valid issues while maintaining your core arguments. This is the final polish - where you incorporate hard-won feedback and transform good research into excellent research.

You're not rewriting from scratch. You're surgically fixing identified problems and strengthening weak points.

## Why It Matters

The Phase 6 critique is useless if you don't act on it. This phase forces you to:

- Confront weaknesses in your arguments    
- Strengthen evidence where it's thin    
- Acknowledge uncertainty where appropriate    
- Address questions readers will obviously ask    

**Combined with Phase 6, this is what separates your work from poorly generated content.** Most people skip adversarial review entirely. You're doing the extra 10% that makes work 99% better.

## Model Selection

**Return to the model you used for Phase 5 writing.**

If you wrote with Claude, revise with Claude.  
If you wrote with GPT, revise with GPT.  
If you wrote with Gemini, revise with Gemini.

**Why the same model:** You want consistency in voice and style. Switching models mid-revision creates tone inconsistencies. The Phase 6 critique already gave you the fresh perspective - now you need execution.

**Best:**

- Whatever you used successfully in Phase 5    
- Claude Sonnet 4.5 (if that's what you used before)    
- GPT-4o or o1 (if that's what you used before)    
- Gemini Pro 1.5 (if that's what you used before)    

## Step-by-Step Instructions

## Step 7.1: Prioritize What to Fix

Review your Phase 6 critique and decide what you're actually addressing:

**Must address:**

- All "Critical" issues    
- All "Important" issues that don't require new research    

**Address if time permits:**

- "Minor" issues that improve readability    
- "Important" issues that require going back to Phase 2 (only if you have time and they're truly important)    

**Explicitly skip:**

- Issues you discussed and dismissed    
- Nice-to-have improvements on low-stakes research    
- Anything requiring entirely new research unless absolutely critical    

**Create a fix list:**

```
## Phase 7: Revision Checklist

### Priority 1 (Must Fix):
- [ ] Issue 1: [Brief description]
- [ ] Issue 2: [Brief description]

### Priority 2 (Should Fix):
- [ ] Issue 3: [Brief description]

### Priority 3 (If Time):
- [ ] Issue 4: [Brief description]

### Explicitly Skipped:
- Issue 5: [Why dismissed]
```

## Step 7.2: Return to Phase 5 Thread or Create New Revision Thread

**Option A:** Continue in your Phase 5 writing thread (if it's not too cluttered)

**Option B:** Start fresh revision thread:

1. Open new thread    
2. Select your **Phase 5 writing model**    
3. Name thread: "[Project] - Phase 7: Revisions"    

## Step 7.3: Address Issues One at a Time

For each issue on your fix list, use this iterative approach:

```

I received adversarial review feedback on my report. I need to address the following issue:

**Issue:** [Describe the problem from Phase 6 critique]

**Current section:** 
[Paste the relevant section(s) of your report that need revision]

**Required fix:**
[What the critique suggested]

**Additional context from my research:**
[Paste relevant findings from Phase 2-4 if needed to support the revision]

Task: Revise this section to address the issue while maintaining the overall argument and voice.

Requirements:
- Keep existing structure unless restructuring is necessary
- Maintain citation style and numbering
- Don't change unrelated content
- If adding caveats/limitations, integrate them naturally (not as tacked-on disclaimers)
```

**Why one at a time:** Trying to fix 5 issues simultaneously leads to incoherent output. Fix, verify, move to next.

## Step 7.4: Review Each Revision

After each section revision:

1. **Does it actually fix the issue?**    
    - Re-read the Phase 6 critique        
    - Does the revision address the core problem?        
2. **Does it maintain report quality?**    
    - Voice still consistent?        
    - Citations still proper?        
    - Doesn't introduce new problems?        
3. **Is the fix proportional?**    
    - Don't add 3 paragraphs for a minor issue        
    - Don't add one sentence for a critical issue        

**If revision needs refinement:**

```
This revision addresses [X] but creates a new issue: [Y]

Revise again to fix both the original issue and this new concern.
```

## Step 7.5: Update Master Document

As you approve each revision:

1. **Replace the old section** in your Master Document with revised version    
2. **Check the box** on your revision checklist    
3. **Note what was changed** (optional but helpful):    

```
## Revision Log

- Section "Key Findings - Margins": Downgraded confidence language, added analyst bias caveat
- Section "Risk Analysis": Added 2 paragraphs on vertical integration threat
- Section "China Market": Expanded from 1 paragraph to 3, addressed export controls
```

**Why track changes:** If you need to explain your revisions later, or if someone asks "why didn't you include X," you can show your reasoning process.

## Step 7.6: Final Coherence Check

After addressing all priority issues, read the **entire report** start to finish:

**Check for:**

- **Flow:** Do sections connect logically?    
- **Consistency:** Is voice uniform across sections?    
- **Redundancy:** Did adding content create repetition?    
- **Executive summary accuracy:** Does it still reflect the revised report?    

**If executive summary needs updating:**

```
I've made the following substantive revisions to my report:
[List major changes]

Current executive summary:
[Paste executive summary]

Does this executive summary still accurately reflect the revised report? If not, provide an updated version.
```

## Step 7.7: Final Export and Formatting

Your report is complete. Now format it for your intended use:

**For sharing/presentation:**

- Export as PDF (cleanest, preserves formatting)    
- Or Google Docs/Word if collaboration is needed    
- Or markdown if your audience prefers (technical teams, GitHub, etc.)    

**Check final document:**

- All citations have working links (if digital) or full references (if print)    
- Formatting is consistent (headers, bullets, spacing)    
- No placeholder text remains ([INSERT], [TK], etc.)    
- Page numbers or section numbers if needed    
- Date of report completion    

**Archive your working materials:**

- Save your Master Document with all phases    
- Save URLs of all AI threads you used    
- Keep source PDFs or archives if critical    
- Store in organized folder: "[Project Name] - [Date]"    

**Why archive:** You might need to update this research in 6 months, or someone might question a source. Having your working materials lets you trace back to original context.

## Decision Point: Ready to Ship?

🟢 **Report is complete if:**

- All "Critical" and "Important" issues addressed    
- Report reads coherently start to finish    
- Citations are complete and accurate    
- Executive summary matches final content    
- You can defend every claim with confidence levels appropriate to evidence    
- You're prepared to answer questions about methodology and limitations    

🟡 **One more pass needed if:**

- Revisions created inconsistencies    
- Executive summary is outdated    
- You're not confident explaining your conclusions    

🔴 **Something is wrong if:**

- You can't address critical issues without new research (go back to Phase 2/4)    
- Report still doesn't answer your research objective (major problem)    
- You're uncomfortable putting your name on it (trust your instincts)    

## Real Example

**Issue from Phase 6:** "Report states HBM margins will remain 2-3x DRAM through 2027 as high confidence, but only 3 sell-side sources, no company guidance beyond 2026."

**Original text:**

> "HBM margins are expected to remain 2-3x higher than legacy DRAM through 2027 [Sources 4, 7, 11], providing sustained profitability advantages for leading producers."

**Revised text:**

> "HBM margins are currently 2-3x higher than legacy DRAM as of Q4 2025 [Sources 4, 7, 11]. However, forward margin projections carry significant uncertainty. Available estimates suggest margins could remain elevated through 2027 [Sources 4, 7], though these projections come exclusively from sell-side analysts and lack company guidance beyond 2026. Increasing competition from Samsung and Micron may compress margins faster than current estimates suggest, particularly if HBM supply begins to exceed demand growth."

**What changed:**

- Shifted high-confidence claim to current state (verifiable)    
- Downgraded forward-looking statement to "estimates suggest"    
- Added caveat about source limitations    
- Acknowledged compression risk    
- Maintains the finding but with appropriate confidence level    

## Common Mistakes

**Mistake 1: Completely rewriting sections**

- Unless structure is fundamentally broken, revise surgically    
- Changing everything risks introducing new errors and inconsistency    

**Mistake 2: Tacking on disclaimers**

- ❌ "The above analysis is correct. However, there are limitations..."    
- ✅ Integrate caveats naturally into the argument    

**Mistake 3: Fixing everything simultaneously**

- Trying to address 8 issues in one prompt    
- Results in incoherent output    
- Fix one, verify, move to next    

**Mistake 4: Not re-reading after revisions**

- Revisions might fix Issue A but create Issue B    
- Always verify the fix didn't break something else    

**Mistake 5: Ignoring all minor issues**

- Some "minor" issues are quick fixes that improve readability    
- If something takes 2 minutes, just fix it    

**Mistake 6: Over-hedging everything**

- Adding "potentially," "possibly," "arguably" to every sentence    
- Makes you sound uncertain even on strong evidence    
- Match confidence language to evidence quality, don't default to hedging    

**Mistake 7: Not updating executive summary**

- You revised the body but executive summary still reflects old version    
- Readers notice this immediately and lose confidence    

**Mistake 8: Forgetting to archive**

- 3 months later you need to update the analysis    
- You have no idea what threads, sources, or reasoning you used    
- Starting from scratch wastes time    

---

**Phase 7 Complete.** Your research is finalized, defensible, and ready to share.

---
# What You've Accomplished

You've completed a comprehensive research workflow that:

✅ **Decomposed** a complex question into answerable components  
✅ **Gathered** 30-50 authoritative sources efficiently  
✅ **Analyzed** contradictions and assessed evidence quality  
✅ **Verified** claims and identified gaps  
✅ **Synthesized** findings into coherent narrative  
✅ **Stress-tested** through adversarial review  
✅ **Polished** based on critical feedback

**This is professional-grade research.** You've implemented RLM principles manually - decomposition, parallel processing, verification, synthesis - with human judgment at every decision point.

The first time through takes 2-4 hours. With practice, you'll move through Phases 2-5 much faster. The methodology becomes second nature.

---
# What's Next

**For your current project:**

- Share your report with intended audience    
- Be prepared to discuss methodology and limitations    
- Update if new information emerges    

**For future research:**

- Use this same 7-phase workflow    
- Adapt the structure to your specific needs    
- Build a template in your note system for faster setup    

**To go deeper:**

- See the [RLM Research Appendix](XXXX) for technical background    
- Check the [Quick Reference Guide](XXXX) for streamlined instructions    

---
# Appendices

---
## Appendix A: RLM Research Background

This section explains the technical foundation behind the workflow. **You don't need to read this to use the guide** - it's here for those curious about the research that inspired this methodology.

## What Are Recursive Language Models?

Recursive Language Models (RLMs) are a technique developed by MIT researchers to solve the "context rot" problem in AI systems. The core insight: instead of feeding an entire long document into an AI model at once (which degrades performance), you can programmatically decompose the task, process pieces in parallel, and recursively call the model on smaller chunks.

**The key RLM components:**

1. **External context management** - The prompt/document lives outside the model's direct context window    
2. **Programmatic decomposition** - Code filters and chunks the input strategically    
3. **Recursive sub-calls** - The model calls itself on smaller pieces and combines results    
4. **Verification loops** - Outputs are validated before being used in further processing    

**Results from the research:**

- Up to 2x performance improvement on complex reasoning tasks    
- Ability to process contexts 100x beyond normal window limits    
- Better handling of contradictory information    
- Reduced "middle of document" attention problems    

## How This Guide Implements RLM Principles

This workflow is a **human-orchestrated implementation** of RLM concepts:

|RLM Component|Your Manual Implementation|
|---|---|
|**External context**|Master Document (stores everything outside AI threads)|
|**Programmatic decomposition**|Phase 1: Planning (you manually break down the question)|
|**Parallel processing**|Phase 2: Multiple search threads running simultaneously|
|**Recursive sub-calls**|Phase 3: Deep dives on complex sub-questions|
|**Verification loops**|Phase 4: Cross-verification before synthesis|
|**State management**|Structured markdown format enables consistent handoffs between phases|
|**Quality control**|Phase 6: Adversarial review catches context pollution|

**The critical difference:** True RLMs use code execution for automation. This guide uses structured prompts and human decision-making. You trade automation for control - the RLM researchers themselves noted that current models are "inefficient decision makers over their context," which is exactly where human oversight adds value.

## Why Manual Implementation Works

**Advantages over fully automated RLMs:**

- **Context control** - You decide what information moves forward (no context pollution)    
- **Dependency management** - You prevent searching for info you can't interpret yet    
- **Strategic decisions** - You choose when to deep dive vs when to accept findings    
- **Quality gates** - You verify before moving to next phase, not after everything is done    

**Trade-off:** Takes longer than automated approach, but produces higher quality for high-stakes research.

## Further Reading

If you want to understand RLMs technically:

- [Original MIT paper](https://arxiv.org/html/2512.24601v1) (Recursive Language Models)    
- [RLM implementation examples](https://alexzhang13.github.io/blog/2025/rlm/)    
- [Discussion on context engineering](https://www.reddit.com/r/ContextEngineering/)    

**Bottom line:** You don't need to understand RLMs to use this guide effectively. The workflow works because it follows principles that research has validated - decompose, process in parallel, verify, synthesize.

---
## Appendix B: Quick Reference Guide

**For experienced users who have completed the workflow once.** This is a condensed checklist version.
## Setup

-  Create Master Document with phase sections    
-  Identify AI platform and models (reasoning + retrieval + critique)    
-  Research objective clearly defined    

## Phase 1: Build Your Map (15-20 min)

-  Thread: Reasoning model    
-  Prompt: Decompose into 6-8 sub-questions with dependencies    
-  Critique and refine decomposition    
-  Document in Master Doc with checkboxes    
-  **Decision:** Sub-questions specific, answerable, dependencies clear?    

## Phase 2: Collect Evidence (30-45 min)

-  Threads: One per sub-question, retrieval model    
-  Launch 3-4 searches in parallel (respect dependencies)    
-  Prompt: Find 5-7 sources with structured output    
-  Copy results to Master Doc    
-  Optional: Rolling verification for 6+ sub-questions    
-  **Decision:** 30-50 sources total, relevant, multiple perspectives?    

## Phase 3: Deep Dive (20-30 min, selective)

-  Identify 2-3 sub-questions with contradictions/complexity    
-  Thread per deep dive: Reasoning model    
-  Prompt: Gap analysis + source quality + synthesis + search strategy    
-  Run 2-3 targeted follow-up searches if needed    
-  Document confidence levels (High/Medium/Low)    
-  **Decision:** Major contradictions explained or resolved?    

## Phase 4: Check Quality (15-20 min)

-  Thread: Reasoning model with long context    
-  Compile all findings from Phases 2-3    
-  Prompt: 7-part verification (single-source, contradictions, evidence quality, coverage, biases, gaps, completeness)    
-  Completeness rating received    
-  **Decision:** 90%+ complete? Address critical gaps or proceed?    

## Phase 5: Write Report (30-45 min)

-  Thread: Reasoning model (same as Phase 1/3)    
-  Create report structure in Master Doc    
-  Draft section-by-section (not all at once)    
-  Methodology → Findings → Analysis → Conclusions → Executive Summary (last)    
-  Match confidence language to Phase 4 assessments    
-  Citations for all factual claims    
-  **Decision:** Report complete, flows logically, properly cited?    

## Phase 6: Stress Test (15-20 min, optional but recommended)

-  Thread: DIFFERENT model than Phase 5    
-  Paste complete report    
-  Prompt: Adversarial review (logic, evidence, missing perspectives, structure, citations)    
-  Review critique, discuss disagreements    
-  Export final critique with severity ratings    
-  **Decision:** Critical issues identified? Proceed to fix or ship as-is?    

## Phase 7: Polish (15-20 min)

-  Thread: SAME model as Phase 5    
-  Prioritize fixes (Critical → Important → Minor)    
-  Address issues one at a time    
-  Update Master Doc with revisions    
-  Final coherence check    
-  Update executive summary if needed    
-  Export and archive    
-  **Decision:** Ready to ship?    

## Stop Rules

- **Phase 1:** Max 30 min planning (diminishing returns)    
- **Phase 2:** Max 20 sources per sub-question (more doesn't help)    
- **Phase 3:** Max 3 deep dives (if flagging more, Phase 1 was wrong)    
- **Phase 4:** 90% complete is good enough (don't chase 100%)    
- **Phase 6:** Address Critical + Important only (skip Minor if time-constrained)    

## Time Estimates

- **First time:** 2-4 hours total    
- **Experienced:** 60-90 minutes for full workflow    
- **Quick version** (Phases 1-2-4-5 only): 45-60 minutes    

---

## Appendix C: Common Adaptations

The 7-phase workflow is flexible. Here's how to adapt it for different use cases:

## For Academic Research

**Modifications:**

- **Phase 1:** Add "Literature review gaps" as explicit sub-question    
- **Phase 2:** Prioritize peer-reviewed sources, use Google Scholar    
- **Phase 4:** Add methodology critique (is approach rigorous?)    
- **Phase 5:** Structure as Introduction/Literature Review/Methodology/Findings/Discussion/Conclusion    
- **Phase 6:** Focus adversarial review on methodological validity    
## For Investment Analysis

**Modifications:**

- **Phase 1:** Always include sub-questions on: financials, competitive position, risks, valuation    
- **Phase 2:** Prioritize primary sources (company filings, earnings calls, industry data)    
- **Phase 3:** Deep dive on competitive moats and risk factors    
- **Phase 4:** Verify all quantitative claims with multiple sources    
- **Phase 5:** Structure as Thesis/Business Overview/Financials/Competitive Analysis/Risks/Valuation/Conclusion    
- **Phase 6:** Have adversarial review focus on "what could go wrong"    

## For Product Decisions / Major Purchases

**Modifications:**

- **Phase 1:** Sub-questions around: features needed, price range, user reviews, alternatives    
- **Phase 2:** Mix professional reviews + user reviews + spec sheets    
- **Phase 3:** Deep dive on common complaints and deal-breakers    
- **Phase 4:** Focus on "what's the catch" (if reviews are all positive, find critical reviews)    
- **Phase 5:** Structure as Requirements/Options Analysis/Pros-Cons/Recommendation    
- **Phase 6:** Adversarial review asks "what am I missing? what will I regret?"    

## For Fact-Checking / Claim Verification

**Modifications:**

- **Phase 1:** Decompose claim into verifiable components    
- **Phase 2:** Search for original sources (not just reporting on the claim)    
- **Phase 3:** Deep dive required - trace claim to original source    
- **Phase 4:** Verify source credibility, check for retraction/corrections    
- **Phase 5:** Structure as Claim/Evidence For/Evidence Against/Verdict with confidence level    
- **Phase 6:** Focus on "am I being fooled by confirmation bias?"    

## For Competitive Intelligence

**Modifications:**

- **Phase 1:** Sub-questions organized by: competitor capabilities, strategy, weaknesses, threats to us    
- **Phase 2:** Use diverse sources (news, job postings, product reviews, financial filings, patents)    
- **Phase 3:** Deep dive on strategic intentions and capability gaps    
- **Phase 4:** Flag any single-source claims about competitor strategy (likely speculation)    
- **Phase 5:** Structure as Executive Summary/Competitor Profile/Strategic Assessment/Implications for Us    
- **Phase 6:** Review for: wishful thinking bias (understating competitor), paranoia (overstating threat)    
- 
## For Content Research / Article Writing

**Modifications:**

- **Phase 1:** Sub-questions become article sections/angles    
- **Phase 2:** Mix data sources, expert quotes, examples, counterarguments    
- **Phase 3:** Deep dive on any controversial/disputed claims    
- **Phase 4:** Verify quotes are accurate, data is current, perspectives are balanced    
- **Phase 5:** Draft in article structure (lede/nut graf/body/conclusion)    
- **Phase 6:** Review for: clarity, bias, unsupported claims, missing context    

## Quick Version (When Time-Constrained)

**Streamlined workflow:**

- **Phase 1:** 10 minutes - 4-5 sub-questions instead of 6-8    
- **Phase 2:** 20-30 minutes - 3-5 sources per sub-question    
- **Phase 3:** SKIP - only if absolutely necessary    
- **Phase 4:** 10 minutes - quick verification focused on single-source claims only    
- **Phase 5:** 20 minutes - shorter report, bullet-point findings acceptable    
- **Phase 6:** SKIP - use your own judgment    
- **Phase 7:** 5 minutes - light polish only    

**Trade-off:** Good enough for exploratory research, but not defensible for high-stakes decisions

---

## Appendix D: Platform-Specific Tips

## Using Perplexity Pro

**Advantages:**

- Built-in web search with citations    
- Access to multiple models (Claude, Gemini, GPT)    
- Thread organization

**Best practices:**

- Phase 1: Claude Sonnet 4.5 Thinking    
- Phase 2: Gemini Pro (fastest for searches)    
- Phase 3: Claude Sonnet 4.5 Thinking    
- Phase 4: Claude Sonnet 4.5    
- Phase 5: Claude Sonnet 4.5 Thinking    
- Phase 6: Switch to GPT-4o or o3    
- Phase 7: Return to Claude Sonnet 4.5    

**Limitations:**

- Rate limits on some models (check current limits)    
- Cannot process uploaded documents natively (paste text instead)    

## Using ChatGPT Plus / o1

**Advantages:**

- o1/o3 excellent for reasoning tasks    
- Canvas mode useful for iterative writing    
- Can upload documents    

**Best practices:**

- Enable web browsing for Phase 2 searches    
- Use o1 for Phases 1, 3, 4, 6    
- Use GPT-4o for Phase 2 (faster, cheaper)    
- Canvas mode helpful for Phase 5/7 revisions    

**Limitations:**

- o1 slower than other models (budget more time)    
- Web browsing sometimes inconsistent    

## Using Claude (Anthropic)

**Advantages:**

- Projects feature for persistent context    
- Artifacts for document drafting    
- 200K context window

**Best practices:**

- Create Project with your research objective as context    
- Use Sonnet 4.5 Thinking for all phases    
- Enable web search via Claude.ai or API    
- Artifacts mode for Phase 5 writing    

**Limitations:**

- Single model (can't switch for Phase 6 without leaving platform)    
- Web search via API is expensive (~$10/1000 searches)    

## Using API Access (Multi-Platform)

**Advantages:**

- Full control over parameters    
- Can script repetitive parts    
- Mix and match models freely    

**Best practices:**

- Use Claude API + Perplexity API for search
- Or build RAG system for document-based research    
- Track costs per phase to optimize    

**Limitations:**

- Requires technical setup    
- Costs less predictable    
- No UI unless you build one    

## Using Manual Search + Free Models

**Advantages:**

- No subscription cost    
- Works with any free AI (Claude Sonnet via Claude.ai, ChatGPT free tier)    

**Best practices:**

- Google/Bing searches yourself in Phase 2    
- Copy relevant excerpts into AI for synthesis    
- Use free tier Claude or ChatGPT for analysis phases    

**Limitations:**

- Much slower (no parallelization in Phase 2)    
- Rate limits may interrupt workflow    
- Manual citation management    

---

## Appendix E: Troubleshooting Common Issues

## "My Phase 1 decomposition feels wrong"

**Symptoms:** Can't find sources, questions overlap, dependencies circular

**Fix:**

- Your research objective might be too vague - make it more specific    
- Or too narrow - broaden scope    
- Run the critique prompt again with specific issues highlighted    
- If still stuck: Start with 3 sub-questions instead of 6-8, complete workflow, then expand    

## "Phase 2 searches aren't finding good sources"

**Symptoms:** All "low relevance," sources off-topic, can't find 5-7 per question

**Fix:**

- Sub-questions might be poorly phrased for search - rewrite with searchable keywords    
- Try different search terms (check Phase 1 "Source types" recommendations)    
- Timeframe might be wrong ("2026 HBM demand" vs "HBM demand projections")    
- Topic might not have public sources - pivot to adjacent answerable questions    

## "Everything needs a deep dive"

**Symptoms:** Flagging 6+ out of 8 sub-questions for Phase 3

**Fix:**

- Your Phase 1 questions were too ambitious (answering each requires a research project)    
- Or Phase 2 searches weren't focused enough (need more specific searches, not deep dives)    
- Or you're being perfectionist (contradictions don't always need resolving)    
- **Action:** Pick 2-3 most critical, deep dive those only, accept "good enough" on others    

## "Phase 4 completeness rating is 60%"

**Symptoms:** Major gaps, many single-source claims, contradictions unresolved

**Fix:**

- Don't panic - this is why Phase 4 exists    
- Review "Critical gaps" list - are they actually researchable?    
- If yes: Run 3-5 targeted searches and re-verify    
- If no: Revise research objective to match what's answerable    
- Or acknowledge limitations and proceed with caveats    

## "Phase 5 report feels like a list of sources"

**Symptoms:** No analysis, just "Source X says... Source Y says..."

**Fix:**

- You're summarizing, not synthesizing    
- Ask model to explain _patterns_ across sources, not just list findings    
- Use Phase 4 confidence assessments to make claims ("Evidence strongly suggests..." vs "Sources list...")    
- Add transitional analysis between findings    

## "Phase 6 critique says everything is wrong"

**Symptoms:** 10+ critical issues, feels overwhelming

**Fix:**

- Critique model might be overly aggressive - discuss specific issues    
- Or your Phase 4-5 genuinely had problems - don't shoot the messenger    
- Separate real issues from model misunderstanding your methodology    
- Focus on top 3 critical issues first, reassess after fixing those    

## "I'm spending 6+ hours on this"

**Symptoms:** Stuck in analysis paralysis, infinite research loops

**Fix:**

- Set hard time caps per phase (use timer)    
- Apply stop rules: 90% complete is good enough    
- Remember: This is your first time, it gets faster    
- Or: Switch to Quick Version workflow for this project    
- Ask: "What decision am I trying to make?" - stay focused on that    

## "Models keep giving inconsistent outputs"

**Symptoms:** Same prompt, very different results each time

**Fix:**

- Your prompts might be too vague - add more structure/constraints    
- Or model temperature too high - check settings    
- Copy-paste exact templates from guide until you understand pattern    
- Use examples in prompts ("Like this: [example], not like this: [bad example]")    

---

## Appendix F: Further Resources

## Original Perplexity-Specific Guide

[Complete Manual Deep Research Guide for Perplexity Pro](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Complete%20Manual%20Deep%20Research%20Guide%20for%20Perplexity%20Pro.md)

## Community & Feedback

- GitHub: [Repository for guide updates and community contributions](https://github.com/VeritasPlaybook/playbook/tree/main)

## Tools Mentioned

- **Perplexity Pro:** [https://perplexity.ai](https://perplexity.ai/)    
- **Claude (Anthropic):** [https://claude.ai](https://claude.ai/)    
- **ChatGPT:** [https://chat.openai.com](https://chat.openai.com/)    
- **Notion:** [https://notion.so](https://notion.so/) (Master Document management)    
- **Obsidian:** [https://obsidian.md](https://obsidian.md/) (Markdown notes)    

## Updates & Changelog

This guide will be updated as:

- New AI models emerge with better capabilities    
- Community discovers improvements    
- Platform features change    

Check back periodically or star the repository for updates.

---
## Final Notes

**You've reached the end of the guide.** Everything beyond this point was explained in the 7 phases and appendices.

**Key takeaways:**

1. **Decomposition is everything** - Phase 1 planning determines success    
2. **Parallelize where possible** - Don't research sequentially when you can work in parallel    
3. **Verify before writing** - Phase 4 quality check saves you from embarrassing errors    
4. **Adversarial review is optional but transformative** - Phase 6 separates good from great    
5. **Match confidence to evidence** - Don't overstate weak claims    

**This workflow is RLM-inspired, not RLM-implemented.** You're using structured prompts and human oversight to achieve what automated RLMs do programmatically. The advantage: you control every decision point. The trade-off: takes longer than automation.

**The first time is the hardest.** You're learning the system. By the third research project, you'll move through phases much faster.

**Adapt freely.** This isn't a rigid formula. Use what works, skip what doesn't, modify for your context.

**Share your experience.** If this guide helped you, consider sharing your results or improvements with the community.

---

**Good luck with your research.**

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