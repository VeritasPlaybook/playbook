>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

For Table of Contents, click **Outline** button on the right ----------------------------------------------------------------------------------------------^

---
# What This Is

**The problem:** You open your AI tool and see 4-5 model options. GPT-5.4, Gemini 3.1 Pro, Claude Sonnet 4.6, Claude Opus 4.6, maybe others. You pick one. Maybe it's the default. Maybe it's whichever name you recognize. You get decent results most of the time, so you never think about it again.

But "decent" is leaving performance on the table. Each of these models was built with fundamentally different design priorities. One dominates at abstract reasoning but takes 30-40 seconds to start responding. Another is 95% as capable as the premium option at 1/5th the cost. A third can process an entire codebase at once and maintain accuracy where the others fall apart. Using the wrong model for the wrong task is like using a screwdriver as a hammer. It works, technically. But you're fighting the tool instead of leveraging it.

**The solution:** A practical decision framework that tells you which model to use for which task, why, and when to switch. No benchmark tables to memorize. No spec sheets to compare. Just: "I need to do X, so I should use Y, because Z."

**The result:** Better outputs on the first try. Lower costs when you don't need the premium model. Higher reliability when you do. And a clear mental model for evaluating new models as they release.

This guide is current as of **March 2026**. The specific models will change. The framework for choosing between them won't.

---

## What Makes This Guide Different

Most model comparisons are spec sheets: benchmark scores, context windows, pricing tables. That's useful if you're an ML engineer evaluating API integrations. This isn't that. It's built for product managers, researchers, and knowledge workers who need to decide which model to open on Tuesday morning for a specific task, not which one wins on a leaderboard.

I built this guide from the opposite direction. I spent weeks doing deep research across every major model available in March 2026: comparing independent benchmarks, reading developer reports, cross-checking measurements, and testing real-world tasks. Then I distilled that into the thing I actually needed: a decision framework I could reference in 30 seconds when starting any task.

If you want the full data with 48 cited sources, that's available separately. This is the practical layer on top of that research.

**This is the third guide in a series:**

- [The Context Prompt That Will Revolutionize Your Workflow](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md) - How to get AI to ask smart clarifying questions before doing any work (works with every model)
- [A Practical RLM-Inspired Workflow for Deep Research with AI](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/A%20Practical%20RLM-Inspired%20Workflow%20for%20Deep%20Research%20with%20AI.md) - A 7-phase research methodology grounded in MIT research on Recursive Language Models
- **This guide** - Which model to use for which task, and why

All three work together. The context prompt pattern works across all models. The research workflow benefits from strategic model selection at each phase. And this guide gives you the model knowledge to make those selections well.

---

**What's in this guide:**
- The five frontier models available in March 2026, explained in plain language
- A decision framework: which model for which task
- The Sonnet vs. Opus question (the most common model selection decision)
- Platform trade-offs: Perplexity vs. native platforms
- Expert perspectives that change how you think about model capabilities
- Common mistakes people make when choosing models
- Quick reference tables you can bookmark

---
# Quick Start

**Want the answer without reading the full guide? Here's the 80/20:**

## The Default Stack (Works for Most People)

| What you're doing | Use this model |
|---|---|
| Most tasks (coding, writing, research, analysis) | **Claude Sonnet 4.6** |
| High-stakes analysis, complex architecture, large documents | **Claude Opus 4.6** |
| Hard science, math, abstract reasoning | **Gemini 3.1 Pro** |
| Browser automation, desktop control, multi-step web tasks | **GPT-5.4** |
| High-volume batch processing, cost-sensitive pipelines | **Nemotron 3 Super** |

## The One Rule That Matters

Start with Sonnet 4.6. Escalate to Opus 4.6 when the task is complex enough that a subtle reasoning error would be expensive to fix. Use Gemini 3.1 Pro when the problem is genuinely hard science or abstract logic. Use GPT-5.4 when the task requires controlling a computer or browser. Use Nemotron 3 Super when you're running thousands of inference calls and cost is the constraint.

If this is enough for you, bookmark this page and come back when you need more detail. If you want to understand *why* this framework works and when the defaults break down, keep reading.

---
# The Five Models, Explained Simply

Each model was built with a different philosophy about what "intelligence" means. Understanding those philosophies is more useful than memorizing benchmark scores.

## GPT-5.4: The Agentic Executor

**Built by:** OpenAI | **Released:** March 5, 2026

**What it's optimized for:** Doing things in the real world. GPT-5.4 is the first general-purpose model with native computer use. It can see your screen, move cursors, click buttons, type text, and navigate desktop applications. On [OSWorld](https://openai.com/index/introducing-gpt-5-4/), which tests a model's ability to use desktop environments through screenshots and keyboard/mouse actions, GPT-5.4 scores 75.0%, surpassing human performance at 72.4%.

**What makes it unique:** Configurable reasoning effort. Five discrete levels from "none" to "xhigh" that let you explicitly trade off cost vs. depth. Fast shallow inference for routine tasks, deep reasoning only when needed. No other model exposes this control with the same granularity. OpenAI also claims a [33% reduction in hallucinations](https://www.glbgpt.com/hub/gpt-5-4-pricing/) compared to the previous generation, which matters for compliance documentation, legal review, or financial analysis.

**In plain language:** GPT-5.4 is the model that can actually *do* things on a computer, not just tell you how. If your task involves navigating websites, filling out forms, automating desktop workflows, or multi-step web research that requires clicking through pages, GPT-5.4 is the right choice.

**Where it falls short:** Raw reasoning speed. The model is moderate on token throughput compared to the fastest options. For pure text generation tasks where you don't need computer interaction, other models are faster or cheaper.

---

## Gemini 3.1 Pro: The Reasoning Powerhouse

**Built by:** Google DeepMind | **Released:** February 19, 2026

**What it's optimized for:** Pure reasoning. Gemini 3.1 Pro holds the [highest score ever recorded on GPQA Diamond](https://almcorp.com/blog/gemini-3-1-pro-complete-guide/) (94.3%), a benchmark testing graduate-level biology, chemistry, and physics. Its [ARC-AGI-2 score of 77.1%](https://almcorp.com/blog/gemini-3-1-pro-complete-guide/) is more than double what the previous Gemini achieved just three months earlier, and it's independently validated by the ARC Prize organization. It ties with GPT-5.4 at #1 on the [Artificial Analysis Intelligence Index](https://artificialanalysis.ai/models/comparisons/nvidia-nemotron-3-super-120b-a12b-vs-claude-4-5-sonnet-thinking).

**What makes it unique:** A thinking mode that allocates additional compute to extended reasoning chains before generating a response. This makes it considerably more capable than even its benchmark numbers suggest for hard logical problems. It also leads on [web research synthesis](https://blog.laozhang.ai/en/posts/gpt-5-4-vs-gemini-3-1) (BrowseComp: 85.9%) and [competitive programming](https://almcorp.com/blog/gemini-3-1-pro-complete-guide/) (LiveCodeBench Elo: 2887).

**In plain language:** Gemini 3.1 Pro is the model you use when the problem is genuinely hard. Graduate-level scientific analysis, complex mathematical proofs, abstract reasoning tasks that require sustained logical chain-of-thought across novel problem domains. It's the smartest model in the room on raw reasoning.

**Where it falls short:** Two critical issues. First, **latency**. Time to First Token has been [independently measured at 29-44 seconds](https://blog.laozhang.ai/en/posts/gpt-5-4-vs-gemini-3-1), versus a peer median of about 1.2 seconds. That's a painful wait in interactive workflows. Second, **long-context retrieval**. Despite having a massive context window on paper, Gemini 3.1 Pro's accuracy [drops to 26.3% on MRCR v2 at 1M tokens](https://docsbot.ai/models/compare/gemini-3-1-pro/gpt-5-4), compared to Claude Opus 4.6's 78.3%. The context window exists, but retrieval accuracy degrades severely at the extreme end.

---

## Claude Sonnet 4.6: The Everyday Workhorse

**Built by:** Anthropic | **Released:** February 17, 2026

**What it's optimized for:** Being good enough at almost everything. That sounds like a backhanded compliment, but it's actually the most valuable position in the lineup. Sonnet 4.6 scores [79.6% on SWE-Bench](https://www.nxcode.io/resources/news/claude-sonnet-4-6-complete-guide-benchmarks-pricing-2026) (real GitHub issues), within 1.2 points of Opus 4.6. It scores [72.5% on OSWorld](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en), within 0.2 points of Opus. Anthropic's own engineers [preferred Sonnet 4.6 over the previous generation](https://www.glbgpt.com/hub/claude-sonnet-4-6-vs-claude-opus-4-6-2026-ultimate-comparison-guide/) in nearly 70% of coding scenarios.

**What makes it unique:** The price-to-performance ratio. At $3/$15 per million tokens (input/output), Sonnet handles [80-90% of real-world scenarios at 95-99% of Opus quality](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en). As of March 13, 2026, Anthropic [dropped the long-context surcharge entirely](https://the-decoder.com/anthropic-drops-the-surcharge-for-million-token-context-windows-making-opus-4-6-and-sonnet-4-6-far-cheaper/), making the 1M token context window available at standard pricing. It's also significantly faster than Opus in interactive sessions: 180-300ms Time to First Token versus Opus's 500-700ms. Over a full day of iterative work, that speed difference compounds.

**In plain language:** Sonnet 4.6 is the model you should be using most of the time. Coding, writing, research synthesis, document analysis, iterative prompt-and-refine workflows. Unless your task hits one of the specific triggers that call for a different model, Sonnet is the default.

**Where it falls short:** The gap with Opus emerges at the upper edge of difficulty. [GPQA Diamond: 74.1% vs Opus's 91.3%](https://www.glbgpt.com/hub/claude-sonnet-4-6-vs-claude-opus-4-6-2026-ultimate-comparison-guide/), a 17-point gap on graduate-level scientific reasoning. Multi-file codebase refactors requiring architectural reasoning across 10+ files. Long-chain multi-agent coordination where failure loops are expensive. High-stakes synthesis across ambiguous inputs where reliability matters more than speed.

---

## Claude Opus 4.6: The Frontier Specialist

**Built by:** Anthropic | **Released:** February 4, 2026

**What it's optimized for:** Maximum reasoning depth under cognitive load. Opus 4.6 is the model you call when the task is complex enough that subtle errors are expensive. Where Sonnet may drift or simplify trade-offs when prompts combine multiple simultaneous constraints (performance optimization, security, backward compatibility, extensibility), [Opus maintains stronger internal consistency](https://emergent.sh/learn/claude-sonnet-vs-opus) and is less prone to overlooking secondary requirements.

**What makes it unique:** Two things. First, [long-context stability at 1M tokens](https://www.reddit.com/r/ClaudeAI/comments/1rsubm0/1_million_context_window_is_now_generally/). On MRCR v2 at 1M tokens (needle-in-haystack retrieval across an entire million-token context), Opus scores 78.3%, the highest of any leading model. Gemini drops to 26.3% at the same length. Second, [128K maximum output tokens](https://www.anthropic.com/news/claude-opus-4-6), the highest in this group, which allows generating complete application modules or comprehensive reports in a single response.

**In plain language:** Opus 4.6 is the model for when the cost of getting it wrong is higher than the cost of using a more expensive model. Multi-file architectural refactors, expert-level scientific analysis, complex compliance review, large document corpus analysis, long agentic chains where failure loops must succeed on the first or second try.

**Where it falls short:** Cost and speed. At $5/$25 per million tokens, it's 1.67x more expensive than Sonnet. 20-30 tokens/second versus Sonnet's 40-60. 500-700ms TTFT versus Sonnet's 180-300ms. If the task doesn't require Opus's depth, you're paying more for slower responses with no meaningful quality improvement.

---

## Nemotron 3 Super: The Open-Source Pipeline Engine

**Built by:** NVIDIA | **Released:** March 10, 2026

**What it's optimized for:** Speed, cost, and full transparency. Nemotron 3 Super is a [Hybrid Mamba-Transformer Mixture-of-Experts model](https://www.greptile.com/blog/nvidia-nemotron-super-in-code-review): 120 billion total parameters, only 12 billion active during inference, with Multi-Token Prediction for efficiency. This architecture allows it to operate at [up to 484 tokens per second](https://www.linkedin.com/pulse/nvidia-nemotron-3-super-new-leader-open-efficient-trmlc), far faster than any closed model. And the cost: [$0.10/M input tokens](https://tokencost.app/blog/nvidia-nemotron-3-super-pricing) at DeepInfra, which is 25x cheaper than GPT-5.4 and 50x cheaper than Claude Opus 4.6.

**What makes it unique:** It's [fully open source](https://www.reddit.com/r/LocalLLaMA/comments/1rqy3cx/nemotron_3_super_released/). Not just open weights, but training data, RL pipeline, everything. For enterprise deployments requiring data sovereignty, or research environments needing full training transparency, this matters. Its 85.6% [PinchBench score](https://developer.nvidia.com/blog/introducing-nemotron-3-super-an-open-hybrid-mamba-transformer-moe-for-agentic-reasoning/) (agentic task orchestration) is extraordinary for an open-source model.

**In plain language:** Nemotron 3 Super is not a replacement for GPT-5.4, Gemini, or Claude in general-purpose tasks. Its [Intelligence Index score of 36](https://artificialanalysis.ai/articles/nvidia-nemotron-3-super-the-new-leader-in-open-efficient-intelligence) sits well below the leaders. It can't process images. It's not built for nuanced writing or real-time chat. What it is: the fastest, most affordable model for multi-agent pipelines, batch processing, and agentic automation tasks where speed and cost dominate over raw intelligence. If you're running thousands of inference calls, building orchestration layers, or need a model you can self-host, Nemotron is the right tool.

**Where it falls short:** Complex reasoning, graduate-level analysis, visual inputs, nuanced writing, real-time conversation quality. Don't use it as a general-purpose chatbot.

---
# The Decision Framework

## Start Here: The Escalation Model

The hybrid escalation model has become [standard practice among enterprise teams in 2026](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en). It works like this:

1. **Default:** Claude Sonnet 4.6 handles 80-90% of all tasks
2. **Escalate to Opus 4.6** when the task is complex + the cost of error is high
3. **Switch to Gemini 3.1 Pro** when the task requires pure abstract reasoning or hard science
4. **Switch to GPT-5.4** when the task requires computer/browser interaction
5. **Switch to Nemotron 3 Super** when running high-volume pipelines where cost is the constraint

This achieves [60-80% cost reduction](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en) compared to using the premium model for everything, while maintaining high-quality output where it matters.

## The Complete Task Routing Guide

### Everyday Work

| Task | Best Model | Why |
|---|---|---|
| Writing, editing, refining documents | Sonnet 4.6 | Strong instruction-following, fast iteration |
| Coding: features, debugging, scaffolding | Sonnet 4.6 | 79.6% SWE-Bench, 2-3x faster than Opus in interactive sessions |
| Research synthesis and summaries | Sonnet 4.6 | Good balance of quality and speed |
| Email drafts, LinkedIn posts, communications | Sonnet 4.6 | Consistent tone, fast turnaround |
| Quick data analysis | Sonnet 4.6 | Handles most analytical tasks well |
| PRDs, specs, technical documentation | Sonnet 4.6 | Excellent at structured long-form output |

### Complex / High-Stakes Work

| Task | Best Model | Why |
|---|---|---|
| Multi-file codebase refactors (10+ files) | Opus 4.6 | Maintains architectural coherence across large changes |
| Compliance review across multiple jurisdictions | Opus 4.6 | Multi-constraint stability, less prone to overlooking requirements |
| Expert-level scientific or technical analysis | Gemini 3.1 Pro | 94.3% GPQA Diamond, strongest abstract reasoning |
| System architecture decisions | Opus 4.6 | Trade-off analysis across entire systems |
| 1M+ token document analysis | Opus 4.6 | 78.3% retrieval accuracy at 1M tokens vs. Gemini's 26.3% |
| High-stakes financial or legal analysis | Opus 4.6 | Reasoning depth where silent errors are expensive |
| Complex mathematical proofs | Gemini 3.1 Pro | Extended reasoning chains, thinking mode |

### Agentic / Automation Work

| Task | Best Model | Why |
|---|---|---|
| Browser automation and web navigation | GPT-5.4 | Only model with native computer use that beats human baselines |
| Desktop application control | GPT-5.4 | 75% OSWorld, native screen reading and mouse/keyboard control |
| Multi-step web research requiring page interaction | GPT-5.4 | Computer use + strong reasoning |
| Batch processing at scale | Nemotron 3 Super | $0.10/M tokens, 484 t/s |
| Multi-agent pipeline substeps | Nemotron 3 Super | 85.6% PinchBench, optimized for orchestration |
| Self-hosted enterprise deployments | Nemotron 3 Super | Fully open source, data sovereignty |

### Strategic Model Combinations

| Workflow | Approach | Why |
|---|---|---|
| Draft then review | Sonnet 4.6 (draft) then Opus 4.6 (review) | Fast drafting + rigorous final check |
| Research with hard science components | Sonnet 4.6 (retrieval) + Gemini 3.1 Pro (analysis) | Speed for gathering, reasoning depth for interpreting |
| High-volume automation with quality gates | Nemotron 3 Super (bulk) + Opus 4.6 (validation) | Cost-efficient at scale with reliability where it counts |
| Cross-model validation on critical questions | Run GPT-5.4 + Opus 4.6 + Gemini 3.1 Pro in parallel | Independent triangulation of answers |

---
# The Sonnet vs. Opus Decision

This deserves its own section because it's the model selection decision you'll make most often. Both are Anthropic models, both have 1M token context windows, and the benchmark gaps are small enough to be misleading.

## Where They're Nearly Identical

- **SWE-Bench Verified** (real GitHub issues): 79.6% vs 80.8% - a [1.2-point gap](https://www.datastudios.org/post/claude-sonnet-4-6-vs-opus-4-6-2026-comparison-capability-split-output-ceilings-long-context-beha)
- **OSWorld** (desktop automation): 72.5% vs 72.7% - a [0.2-point gap](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en)
- Most everyday coding, writing, and analysis tasks

On these benchmarks, you're paying 1.67x more for Opus and getting near-identical results. The math doesn't work.

## Where Opus Pulls Ahead

The divergence only becomes visible at the **upper edge of difficulty**:

- **GPQA Diamond** (graduate-level science): 74.1% vs [91.3%](https://www.glbgpt.com/hub/claude-sonnet-4-6-vs-claude-opus-4-6-2026-ultimate-comparison-guide/) - a 17-point gap
- **Long-context retrieval at 1M tokens**: Opus maintains [78.3% accuracy](https://www.reddit.com/r/ClaudeAI/comments/1rsubm0/1_million_context_window_is_now_generally/) where others degrade
- **Multi-file refactors** requiring architectural reasoning across an entire system
- **Multi-constraint prompts** where Sonnet starts simplifying trade-offs or dropping secondary requirements
- **Long agentic chains** where each reasoning error compounds

## The Decision Trigger

Ask yourself one question: **"If this model makes a subtle reasoning error, how expensive is that to fix?"**

- If the answer is "I'll catch it in review" or "I can just re-run it": use **Sonnet**
- If the answer is "It could cascade through a production system" or "I won't notice until it's too late": use **Opus**

## Practical Examples

**Use Sonnet for:**
- Writing and refining PRDs, specs, or compliance documentation
- Coding features of moderate complexity (REST endpoints, schemas, utilities, frontend components)
- Iterative agentic loops where speed matters and retries are cheap
- Running high-volume drafting tasks where per-unit cost compounds
- Loading a document under 200K tokens for analysis
- Any task where you have automated validation (tests, linters, review) that catches errors

**Use Opus for:**
- Multi-file refactors touching 10+ files simultaneously, especially legacy-to-modern migrations
- Architectural decisions requiring trade-off analysis across an entire system
- Deep synthesis across ambiguous, competing inputs where silent reasoning failures are expensive
- Expert-level scientific or technical analysis
- 1M token context sessions with high retrieval accuracy requirements
- Long agentic chains (multi-day, multi-tool) where failure loops must succeed quickly
- High-stakes document analysis for legal, compliance, or financial decisions
- Single-shot deliverables requiring 64K+ output tokens in one coherent response

## Speed and Latency in Practice

Sonnet's [40-60 t/s and 180-300ms TTFT versus Opus's 20-30 t/s and 500-700ms TTFT](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en) means Sonnet feels 2-3x more responsive in interactive sessions. Over a full day of iterative prompt-and-refine cycles, that difference in cognitive flow is more significant than it sounds on paper.

---
# Platform Trade-Offs: One Subscription vs. Native Access

## The Perplexity Advantage

I use [Perplexity](https://www.perplexity.ai/) as my primary interface, and the reason is simple: Pro and Max tiers give you GPT-5.4, Gemini 3.1 Pro, Claude Sonnet 4.6, and Claude Opus 4.6 under one subscription. No separate accounts for OpenAI, Google, and Anthropic. No tab-switching mid-workflow. That model flexibility is genuinely useful when you're working through the decision framework in this guide.

Perplexity also layers real-time web retrieval on top of whichever model you select. The retrieval pipeline determines the factual boundary of the answer (sources are collected and ranked before the model generates). The model determines composition, reasoning depth, and style. This means when using Perplexity for research, factual grounding comes from retrieval regardless of model, and your model choice is most meaningful for reasoning quality and synthesis depth.

For [Max subscribers](https://www.linkedin.com/posts/juliangoldieseo_new-perplexity-computer-update-is-insane-activity-7437213067584638976-kZlt), the **Model Council** feature runs GPT-5.4, Claude Opus 4.6, and Gemini 3.1 Pro simultaneously in parallel. A synthesizer model reviews all three independent outputs, finds convergence, flags disagreement, and delivers one structured response with a confidence signal. For genuinely hard, high-stakes research questions where you want independent triangulation, this is one of the most powerful features in any AI product right now.

## What You Give Up

Each platform has exclusive features that aren't available through aggregators:

| Platform | What you get natively that you lose through aggregators |
|---|---|
| **OpenAI (ChatGPT)** | Image generation (DALL-E/GPT-native), voice mode, custom GPTs, Canvas editor, memory across conversations |
| **Anthropic (Claude)** | Projects (persistent context across conversations), Artifacts (inline code/document generation), fine-grained system prompts |
| **Google (Gemini)** | Deep Google Workspace integration (Docs, Sheets, Drive), Gems (custom personas), NotebookLM integration |

## The Practical Recommendation

Use a multi-model platform like Perplexity as your **primary research and analysis interface**. It gives you model flexibility and built-in retrieval. Use native platforms when you need their **exclusive features**: Claude Projects for persistent project context, ChatGPT for image generation, Gemini for deep Google Workspace integration.

This isn't about picking one. It's about knowing which tool to open for which task.

---
# Expert Perspectives Worth Knowing

Two perspectives from frontier AI researchers that fundamentally change how you should think about model capabilities.

## The Benchmark Trap (Ilya Sutskever)

Ilya Sutskever, co-founder of OpenAI and now at Safe Superintelligence Inc., gave the clearest framing I've found for calibrating expectations around these models. His [observation](https://globaladvisors.biz/2025/11/26/quote-ilya-sutskever-safe-superintelligence-2/):

> "A competitive programmer who practices 10,000 hours on competition problems will be highly skilled within that narrow domain but often fails to transfer that knowledge flexibly to broader engineering challenges. Current models resemble that hyper-specialized competitor rather than the flexible, adaptive learner."

**Why this matters for you:** A model scoring 80% on SWE-Bench will still fail in ways that feel surprising. The 20% it misses is not randomly distributed. It clusters at precisely the kind of novel, transfer-requiring problems that actually matter in production. Treat benchmark scores as directional indicators, not guarantees.

Sutskever's broader point: the [scaling paradigm that produced the current generation of models is approaching exhaustion](https://www.dwarkesh.com/p/ilya-sutskever-2). The next leap requires something architecturally different, not just bigger models trained on more data.

## The Reasoning Paradigm Shift (Geoffrey Hinton)

Geoffrey Hinton, Nobel Prize laureate and widely regarded as the "godfather of AI," has [shifted his commentary](https://www.reddit.com/r/artificial/comments/1q9an1z/geoffrey_hinton_says_llms_are_no_longer_just/) toward what I think is the more useful framing of what reasoning models actually represent:

> "LLMs are no longer just predicting the next word. New models learn by reasoning and identifying contradictions in their own logic."

He's also [explicitly skeptical](https://www.persuasion.community/p/geoffrey-hinton) of hybrid symbolic approaches: "People who want hybrid systems, consisting of neural nets for the input and output and symbolic AI for the reasoning, are trying to cling to the past."

**Why this matters for you:** The models with explicit reasoning modes (Gemini 3.1 Pro's thinking mode, Claude's adaptive reasoning, GPT-5.4's configurable effort levels) represent a genuine architectural shift, not just a marketing label. When you enable thinking/reasoning mode, you're not getting the same model "trying harder." You're activating a different inference pathway. That's why model selection now includes not just *which* model, but *which reasoning mode* within that model. Practical takeaway: don't benchmark one model's default mode against another's reasoning mode. That comparison tells you nothing useful.

Hinton and Sutskever have also [co-endorsed a major 2025 paper](https://fortune.com/2025/07/22/researchers-ai-labs-google-openai-anthropic-warn-losing-ability-understand-advanced-models/) warning that as chain-of-thought reasoning becomes more sophisticated, frontier labs risk losing the ability to understand their own models. Worth knowing if you're building systems that depend on AI reasoning being interpretable.

---
# Common Mistakes

## ❌ Mistake 1: Using the Same Model for Everything

**What happens:** You pick Claude Opus because "it's the best" and use it for everything, including quick drafts and simple questions where Sonnet would produce identical results 3x faster at 1/5th the cost.

**How to avoid:** Sonnet 4.6 is your default. Escalate only when the task complexity or error cost justifies it. After a week of conscious model selection, it becomes automatic.

---

## ❌ Mistake 2: Choosing Based on Benchmark Headlines

**What happens:** You read "Gemini 3.1 Pro is #1 on the Intelligence Index" and switch to it for everything. Then you wonder why it takes 30-40 seconds to start responding and why your long-document analysis is missing information.

**How to avoid:** Benchmarks measure specific capabilities under specific conditions. GPQA Diamond measures graduate-level science. ARC-AGI-2 measures abstract reasoning. Neither measures "will this model write a good PRD" or "will this model be pleasant to use interactively." Match the model to the actual task, not the headline.

---

## ❌ Mistake 3: Ignoring Context Window Quality

**What happens:** You see "1M token context window" on three different models and assume they're equivalent. You load a million tokens into Gemini 3.1 Pro and wonder why it's missing information that Claude Opus 4.6 finds reliably.

**How to avoid:** Advertised context length is not retrieval accuracy. Gemini 3.1 Pro leads at 128K tokens but [drops to 26.3% accuracy at 1M tokens](https://docsbot.ai/models/compare/gemini-3-1-pro/gpt-5-4). Opus maintains [78.3% at the same length](https://www.reddit.com/r/ClaudeAI/comments/1rsubm0/1_million_context_window_is_now_generally/). For documents under 128K, any model works. For truly massive contexts, Opus is the reliable choice.

---

## ❌ Mistake 4: Not Using Reasoning Modes

**What happens:** You ask a complex question and get a mediocre answer, not realizing the model has a reasoning/thinking mode that would have produced a dramatically better response.

**How to avoid:** For hard problems, enable reasoning mode explicitly. Gemini 3.1 Pro's thinking mode, Claude's extended thinking (adaptive or max), GPT-5.4's effort levels (set to "high" or "xhigh"). The difference on complex tasks can be enormous.

---

## ❌ Mistake 5: Treating Nemotron 3 Super as a General-Purpose Model

**What happens:** You hear "open source, 484 tokens per second, 25x cheaper" and try to use it for everything. The outputs are noticeably worse than Claude or GPT for nuanced tasks.

**How to avoid:** Nemotron 3 Super is a specialist. It excels at multi-agent pipeline substeps, batch processing, and agentic automation. It does not replace Claude, GPT, or Gemini for general-purpose work. Use it where its strengths apply: speed, cost, and orchestration at scale.

---
# Quick Reference Card

## Model Strengths at a Glance

| Model | Best At | Worst At | Cost (Input/Output per M tokens) |
|---|---|---|---|
| **GPT-5.4** | Computer use, browser automation, multi-step web tasks | Raw speed for text-only tasks | $2.50 / $15.00 |
| **Gemini 3.1 Pro** | Abstract reasoning, hard science, competitive coding | Latency (29-44s TTFT), long-context retrieval at 1M | $2.00 / $12.00 |
| **Claude Sonnet 4.6** | Everything at 95-99% quality, speed, cost efficiency | Upper-edge complexity, graduate-level science | $3.00 / $15.00 |
| **Claude Opus 4.6** | Multi-constraint reasoning, long-context stability, max output | Cost, speed, tasks that don't need the depth | $5.00 / $25.00 |
| **Nemotron 3 Super** | Batch pipelines, agentic orchestration, self-hosting | General-purpose tasks, visual input, nuanced writing | $0.10 / $0.50 |

## Decision Flowchart

```
Start with your task
    |
    v
Does it require controlling a computer/browser?
    |-- Yes --> GPT-5.4
    |-- No
        |
        v
    Is it hard science, complex math, or abstract reasoning?
        |-- Yes --> Gemini 3.1 Pro (with thinking mode)
        |-- No
            |
            v
        Is it high-stakes with expensive error consequences?
            |-- Yes --> Claude Opus 4.6
            |-- No
                |
                v
            Is it high-volume batch processing?
                |-- Yes --> Nemotron 3 Super
                |-- No
                    |
                    v
                Claude Sonnet 4.6 (default)
```

## Key Numbers to Remember

- **Sonnet vs. Opus gap on coding benchmarks:** 1.2 points (negligible for most tasks)
- **Sonnet vs. Opus gap on graduate-level science:** 17 points (massive; use Opus or Gemini)
- **Gemini's long-context accuracy at 1M tokens:** 26.3% (use Opus instead for large documents)
- **Opus's long-context accuracy at 1M tokens:** 78.3% (best in class)
- **Nemotron's cost advantage:** 25-50x cheaper than closed models
- **Gemini's TTFT:** 29-44 seconds (plan for the wait)
- **Sonnet vs. Opus speed:** 2-3x faster interactive response

---
# Honest Caveats

One framing note before the specifics: I'm a product manager, not an ML engineer. I built this guide from weeks of reading, testing, and synthesizing, not from implementing these models at the infrastructure level. The recommendations reflect how I use these models daily for research, documentation, and analysis. If your primary use case is significantly different, adapt the framework.

Several additional limitations to keep in mind:

1. **This guide reflects March 2026.** Models update frequently. GPT-5.4 launched March 5, Gemini 3.1 Pro on February 19, both Claudes in February. By the time you read this, there may be newer versions or updated benchmarks. The decision *framework* (match model to task type) will still hold. The specific rankings may shift.

2. **Benchmark scores don't predict real-world results.** As Sutskever noted, models are optimized for evaluation tasks and fail in ways that cluster at exactly the novel problems you'll actually encounter. Treat the numbers as directional signals, not guarantees. I've been surprised by both models outperforming and underperforming their benchmarks on specific tasks.

3. **GPT-5.4 latency specs are incomplete.** OpenAI hasn't published comprehensive latency data. "Moderate" is the best characterization available from independent testing.

4. **Nemotron 3 Super can't process images.** No visual input at all. If your task involves screenshots, diagrams, charts, or any visual content, Nemotron is not an option.

5. **Gemini 3.1 Pro is still in Preview.** Some performance characteristics, including the extreme TTFT, may improve as it moves to general availability.

6. **Your mileage may vary.** If your primary use case is significantly different from mine (pure software engineering, creative writing, academic research), you may find different models work better for your specific workflow. Adapt the framework to your context.

---
# How This Connects to the Other Guides

This guide tells you **which model to use**. The other two guides in the series tell you **how to use any model more effectively**, and I'd recommend reading them in order if you haven't already:

- **[The Context Prompt That Will Revolutionize Your Workflow](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md)** - Before you start any task with any model, force the AI to ask smart clarifying questions. Works across all five models. The better context you provide, the less the model choice matters for everyday tasks.

- **[A Practical RLM-Inspired Workflow for Deep Research with AI](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/A%20Practical%20RLM-Inspired%20Workflow%20for%20Deep%20Research%20with%20AI.md)** - A 7-phase research methodology where model selection at each phase matters. Use fast models for retrieval (Phase 2), reasoning models for analysis (Phase 3), and fresh models for adversarial review (Phase 6). This guide gives you the knowledge to make those phase-specific model selections well.

---
# Further Reading & References

This guide is built on independent benchmarks, developer reports, and research across every major model available in March 2026. If you want to verify the data behind any recommendation or go deeper on a specific model:

## Key Sources Used in This Guide

- [Introducing GPT-5.4 - OpenAI](https://openai.com/index/introducing-gpt-5-4/) - Official release announcement and benchmark data
- [Gemini 3.1 Pro: Benchmarks, Pricing & Full Access Guide](https://almcorp.com/blog/gemini-3-1-pro-complete-guide/) - Independent benchmark verification including ARC-AGI-2 validation
- [Claude Sonnet 4.6 Guide: Benchmarks, Pricing & How It Compares](https://www.nxcode.io/resources/news/claude-sonnet-4-6-complete-guide-benchmarks-pricing-2026) - Comprehensive Sonnet 4.6 analysis
- [Introducing Claude Opus 4.6 - Anthropic](https://www.anthropic.com/news/claude-opus-4-6) - Official release with 1M context and 128K output specs
- [Introducing Nemotron 3 Super - NVIDIA Developer Blog](https://developer.nvidia.com/blog/introducing-nemotron-3-super-an-open-hybrid-mamba-transformer-moe-for-agentic-reasoning/) - Architecture details and PinchBench results
- [Claude Sonnet 4.6 vs Opus 4.6 Comparison 2026](https://webscraft.org/blog/claude-sonnet-46-vs-opus-46-povne-porivnyannya?lang=en) - Independent Sonnet vs Opus analysis with cost modeling
- [Claude Sonnet vs Opus (2026): Which Claude Model Is Actually Worth It?](https://emergent.sh/learn/claude-sonnet-vs-opus) - Enterprise decision framework
- [GPT-5.4 vs Gemini 3.1 Pro: Full Developer Comparison](https://blog.laozhang.ai/en/posts/gpt-5-4-vs-gemini-3-1) - Independent latency measurements and BrowseComp data
- [Anthropic drops the surcharge for million-token context windows](https://the-decoder.com/anthropic-drops-the-surcharge-for-million-token-context-windows-making-opus-4-6-and-sonnet-4-6-far-cheaper/) - March 2026 pricing update
- [Ilya Sutskever on Superintelligence - Dwarkesh Podcast](https://www.dwarkesh.com/p/ilya-sutskever-2) - Scaling paradigm exhaustion and generalization
- [Geoffrey Hinton on Artificial Intelligence - Persuasion](https://www.persuasion.community/p/geoffrey-hinton) - Reasoning paradigm shift and hybrid systems critique
- [NVIDIA Nemotron 3 Super: The new leader in open, efficient intelligence - Artificial Analysis](https://artificialanalysis.ai/articles/nvidia-nemotron-3-super-the-new-leader-in-open-efficient-intelligence) - Intelligence Index data and benchmark comparisons
- [Researchers from top AI labs warn they may be losing the ability to understand advanced models - Fortune](https://fortune.com/2025/07/22/researchers-ai-labs-google-openai-anthropic-warn-losing-ability-understand-advanced-models/) - CoT transparency concerns

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

Based on "The 2026 Frontier Model Playbook" by VeritasPlaybook
Original: [https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%202026%20Frontier%20Model%20Playbook.md](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%202026%20Frontier%20Model%20Playbook.md)
License: CC BY 4.0

---

# Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- 💼 [LinkedIn](https://www.linkedin.com/in/malocilja/?view=public)
- 🐙 [Veritas Playbook - GitHub](https://github.com/VeritasPlaybook/playbook)
- 📊 [Investment Research](https://github.com/Veritas-Research/investment-research)

---

*If you found this valuable, star ⭐ the repo to help others find it.*