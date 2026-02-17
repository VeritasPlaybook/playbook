>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

For Table of Contents, click **Outline** button on the right ----------------------------------------------------------------------------------------------^

---
# What This Is

**The problem:** You ask AI a vague question. It makes assumptions about what you want. You get an answer that's 70% right but misses the key details you actually needed. You try again with more context. It's better, but you've wasted 3-4 turns and you're still not sure the AI fully understands. This happens constantly to me; whether its research projects, writing tasks, strategic planning, data analysis. The AI *can* deliver exactly what you need, but only if it has the right context. In fact, when using AI, you can argue, context is everything. And the more context you give, the better the answer you get. Unfortunately, most people don't provide it because typing detailed explanations is exhausting.

**The solution:** A single reusable prompt pattern that forces AI to ask you smart, structured clarifying questions before doing any work, and makes answering those questions ridiculously easy. Instead of writing paragraphs of context, you pick from multiple-choice options and copy-paste your selections. The AI gets 10x better context in 1/5th the time.

**The result:** Fewer terrible first drafts. Less back-and-forth. More accurate outputs that actually match what you need. And because you embed this as a custom instruction (system prompt), it works automatically across all your tasks without remembering to trigger it each time.

This isn't a hack or a workaround. It's grounded in research on how large language models actually learn from context, and why the default behavior (guessing instead of asking) produces mediocre results.

## What Makes This Pattern Different
What makes this pattern unique is something I developed through trial and error, combined with insights from reading AI research papers on in-context learning and clarification frameworks. The key innovation: **asking numbered questions with clear multiple-choice options (Q1: A, B, C, etc.)**.

Most people just tell the AI "ask me clarifying questions" and get back free-form questions that still require you to write paragraphs. I took it further: force the AI to structure every question with specific options you can choose from. This transforms clarification from "writing more context" into "selecting from a menu."

Then I added the second layer: **the copy-paste answer template**. Early on, I was manually typing "Q1: A, Q2: B, Q3: C..." every time. That got old fast. So I trained the AI to always provide a prefilled template at the end of its questions. Now I just copy it, scroll through, and change the letters. This saves me from retyping Q1:, Q2:, Q3: over and over. When you do this dozens of times a day, those seconds add up—and more importantly, the friction disappears.

**Disclaimer:** I haven't seen this exact pattern documented anywhere else, but if there are earlier examples of this method, let me know and I'll revise my claim. Until then, I'm sharing what's worked for me for years.

---

**What's in this guide:**
- How this pattern works (the 4-step flow)
- Why it works (research-backed explanations)
- Three prompt versions you can use (minimal, detailed, customizable)
- How to embed into major AI platforms (Perplexity, ChatGPT, Claude)
- Detailed examples across different use cases
- Common mistakes and how to avoid them

---
# Quick Start

**Want to try this right now? Here's the fastest path:**

## Copy This Into Your AI's Custom Instructions

```
Whenever I say something like "Ask me questions for clarity and to get as much context," 
assume I want you to fully understand the situation before doing any main task.

Always respond by:
1) Asking me numbered questions (Q1, Q2, Q3, etc.), where each question includes 
   clear multiple-choice options (e.g., Q1: A, B, C; Q2: A, B, C, D).
2) Providing, at the end of your message, a ready-to-use answer template in this format 
   so I can copy and paste it back quickly:

Q1: [A/B/C/etc]
Q2: [A/B/C/etc]
Q3: [A/B/C/etc]

3) After I provide my answers, ask: "Do you have any more questions I should answer 
   before I proceed?" and repeat this pattern if I say yes.

Use this pattern any time I ask you to "ask me questions for clarity" or use similar 
wording, before you start solving the main task.
```

## Test It

1. Open your AI (Perplexity, ChatGPT, Claude)
2. First, pick a topic you want to research and ask it to write a report. Try something like "AI's impact on healthcare" or "semiconductor industry competitive dynamics" or any topic that interests you.
3. At the end of your prompt, add: **"Ask me questions for clarity and to get as much context."**
4. You should get 5-10 multiple-choice questions + a copy-paste answer sheet
5. Fill in your answers, paste back, and watch the AI deliver exactly what you need

If it works, you're done. If you want to understand *why* this is so effective and see advanced examples, keep reading.

---
# How It Works (General Flow)

This pattern has 4 steps that repeat until the AI has enough context.

**When to use this pattern:** Before starting any complex task, especially when you're about to give the AI detailed instructions, large amounts of information, or specific requirements, trigger the pattern by saying: **"Ask me questions for clarity and to get as much context"** at the end of your prompt.

## Step 1: You Trigger the Pattern
- You say: **"Ask me questions for clarity and to get as much context"** (or similar phrasing)
- Works for any task: research, writing, planning, analysis, personal decisions
- You can also bake this into a project description or task brief
- Add it at the end of your main prompt to signal the AI should clarify before proceeding

## Step 2: AI Generates Structured Questions
- The AI produces numbered questions (Q1, Q2, Q3...)
- Each question has 3-6 multiple-choice options that cover the most common scenarios
- Questions are strategically chosen to disambiguate the task and gather critical context
- Example for "Write a PRD":
  - Q1: Audience? A) Internal engineering team, B) Executive stakeholders, C) External partners, D) Mixed audience
  - Q2: Feature complexity? A) Simple UI change, B) New workflow, C) Backend integration, D) Full platform addition
  - Q3: Depth needed? A) 1-page overview, B) 3-5 pages with specs, C) 10+ pages comprehensive

## Step 3: AI Provides Copy-Paste Answer Sheet
- At the end of the questions, the AI gives you a prefilled template:
```
Q1: 
Q2: 
Q3: 
Q4: 
Q5: 
```
- You just fill in the letters (Q1: A, Q2: C, Q3: B...) and paste back
- Takes 30-60 seconds instead of writing 3-4 paragraphs


> **💡 Pro Tip: You're Never Bound by the Choices**
> 
> If none of the multiple-choice options fit what you need, just say so. You can always respond with: "None of those—what I actually want is [explain in your own words]." The AI will adjust and continue the clarification process. The multiple-choice format is there to make things _easier_, not to limit you.

## Step 4: Iteration Check
- After you provide answers, AI asks: **"Do you have any more questions I should answer before I proceed?"**
- If yes: AI asks follow-up questions based on your initial answers (refining context)
- If no: AI proceeds with the main task using all gathered context as hard constraints
- **This iteration step is critical** because it's why this pattern avoids the "AI makes wrong early assumptions" problem

**Key insight:** The AI doesn't start working on your task until it has sufficient context. This prevents wasted effort on wrong directions and dramatically improves first-draft quality.

---
# Three Prompt Versions: Choose What Fits Your Workflow

## Version 1: Minimal (Fastest Setup)

Use this if you want bare-bones functionality:

```
Whenever I say "Ask me questions for clarity," respond with numbered questions that have 
multiple-choice options (Q1: A, B, C, etc.), then provide a copy-paste answer sheet at 
the end. After I answer, ask if I have more questions before proceeding.
```

**Pros:** Short, easy to understand, covers core functionality  
**Cons:** Less explicit about format, might not always generate answer sheet  

---
## Version 2: Detailed (Recommended for Most Users)

This is the version from Quick Start (comprehensive and reliable):

```
Whenever I say something like "Ask me questions for clarity and to get as much context," 
assume I want you to fully understand the situation before doing any main task.

Always respond by:
1) Asking me numbered questions (Q1, Q2, Q3, etc.), where each question includes 
   clear multiple-choice options (e.g., Q1: A, B, C; Q2: A, B, C, D).
2) Providing, at the end of your message, a ready-to-use answer template in this format 
   so I can copy and paste it back quickly:

Q1: [A/B/C/etc]
Q2: [A/B/C/etc]
Q3: [A/B/C/etc]

3) After I provide my answers, ask: "Do you have any more questions I should answer 
   before I proceed?" and repeat this pattern if I say yes.

Use this pattern any time I ask you to "ask me questions for clarity" or use similar 
wording, before you start solving the main task.
```

**Pros:** Explicit format requirements, includes iteration check, reliable output  
**Cons:** Longer to paste, slightly more verbose  

---
## Version 3: Customizable (For Power Users)

Use this structure and add your domain-specific requirements:

```
Whenever I say "Ask me questions for clarity," assume I want you to fully understand the 
situation before doing any main task.

Always respond by:
1) Asking numbered questions (Q1, Q2, Q3, etc.) with clear multiple-choice options
2) Providing a copy-paste answer template at the end
3) After I answer, asking: "Do you have any more questions?" and iterating if needed

[CUSTOM ADDITIONS - Add your specific requirements here:]
• For writing tasks: Always ask about audience, purpose, length, and tone
• For research tasks: Always ask about depth needed, time horizon, and key stakeholders
• For data analysis: Always ask about business context, target audience for findings, 
  and what decisions this analysis will inform
• [Add your own patterns based on your most common tasks]

Use this pattern before starting any main task when I say "Ask me questions for clarity" 
or similar phrasing.
```

**Pros:** Tailored to your exact workflow, bakes in your most common needs  
**Cons:** Requires upfront thinking about your patterns, needs periodic updates  

---
# How to Embed Into Custom Instructions (Perplexity, ChatGPT, Claude)

## Perplexity AI

**Where to add it:**
1. Click your profile icon (top right)
2. Select "Settings"
3. Scroll to "Custom Instructions" or "AI Behavior"
4. Paste your chosen prompt version (see options above)

**Sanity check:**
- Open new thread
- Say: "Ask me questions for clarity. I need to research X."
- Should get numbered questions with options + answer sheet

---
## ChatGPT (OpenAI)

**Where to add it:**
1. Click your profile icon (bottom left)
2. Select "Customize ChatGPT" or "Settings"
3. Look for "Custom Instructions" section
4. Paste in the "How would you like ChatGPT to respond?" field

**Sanity check:**
- Start new chat
- Say: "Ask me questions for clarity. I need to write a PRD."
- Should get structured Q&A format

**Note:** Custom instructions persist across all chats. You don't need to retrigger each time; just say your trigger phrase and it activates.

---
## Claude (Anthropic)

**Where to add it:**
1. Go to Settings (gear icon)
2. Select "Custom Instructions" or "Projects" (if using Claude Projects)
3. If using Projects: Add to project instructions
4. If using regular Claude: May not support custom instructions yet (check current features)

**Alternative for Claude:** If no custom instructions available, save the prompt pattern in a note and paste it at the start of important conversations.

---
# How to Customize: Decision Framework

After using the base pattern 5-10 times, ask yourself:

- **Do I always clarify the same things?** (e.g., audience, deadline, depth) → Add to custom instruction
- **Are there domain-specific dimensions that always matter?** (e.g., for finance work: risk tolerance, time horizon) → Add to custom instruction
- **Do I use this pattern for only 2-3 task types?** (e.g., only research and writing) → Customize questions for those types
- **Do I need output in specific formats?** (e.g., always markdown, always with citations) → Add format requirements

**Example customization for Product Managers:**

```
[After base prompt]

For product-related tasks (PRDs, roadmaps, specs), always ask:
• Audience mix (eng, exec, product, external)
• Stage of product (idea, spec, built)
• Timeline pressure
• Success metrics
• Resource constraints
```

---
# Why It Works

This isn't just a clever trick. It's grounded in how large language models actually process information and why they fail when context is missing.

### 1. In-Context Learning as Bayesian Inference
LLMs perform implicit Bayesian inference when they receive context. Think of it like this: every piece of information you provide narrows down the model's "probability distribution" over what you actually want. With vague input, the model has to guess among thousands of valid interpretations. With structured context, it converges on the right one.

Research shows that more relevant context = tighter posterior = better predictions. This is mathematically provable, not just anecdotal.

### 2. Clarification Dramatically Improves Accuracy
Studies on frameworks like CLAM (Clarify-if-Ambiguous) found that simply asking one clarifying question before answering boosted accuracy by ~20 percentage points on ambiguous questions. The problem? LLMs rarely ask for clarification by default; they just guess and often guess wrong.

This pattern forces the clarification behavior that produces better outputs but doesn't happen naturally.

### 3. Multi-Turn Conversation Failures
Research on multi-turn AI conversations found a 39% average performance drop compared to single-turn interactions. Why? Because LLMs make assumptions in early turns and don't recover when those assumptions are wrong; they "get lost and don't recover."

**But:** Structured clarification *before* the AI starts working prevents this failure mode entirely. The AI isn't making assumptions; it's asking, you're telling it explicitly, and then it proceeds with confidence.

### 4. Cognitive Load Reduction for Users
Multiple-choice questions + copy-paste templates dramatically reduce the cognitive load on you. Instead of generating context from scratch (high cognitive load), you're recognizing and selecting from options (low cognitive load). This makes it easy to provide rich, detailed context without exhaustion.

Research on human-computer interaction shows that structured input formats improve task completion rates and reduce abandonment; people actually *do* provide the context when it's this easy.

### 5. System Prompts Generalize Across Tasks
Studies on system prompt optimization found that a single well-designed system prompt performs on par with task-specific prompts across 47 different types of tasks. By embedding this pattern as a custom instruction, you get consistent, high-quality clarification across research, writing, planning, analysis (everything).

### Why Iteration After Initial Answers Is Critical
This is the secret sauce. After you answer the first round of questions, the AI asks: **"Do you have any more questions I should answer before I proceed?"**

Why this matters:
- **Prevents wrong turns:** If the AI misunderstood something in your initial answers, you catch it *now* instead of after it's written 1,000 words in the wrong direction
- **Progressive refinement:** Your first answers often reveal new dimensions the AI should ask about (e.g., "Oh, you're writing for executives; should I include technical appendices?")
- **Confidence building:** Knowing you can iterate creates psychological safety to give quick first answers, then refine

The research is clear: LLMs that take a wrong turn early don't recover. Iteration prevents the wrong turn entirely.

---
# Detailed Examples: How to Use This Pattern

### Example 1: Deep Research Projects

#### Before (One-Shot, No Context)
**You:** "Research SK Hynix's competitive position in the HBM market."

**AI:** *Generates 800 words of generic background about HBM technology, SK Hynix's history, and current market share. Misses your actual question about defensibility. No discussion of competitive threats or barriers to entry. You spend 15 minutes reading something that doesn't help.*

#### After (Structured Clarification)
**You:** "Ask me questions for clarity. I need to research SK Hynix's competitive position in the HBM market."

**AI:**
```
I'll ask you clarifying questions to understand exactly what you need.

Q1: What's the primary purpose of this research?
A) Investment decision (buy/sell/hold)
B) Competitive intelligence for a company entering the market
C) Academic analysis
D) General industry understanding

Q2: What's your current knowledge level of the HBM market?
A) Expert (I understand technical specs, supply chains, customers)
B) Intermediate (I know basics but need depth)
C) Beginner (need foundational context first)

Q3: What time horizon matters most?
A) Current snapshot (2026 only)
B) 1-2 year outlook
C) 3-5 year strategic view
D) Long-term (5-10 years)

Q4: Which aspects are most critical? (Choose 2-3)
A) Technology barriers / moats
B) Customer concentration risks
C) Manufacturing capacity and capital requirements
D) Competitive dynamics (Samsung, Micron, etc.)
E) Margin structure and profitability
F) Supply chain dependencies

Q5: What depth do you need?
A) Executive summary (2-3 pages)
B) Moderate depth (5-8 pages with data)
C) Comprehensive deep dive (15+ pages, all angles)

Q6: Do you have access to paid research sources, or should I focus on public info?
A) Public only (news, company filings, free reports)
B) I have access to paid sources (industry reports, financial databases)

---

**Copy-paste answer sheet:**

Q1: 
Q2: 
Q3: 
Q4: 
Q5: 
Q6: 
```

**You:** (30 seconds later)
```
Q1: A
Q2: B
Q3: C
Q4: A, B, D
Q5: C
Q6: A
```

**AI:** "Got it. Do you have any more questions I should answer before I proceed?"

**You:** "No, go ahead."

**AI:** *Now generates a comprehensive research plan focused specifically on:*
- *Technology moats and defensibility (your Q4:A)*
- *Customer concentration risks, especially NVIDIA dependency (your Q4:B)*
- *Competitive dynamics with Samsung and Micron (your Q4:D)*
- *Written for someone who understands basics but needs depth (your Q2:B)*
- *3-5 year strategic view (your Q3:C)*
- *Investment decision framework (your Q1:A)*
- *Comprehensive 15+ page depth (your Q5:C)*
- *Uses only public sources (your Q6:A)*

**Outcome:** The AI delivers exactly what you need on the first try. No wasted reading. No second attempt needed.

---
## Example 2: Writing (PRDs, Articles, LinkedIn Posts)

#### Before (One-Shot, No Context)
**You:** "Write a PRD for a fraud detection feature using machine learning."

**AI:** *Generates a generic 2-page PRD with standard sections. Uses jargon inconsistently. Includes technical ML details that your stakeholders won't understand. Misses the actual business context (regulatory compliance driver, customer complaints about false positives, tight Q2 deadline).*

#### After (Structured Clarification)
**You:** "Ask me questions for clarity. I need to write a PRD for a fraud detection feature."

**AI:**
```
I'll ask questions to understand what you need.

Q1: Who's the primary audience for this PRD?
A) Engineering team (technical specs, implementation details)
B) Executive stakeholders (business case, ROI, strategic fit)
C) Product team (user flows, requirements, success metrics)
D) Mixed audience (need to serve multiple groups)

Q2: What stage is this feature in?
A) Idea/exploration (defining the problem)
B) Approved, needs detailed spec for build
C) In progress, need to document decisions
D) Built, need post-launch documentation

Q3: How much technical depth?
A) High (ML model details, data pipelines, architecture)
B) Medium (what it does, how users experience it, key tech constraints)
C) Low (business value, user flows, no technical internals)

Q4: What's driving this feature? (Choose 1-2 most important)
A) Customer complaints / feedback
B) Regulatory compliance requirement
C) Competitive pressure
D) Revenue opportunity
E) Cost reduction / efficiency
F) Strategic initiative

Q5: Length and format preference?
A) 1-2 pages (brief overview)
B) 3-5 pages (standard PRD)
C) 8-12 pages (comprehensive with appendices)
D) Flexible, tell me what sections matter most

Q6: Deadline pressure?
A) Need this today/tomorrow (time-crunched)
B) Have 1-2 weeks (normal pace)
C) No rush, quality over speed

---

**Copy-paste answer sheet:**

Q1: 
Q2: 
Q3: 
Q4: 
Q5: 
Q6: 
```

**You:**
```
Q1: D
Q2: B
Q3: B
Q4: B, A
Q5: C
Q6: A
```

**AI:** "Got it. Do you have any more questions I should answer before I proceed?"

**You:** "Yes; how should I structure this for the mixed audience?"

**AI:**
```
Good question! A few more clarifications:

Q7: For your mixed audience, should I:
A) Write one unified document with sections clearly labeled by audience
B) Create a main PRD + separate technical appendix
C) Write layered (exec summary → product details → tech appendix)

Q8: For the regulatory compliance driver (Q4:B), do you need:
A) Just mention it as context
B) Detailed section on compliance requirements and how feature addresses them
C) Full regulatory mapping in an appendix

---

Q7: 
Q8: 
```

**You:**
```
Q7: C
Q8: B
```

**AI:** "Any more questions I should answer?"

**You:** "No, go ahead."

**AI:** *Now writes:*
- *Executive summary (2 paragraphs) for stakeholders*
- *Main PRD body in medium-technical language accessible to product + engineering*
- *Technical appendix with ML model details for engineering*
- *Detailed compliance section explaining regulatory requirements*
- *Comprehensive 8-12 pages with proper structure*
- *Optimized for quick turnaround (your Q6:A deadline pressure)*

**Outcome:** First draft is 85-90% final. You edit for specifics, not structure. Saves 2-3 revision cycles.

---
## Example 3: Strategic Planning (Roadmaps, OKRs, Decision Frameworks)

#### Before/After Comparison

| Without Clarification | With Clarification |
|---------------------|-------------------|
| **You:** "Help me plan Q2 OKRs for my product team." | **You:** "Ask me questions for clarity. I need to plan Q2 OKRs for my product team." |
| **AI:** *Generates generic OKR template with example objectives like "Improve user engagement" and "Ship new features." Completely abstract. Doesn't account for your actual constraints (3-person team, legacy tech debt, customer churn issues).* | **AI:** *Asks 8 questions about: team size, current priorities, biggest challenges, executive expectations, resource constraints, success metrics, how OKRs will be used (planning vs performance review).* |
| **You:** Spend 20 minutes explaining what's wrong, trying again. | **You:** 60 seconds filling out answer sheet. |
| **Result:** After 3-4 attempts, you have something usable but it feels like pulling teeth. | **Result:** First draft includes: specific OKRs tied to your customer churn issue, realistic Key Results for a 3-person team, notes on how to present to executives, trade-offs between new features and tech debt. You refine 10% and you're done. |

### Step-by-Step Walkthrough for Strategic Planning

**You:** "Ask me questions for clarity. I need to build a 12-month product roadmap."

**AI:** *(Generates 8-10 questions about strategy, team, constraints, stakeholders, prioritization framework)*

**You:** *(Fills in answer sheet in 60-90 seconds)*

**AI:** "Do you have any more questions I should answer?"

**You:** "Yes; I mentioned we're resource-constrained (Q5:A). What if I tell you our exact team composition?"

**AI:** 
```
Great, that will help me be more realistic about what you can deliver.

Q11: Team composition?
A) 2-3 engineers, 1 PM (you)
B) 5-8 engineers, 1-2 PMs
C) 10+ engineers, 3+ PMs, dedicated design/data
D) Pre-product-market fit founding team (everyone wears multiple hats)

Q12: Engineering seniority mix?
A) Mostly senior (can work autonomously, fast)
B) Mixed (need some oversight, moderate pace)
C) Mostly junior (need significant oversight, slower)

---

Q11: 
Q12: 
```

**You:**
```
Q11: A
Q12: B
```

**AI:** "Any more questions?"

**You:** "No, go ahead."

**AI:** *Generates roadmap that:*
- *Accounts for 2-3 engineer capacity*
- *Includes realistic timelines for mixed-seniority team*
- *Prioritizes ruthlessly (no "nice-to-haves" that won't ship)*
- *Builds in buffer time for unexpected issues*
- *Matches your strategic goals from initial answers*

**Outcome:** Roadmap you can actually commit to. Not aspirational fantasy.

---
## Example 4: Data Analysis

#### Before (One-Shot, No Context)
**You:** "Analyze this dataset and tell me what's interesting." *(Attaches CSV)*

**AI:** *Runs basic summary stats. Generates 3-4 generic visualizations. Finds a correlation that's obvious and meaningless. No actionable insights.*

### After (Structured Clarification)
**You:** "Ask me questions for clarity. I need you to analyze this dataset." *(Attaches CSV)*

**AI:**
```
I'll ask questions to guide the analysis effectively.

Q1: What's the business context for this dataset?
A) Customer behavior data (purchases, churn, engagement)
B) Operational metrics (performance, efficiency, costs)
C) Financial data (revenue, expenses, forecasts)
D) Marketing data (campaigns, conversions, attribution)
E) Other: [describe]

Q2: What problem are you trying to solve or question to answer?
A) Identify what's driving specific outcomes (root cause analysis)
B) Predict future trends or outcomes
C) Find anomalies or issues
D) Compare segments or time periods
E) Exploratory (not sure what's there yet)

Q3: What's your data literacy level?
A) Expert (I can interpret complex stats, models, technical jargon)
B) Intermediate (I understand correlations, trends, basic stats)
C) Beginner (explain in plain language, avoid jargon)

Q4: What output do you need?
A) Written summary with key findings
B) Visualizations (charts, graphs)
C) Statistical analysis (hypothesis testing, regressions)
D) Actionable recommendations
E) All of the above

Q5: Time period or segments of focus?
A) Analyze everything equally
B) Focus on recent data (last 3-6 months)
C) Compare specific segments: [describe]
D) Look for changes over time

---

**Copy-paste answer sheet:**

Q1: 
Q2: 
Q3: 
Q4: 
Q5: 
```

**You:**
```
Q1: A
Q2: A
Q3: B
Q4: D
Q5: B
```

**AI:** "Do you have any more questions I should answer before I proceed?"

**You:** "Yes; what outcomes specifically? We're seeing churn spike."

**AI:**
```
Perfect, that focuses the analysis.

Q6: When did churn start spiking?
A) Last month
B) Last quarter
C) Gradual increase over 6+ months
D) Not sure, need you to identify the pattern

Q7: Do you have hypotheses about why churn increased?
A) Yes: [describe your hypothesis]
B) No, need data to generate hypotheses

Q8: What customer segments matter most?
A) High-value customers (top 20% revenue)
B) All customers equally
C) Specific segment: [describe]

---

Q6: 
Q7: 
Q8: 
```

**You:**
```
Q6: B
Q7: B
Q8: A
```

**AI:** "Any more questions?"

**You:** "Nope, go ahead."

**AI:** *Now performs targeted analysis:*
- *Focuses on recent data (last 3-6 months)*
- *Root cause analysis for churn spike*
- *Segments high-value customers (top 20%)*
- *Identifies patterns: timing, customer characteristics, behavioral signals*
- *Outputs actionable recommendations in intermediate-level language*
- *Includes visualizations showing key findings*

**Outcome:** Instead of generic summary stats, you get specific insights: "High-value customer churn increased 34% starting in Q4. Analysis shows 78% of churned customers had support ticket response times >48 hours in the 30 days before churn. Recommendation: Prioritize support SLA for top 20% customers."

---
# Common Mistakes & How to Avoid Them

## ❌ Mistake 1: Skipping the Iteration Check
**What happens:** AI asks questions, you answer, AI immediately starts working and makes a subtle wrong assumption because it misinterpreted one of your answers.

**How to avoid:** Always include in your custom instruction: "After I provide my answers, ask: 'Do you have any more questions I should answer before I proceed?'"

**Why it matters:** Catching misunderstandings *before* generation saves 10+ minutes of revising wrong outputs.

---
## ❌ Mistake 2: Limiting Questions to "5-10"
**What happens:** Complex tasks need 12-15 questions to fully contextualize. If you cap at 5-10, the AI skips important dimensions.

**How to avoid:** Don't specify a number in your custom instruction. Let the AI ask as many questions as needed. If it's asking 20+ questions, your task is probably too broad (break it into sub-tasks).

**Why it matters:** Some research projects need 15 questions. Some LinkedIn posts need 4. Let the AI adapt to task complexity.

---
## ❌ Mistake 3: Asking Too Broadly
**What happens:** You say "Ask me questions for clarity" with no task mentioned. AI asks generic questions that don't help.

**How to avoid:** Always pair the trigger phrase with your task: "Ask me questions for clarity. I need to [specific task]."

**Example:**
- ❌ "Ask me questions for clarity."
- ✅ "Ask me questions for clarity. I need to analyze customer churn data."

---
## ❌ Mistake 4: Not Customizing the Prompt for Your Needs
**What happens:** You use the base version, but your workflow needs specific things (e.g., always include timeline questions, always ask about budget constraints, always check technical vs non-technical audience).

**How to avoid:** After using the base version 5-10 times, notice patterns in what you *always* clarify. Add those to your custom instruction as standing requirements.

**Example addition:** "When the task involves writing or communication, always ask about audience technical level and whether this is internal or external."

---
## ❌ Mistake 5: Not Testing After Setup
**What happens:** You paste the custom instruction, assume it works, then weeks later realize it's not triggering properly.

**How to avoid:** Immediately after setting up custom instructions, run 2-3 test scenarios in different task domains (research, writing, analysis). Confirm you get structured questions + answer sheet.

---
# Further Reading & Research

This guide is grounded in research on in-context learning, prompt engineering, and human-AI interaction. If you want to dive deeper:
## Core Research Papers
- **Chain-of-Thought Prompting (Wei et al., 2022)** - arXiv:2201.11903  
  Shows how intermediate reasoning steps dramatically improve LLM performance

- **A Survey on In-Context Learning (Dong et al., 2022)** - arXiv:2301.00234  
  Comprehensive overview of why context helps LLMs learn and predict better

- **CLAM: Selective Clarification (Kuhn et al., 2023)** - OpenReview:VQWuqgSoVN  
  ~20% accuracy boost from asking clarifying questions on ambiguous inputs

- **LLMs Get Lost in Multi-Turn Conversation (Laban et al., 2025)** - arXiv:2505.06120  
  Explains the 39% performance drop when LLMs make early wrong assumptions

- **SPRIG: System Prompt Optimization (Zhang et al., 2024)** - arXiv:2410.14826  
  One optimized system prompt performs across 47 task types
## Practical Guides
- **NNGroup: Prompt Structure in AI Conversations** - User research on why people don't provide context
- **Systematic Survey of Prompt Engineering (Sahoo et al., 2024)** - arXiv:2402.07927  
  Comprehensive overview of 58+ prompting techniques

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