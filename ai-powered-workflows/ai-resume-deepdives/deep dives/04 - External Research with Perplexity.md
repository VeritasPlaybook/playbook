>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# External Research with Perplexity (and Others)

This deep dive expands Step 8 of the main guide. The main guide explained why external research belongs outside the main Cowork thread and gave you three research angles. This is the longer version: the exact prompt patterns Claude writes for you, how to read the output, the red-flag library that decides whether to apply at all, the alternative tools that work if you do not use Perplexity, and the criteria for walking away from a role before you invest an hour tailoring an application.

The research step is the highest-leverage step in the workflow. Half the time, the most valuable output of this step is a "do not apply" decision that saves you the hour the rest of the workflow would consume. Tailoring is cheap when you have the system; deciding which jobs deserve the tailoring is the part with real returns.

---

# Why External Research Belongs Outside the Main Session

The main Cowork thread is doing one thing: tailoring your application to the Job Description (JD). It needs your Career Brain Trust loaded, the JD parsed, and a focused conversation about phrasing, framing, and tone. Mixing live research into that thread pollutes the context. The model now has to juggle "what did I write about my last role" alongside "what is this company's revenue model" alongside "what is the team culture at this company." The drafting quality drops because the model is now context-switching.

There is also a tool-suitability argument. The job of company research is finding live web sources, citing them, and synthesizing across multiple results. Perplexity is built for exactly this. It has live web access, structured citations, and a Deep Research mode that runs for several minutes across many sources before returning a structured answer. Claude inside Cowork has live web access too, but using Claude for the research step pulls the main thread's focus away from drafting. Better to keep the tools doing what each is best at.

There is a third reason that becomes obvious only after about ten applications. Research belongs in a separate file in the project folder so you can read it again later. If the research is interleaved with the drafting conversation, you cannot easily extract it. If the research is a standalone Markdown file in the project folder, you can re-open it during the interview prep step, you can compare research across applications to spot industry-level patterns, and you can paste it into a future conversation if a related role comes up.

So the rule: tailoring lives in the main Cowork thread. Research lives in Perplexity (or another deep research tool), with the output saved as a Markdown file in the project folder. The two never share a context window.

---

# Picking Your Deep Research Tool and Mode

Before the prompt patterns, the practical question: which tool do you run them in, and which mode inside that tool?

**Two modes, across every tool.** Whichever tool you pick, you will use both modes during a single application's research:

- **Quick mode.** Fast, one-shot search. Returns in roughly thirty seconds. Use for spot checks: "Who is the Chief Executive Officer (CEO) and how long have they been there?" "Has this company been in the news in the last six months?" Good for follow-ups and small clarifications, not for the main angles.
- **Deep Research mode.** Slow, thorough research. Runs for several minutes across dozens of sources, organizes findings into structured sections with citations, returns a long Markdown report. Use this mode for the three main research prompts below (company, team, role context). The investment is roughly five to ten minutes per prompt. For a senior role you would otherwise spend an hour tailoring for, five to ten minutes of Deep Research before deciding to apply is a high-leverage trade.

Most applications need exactly three Deep Research runs plus two or three quick-mode follow-ups, all happening in parallel while the main Cowork thread sits open. By the time the research returns, you are ready to fold the findings into the draft.

**Four tools that work.** The prompt patterns later in this deep dive transfer cleanly across all four. Pick the one you already pay for.

- **Perplexity Pro ($20/month).** What I use. Strong Deep Research mode, clean citations, easy Markdown export.
- **ChatGPT Deep Research.** Comparable output. Same prompt patterns work. Slightly different formatting on the report.
- **Gemini Deep Research.** Comparable output. Tends to be more verbose in synthesis. Same prompt patterns work.
- **Claude's own research mode (included with Claude Pro or Max).** Comparable output, integrated with the Cowork session. Lowest-friction option if you want everything in one tool. The tradeoff is the context-pollution problem mentioned just above: research findings can blur the focus of the drafting conversation. If you use this mode, save the output as a Markdown file in the project folder immediately and clear the research findings from the working context before continuing.

**No paid Deep Research subscription? Build your own with the RLM-inspired workflow.** If you do not pay for any Deep Research tool and you do not want to add another subscription, you can simulate Deep Research inside a regular Claude conversation by following a Recursive Language Model (RLM) inspired workflow guide I wrote earlier: [A Practical RLM-Inspired Workflow for Deep Research with AI](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/A%20Practical%20RLM-Inspired%20Workflow%20for%20Deep%20Research%20with%20AI.md). One note up front: this workflow is RLM-inspired, not true RLM. Download that guide, feed it into Claude, and you can build a skill or project folder that does a respectable job of approximating Perplexity-style Deep Research inside a normal Claude thread. It will not match a dedicated Deep Research tool one-to-one, and it will burn through tokens noticeably faster than a quick chat, but for most job applications it is good enough to do the work.

Pick a tool, learn the prompt patterns, and move on. The compounding leverage is in the prompt patterns and the discipline of running them on every application, not in which specific tool returns the results.

---

# The Prompt Patterns Claude Writes for You

The point of asking Claude to write the research prompts (instead of writing them yourself) is consistency. Claude pulls the company name, the role title, and the function out of the Job Description and inserts them into a prompt template tuned for senior application research. Every prompt asks the same kinds of questions in the same structure, so you can compare research across applications and across weeks.

A trigger phrase that works: "Write me three Perplexity research prompts for this company." Claude returns three prompts, ready to paste, one for each angle. Below are the canonical patterns Claude uses for senior product, engineering, or marketing roles. You can ask Claude to adjust the patterns for your function if your roles target different signals.

**Pattern 1: The company prompt.**

```
Conduct deep research on [Company Name] for someone considering a senior 
[Function] role. Cover:

1. Business model and revenue model. How does the company make money?
2. Recent financial signals: any reported revenue, ARR, valuation, or 
   funding rounds in the last 18 months. Cite each.
3. Known layoffs, hiring freezes, or reductions in force (RIFs) in the 
   last 12 months. Cite news sources.
4. Leadership turnover at the C-suite and Vice President (VP) level in 
   the last 24 months. Names, tenures, and departure reasons if public.
5. Public statements from the CEO in the last 12 months, including 
   earnings calls, podcasts, or shareholder letters. Tone and themes.
6. Any major product missteps, security incidents, or regulatory issues 
   in the last 24 months.
7. Anything else that would be a flag for a senior incoming hire.

Cite sources for every claim. Return as a Markdown report with clear 
section headers.
```

**Pattern 2: The team prompt.**

```
[Company Name] has a team that owns [Function from JD]. For an incoming 
senior hire considering this role, find:

1. Who runs that team. Name, title, tenure at the company, prior companies.
2. What the team has shipped publicly in the last 24 months. Product 
   announcements, blog posts, conference talks, podcast appearances.
3. Any team-member GitHub or open-source presence indicating technical 
   posture and the team's technology stack.
4. Any visible team-culture signals from Glassdoor, Blind, Reddit, or 
   LinkedIn posts written by current or former team members.
5. Any signals of team-level dysfunction: rapid turnover at the 
   individual contributor (IC) or manager level, repeated reorganizations, 
   public complaints from former team members.

Cite sources for every claim. Flag anything that looks like a 
team-health red flag.
```

**Pattern 3: The role context prompt.**

```
The role I am considering at [Company Name] is [Job Title from JD]. 
Find:

1. Is this a backfill or a new role? Pull the LinkedIn job listing date 
   and any history of the same role being posted there in the last 
   24 months.
2. What does the typical tenure look like for this role at this company? 
   Look for past holders on LinkedIn and their move-on dates.
3. What are people in similar roles at peer companies saying publicly 
   about the role's scope, expectations, and challenges?
4. Are there any indicators that this role specifically has had high 
   churn at this company (multiple short-tenure incumbents, repeated 
   re-postings, public complaints)?
5. What does compensation for this level at this company look like, 
   based on Levels.fyi, Glassdoor, Blind, or similar public data?

Cite sources for every claim. Flag anything that suggests this is a 
"churn seat" the company struggles to retain.
```

You paste each prompt into Perplexity Deep Research, wait the few minutes, and save each output as a Markdown file in the project folder (for example, `Research Company.md`, `Research Team.md`, `Research Role Context.md`). You now have three structured reports with citations, organized by the angles that actually matter for an application decision.

---

# The Three Research Angles, Read in Detail

What you do with the three reports matters as much as how you generated them. Here is how to read each one.

## Angle 1: The Company

You are looking for stability and credibility signals. The questions you are actually answering: is this company going to be here in a year? Is the leadership pattern healthy? Are there any incoming-hire red flags I should know before I invest an hour?

Read the financial signals section first. If the company has not raised in twenty-four months and the most recent reported revenue was flat, that is a flag. Not a "do not apply" flag, but a flag that informs how you frame the application. Read the leadership turnover section second. A new CEO in the last twelve months at a private company is a normal signal. Three CEOs in twenty-four months at a private company is a different signal. Read the news section third. A security incident, a major product issue, or a regulatory action you did not know about changes the application math.

What you are not looking for at this angle: the perfect company. No company is the perfect company. You are looking for whether the imperfections you find are within your tolerance.

## Angle 2: The Team

You are looking for cultural and technical fit signals. The questions you are actually answering: would I survive on this team for two years? Does this team ship the kind of work I want to do? Is the leader of this team someone I would want to report into?

Read the team leader section first. Length of tenure, prior companies, and public statements tell you most of what you need to know. A team leader who is twelve months into the role, who came from a peer company you respect, and who has made one or two thoughtful public statements about the work is a strong signal. A team leader who has been in seat for sixteen months and has cycled through three teams at this company is a different signal.

Read the shipped work section second. What the team has actually put into the world in the last twenty-four months is your strongest signal of what your day-to-day would look like. Lots of polished shipped work means a team that gets things across the finish line. Lots of strategy talks but no shipped products means a team that does a lot of preparation and not much delivery.

Read the culture signals section last. Glassdoor and Blind reviews are noisy. Read them for patterns, not individual reviews. Three reviewers saying "leadership does not listen" over twelve months is a pattern. One reviewer saying it is noise.

## Angle 3: The Role Context

You are looking for "churn seat" signals. The questions you are actually answering: how long do people last in this seat? Why have they left? Is the scope of the role honest about what is actually expected?

Read the tenure section first. If the median tenure for the role at this company is fourteen months, that is a red flag. Senior roles should run two to four years in healthy companies. Less than two years systematically is a sign that something about the seat is broken: scope creep, no real authority, unrealistic targets, or a manager problem.

Read the re-posting section second. If the same role has been posted three times in twenty-four months, the company is struggling to retain in this seat. The reason could be benign (the role keeps growing and needs a different shape) or it could be malignant (the seat is set up to fail). Either way you want to know before you apply.

Read the compensation section last. Compensation drift is a powerful late-stage signal. If Levels.fyi shows the role's compensation band has not moved in three years while peer companies have raised theirs, the company is falling behind on retention. Apply if the role still appeals, but go in with eyes open about why incumbents may be leaving.

---

# Red Flag Detection

Below is a short library of the most common red flags the three research prompts surface. Each is followed by the recommended action: walk away, apply with adjustments, or proceed normally.

**Recent reductions in force at the function you are joining.** Action: do not apply unless the company has publicly committed to backfilling and the role you are targeting is part of that backfill. Joining a team that just shed thirty percent of its headcount means you inherit the surviving team's trauma and the workload that was distributed across the people who left.

**CEO turnover in the last six months.** Action: apply, but probe in the interview. New CEOs reshape priorities. The role you are interviewing for may not be the role you are doing six months in. Ask about the new CEO's strategic priorities and how the function you are joining aligns.

**Median role tenure under two years for senior seats.** Action: apply with eyes open. Ask in the interview about why the role has had multiple incumbents in a short window. The honest answers are useful. The evasive answers are even more useful.

**No shipped product or public output from the target team in the last twelve months.** Action: apply, but adjust your framing in the cover letter. Position yourself as the person who ships, not the person who strategizes. The team likely needs more execution muscle.

**Compensation band has not moved in three years.** Action: apply if the role still appeals at the current band, but be prepared for compensation negotiations to be hard. Have a clear walk-away number before the first conversation.

**Recent security incident or regulatory action.** Action: walk away unless the role you are targeting is specifically related to fixing the problem. Joining a company in the middle of remediation as a non-remediation hire is exhausting and limits your ability to do the role you signed up for.

**Public CEO statements that are tonally off (defensive, dismissive of customer concerns, hostile to former employees).** Action: walk away. The tone at the top sets the cultural ceiling. You cannot out-perform that ceiling no matter how good you are.

**Repeated reorganizations.** Action: apply with low confidence in the org chart you read about. Every reorg costs the function six months of productivity. Three reorgs in twenty-four months means the function has been in setup mode for the entire window.

The pattern across all of these: research is most useful for the "walk away" decision. The strong applies are usually clear from the Job Description plus your Brain Trust. The marginal applies are where the research either confirms the apply or tips the decision to walk.

---

# When to Walk Away Before You Apply

This is the highest-value decision the research step makes. The point of automating tailoring is not to apply to more bad jobs faster. It is to free up your judgment for the right ones. Walking away from a marginal application is not failure; it is the system working.

The walk-away criteria, in order of importance:

1. The Chief Executive Officer (CEO) or hiring manager has signaled values incompatible with how you want to work.
2. The role has shown clear churn-seat patterns (median tenure under eighteen months, three or more re-postings in the last two years).
3. The team has not shipped anything in the last twelve months and the Job Description does not acknowledge this honestly.
4. The company is in active remediation from a major incident and you are not being hired to fix the remediation.
5. The compensation band is materially below what you need and you have evidence the company will not move on it.

If any one of these is true, walk away. The hour you save goes into the next application. Over fifty applications, the discipline of walking away on the marginal ones is what raises the quality of your overall job search. You will send fewer applications and land more interviews, because the applications you do send are to companies where the research came back clean.

The application math is asymmetric. A wrong "apply" costs you an hour now and potentially a bad job for two years later. A wrong "walk away" costs you almost nothing because there are more roles. Make decisions with that asymmetry in mind.

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

If you use or adapt this deep dive, please include:

Based on "External Research with Perplexity (and Others)," part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
