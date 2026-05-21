>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market

---

# Why I Built This

The 2026 job market is brutal. A Director-level Product Manager (PM) role on LinkedIn pulls 200 to 800 applicants in the first week. Senior individual-contributor PM roles are often worse. The pool is bigger, the gates are tighter, and the screen-out time per applicant is shorter than it has ever been.

Generic resumes do not land. I know firsthand, because I sent them for months. I had a perfectly good base resume, friends who read it and liked it, and a steady drip of "thank you for applying, we have moved on with other candidates." A friend who had been through it told me the only thing that worked for him was hyper-tailoring each application to the company and the role. Read the Job Description (JD) line by line. Map his experience to it word for word. Rewrite the cover letter for the specific team. Polish until every bullet earned its place.

He was right. Tailored applications got phone screens. The math was just ugly. Four hours per application to do it well. If I treated this like a job, I could send three a week. Three a week, in a market where good roles get pulled inside 14 days because they have already filled the funnel ten times over.

I am a Lead PM at the intersection of Payments, Fraud, and Artificial Intelligence and Machine Learning (AI/ML). I build platforms for a living. So I built one for the application problem. The premise was simple: if hyper-tailoring works, automate the parts that are tedious and keep the parts that need my judgment. Use Claude as a tireless thought partner. Hold every framing, metric, and cover-letter hook I have ever written in a structured source of truth so the AI is pulling from my actual experience, not its training data. Make every application sharper than the last by closing the loop after I hit send.

What I ended up with cuts the time from four hours to about twenty minutes per application. The output is better than what I produced by hand. I am sending more applications, of higher quality, with less fatigue. And the system gets sharper every time I use it, because the lessons from yesterday's application are baked into the source of truth before today's draft starts.

This guide is the whole thing. Free. Open source. Creative Commons Attribution 4.0 (CC BY 4.0). You can take it, fork it, rename anything, plug in your own experience, and ship.

---

# Why This Works

Three things make this work where one-shot AI prompts fail.

**Structured source of truth (Career Brain Trust).** The AI is not guessing about your experience. It is pulling from a structured folder you control: your roles, your metrics, your reusable phrasings, your past cover letters by archetype. When you tell it to tailor for a Director of Product Payments role, it reads the Job Description, scans your folder's INDEX file for tag matches, and selectively loads only the roles and archetypes that fit. No hallucinated experience. No generic filler. The bullets are yours.

**Persistent memory across applications.** Every application teaches the system something. A new metric you used. A framing that landed better than the canonical version. A cover-letter hook for a company archetype you had not encountered before. After you hit send, a second skill (`update-brain-trust`) folds the application back into your source of truth. The next application starts smarter. Over fifty applications, the compounding is enormous.

**Human in the middle.** This is not "AI writes your resume." This is "AI drafts, you push back, you both iterate, you ship." Claude catches what you miss (a tag, a keyword, a framing you forgot you had). You catch what Claude misses (a phrasing you would never use, a metric that needs context, a tone that does not match the company). The conversation is the magic. Both of you working together produce something neither would alone.

There is also a body of research that backs why this loop works. In-context learning behaves like Bayesian inference: every piece of structured context narrows the model's distribution over what you actually want. Multi-turn AI conversations degrade by roughly 39 percent on average because models make wrong assumptions early and do not recover. Structured clarifying questions before generation can boost output quality by about 20 percentage points on ambiguous tasks. If you want the deeper version of that argument with citations, my companion guide on the [Context Prompt pattern](./References/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md) lays it out. I will name the pattern again when we get to Step 7, because it is the engine behind the back-and-forth that produces the final draft.

---

# How This Compares to What You Might Already Use

**vs. resume builders (Resume.io, Zety, Novoresume):**
These optimize formatting and Applicant Tracking System (ATS) parseability. They do not tailor content. Their templates produce resumes that look like resumes. They do not know your story, your metrics, your past phrasings, or the company you are applying to. You still have to write everything yourself. The output is a prettier version of your generic resume.

**vs. one-shot AI prompts (ChatGPT, Claude, Gemini, used as standalone tools):**
These can draft well, but they have no memory across applications and no source of truth about you. They will hallucinate metrics, invent jobs you did not hold, and recycle the same generic framings every time. You start every conversation from zero. By the tenth application, you are tired of typing the same context paragraph at the top of every prompt, so you stop, and the quality drops.

**vs. manual hyper-tailoring (4 hours per application):**
This is the gold standard for quality, and the workflow this guide automates. The output of manual tailoring is excellent. The problem is throughput. Four hours per application means you ship three a week if it is your full-time focus, and one a week if you are also working. In a market where the best roles are gone in two weeks, three a week is not enough.

**vs. paying a resume writer ($500 to $2,000 per resume):**
The good ones write well. None of them know you the way you know you. None of them are going to do hyper-tailored versions for every JD you find. The turnaround is usually a week. The output is one polished version. You are back to spraying.

**A note on tools:** This guide is written for Claude inside the desktop app's Cowork mode because that is what I use. The underlying pattern (a structured source of truth, persistent memory, skills wrapped around repeating workflows, human-in-the-middle iteration) is not locked to Claude. You could likely adapt it to other frontier models that support file-system access and reusable skill or prompt patterns. I am writing what I know and what I have tested. Adapt as you see fit.

---

# When and How to Use This

The system handles anything in the orbit of a job application. Here are real scenarios:

**You found a role you want to apply to.**
Open a new project folder for the company and role. Start a new thread in Cowork. Paste or capture the JD. Trigger the `resume-builder` skill. Twenty minutes later you have a tailored combined cover letter and resume as a single Word document. You open it in Google Docs (or Microsoft Word), polish the last ten percent, export to PDF (Portable Document Format), and send.

**You got rejected and want to learn from the application.**
Trigger the `update-brain-trust` skill at the end of the thread, before you close it. The skill folds new framings, metrics, and cover-letter hooks back into your source of truth, logs the application, and saves copies of the resume and cover letter to a "Past Resumes" folder so future-you can search what you sent to whom.

**You are prepping for an interview at one of these companies.**
The brain trust is already loaded with the framings you used for that company's application. Open a new thread, point it at the brain trust folder, and ask Claude to generate prep notes for the specific role. The same source of truth that drafted the resume now drafts your prep.

**You are researching whether to apply at all.**
Do the external research step (Step 8 below) before the tailoring. If the company has visible red flags (recent layoffs you did not know about, a culture pattern you would not survive, executive turnover six months in a row), you walk away and reinvest the hour somewhere worthwhile. The point of automating tailoring is not to apply to more bad jobs faster. It is to free up your judgment for the right ones.

---

# What This System Actually Does

The workflow is a loop. Every component feeds the next, and the system cycles continuously with every application:

```
Career Brain Trust (your structured source of truth)
  --> Capture JD (copy-paste or Chrome plugin)
    --> Run resume-builder skill (Claude drafts and collaborates with you)
      --> External research (Perplexity Deep Research)
        --> Polish in Google Docs (human in the middle)
          --> Export PDF and send
            --> Run update-brain-trust skill (close the loop)
              --> back to Career Brain Trust (now sharper)
```

**Career Brain Trust** is a structured folder that holds your experience: an INDEX file at the top, a per-role child file for each job you have held, per-archetype cover-letter files (banking, startup, big tech, AI, crypto, whatever you target), a skills inventory, an achievements file, and an identity file with your headline and a library of positioning statements tagged by angle. This is the source of truth. Everything else pulls from it.

**Capture JD** is how the Job Description gets into the workflow. Copy and paste is universal and works everywhere. The Claude in Chrome extension is a faster upgrade once you trust the consent model.

**Run resume-builder skill** is the main event. The skill reads the INDEX, selects matching role files and cover-letter archetypes by JD tag, produces a first draft of the combined cover and resume, then asks you the right clarifying questions to refine it.

**External research** is Perplexity Pro (with Deep Research mode) doing company and team context outside the main session. You bring the findings back. You decide if the company is still worth your hour.

**Polish in Google Docs** is the last ten percent. AI does ninety percent of the work. You do the part it cannot.

**Export PDF and send.** Self-explanatory.

**Run update-brain-trust skill** closes the loop. Folds the new framings back in, logs the application, archives the files.

The loop never stops. Every time you apply, the system gets sharper.

---

# What You'll Need

| Item | Cost | Required? |
|------|------|-----------|
| Claude Desktop app (with Cowork mode) | Free with Claude subscription | Yes |
| Claude Pro or Max subscription | Subscription | Yes |
| Google Docs (or Microsoft Word desktop) | Free for Google Docs | Yes |
| Perplexity Pro (for Deep Research mode) | $20/month | Recommended |
| Claude in Chrome extension | Free with Claude subscription | Optional |
| The `resume-builder` skill (downloadable) | Free | Yes |
| The `update-brain-trust` skill (downloadable) | Free | Yes |
| Career Brain Trust template (downloadable) | Free | Yes |

**Total recurring cost beyond your Claude subscription:** $20/month for Perplexity Pro. You can skip Perplexity entirely and use ChatGPT Deep Research or Gemini Deep Research instead; the prompt patterns transfer cleanly.

**Technical comfort level:** You do not need to be a developer. If you can install a desktop app, download a folder, and follow step-by-step instructions, you can build this. The hardest part is sitting with the brain trust setup once at the beginning. After that, every application is a 20-minute conversation.

**Time investment:** Plan for one afternoon to install the apps, download the skills, and set up your Career Brain Trust (Steps 1 through 5). After that, each application is roughly 20 minutes of focused work end to end.

---

# The Steps

---

## Step 1: Set Up Your Project Folder

**Why this matters:** One thread per job application keeps the context clean. Mixing four applications into one thread pollutes the AI's working memory and produces worse drafts. Creating the project folder in an easy-to-find location BEFORE you open Cowork means Cowork can be pointed at it on day one. This is a small setup detail that saves you hours over the year.

**What to do:**

1. Pick a parent folder somewhere easy to find. Something like `Project - Job Search/` works.
2. For every new application, create a child folder using this format: `[Company Name] - [Role Title]`. Example: `Acme Fintech - Director of Product Payments`.
3. Keep filenames consistent: spaces (not underscores), title case, no special characters.
4. The folder will hold the JD, the tailored Word document, the cover letter (if separate), the Perplexity research notes, and any company-specific intel you collect.

---

## Step 2: Set Up Claude Desktop and Cowork

**Why this matters:** Cowork is the mode in Claude's desktop app that gives Claude read and write access to a folder on your computer. Without it, Claude has no way to read your JD, write the Word document, or save the cover letter where you want it. You install once, then connect Cowork to a different project folder per application.

**What to do:**

1. Download and install the [Claude Desktop app](https://claude.ai/download).
2. Open it and switch to Cowork mode.
3. Create a new Cowork project. Point it at the project folder you created in Step 1.
4. Verify it can see the folder by asking Claude to list the files in it.

From here on, every application starts with a new Cowork project pointed at a new project folder.

---

## Step 3: Configure Persistent Memory

**Why this matters:** Without persistent memory, every thread starts from zero. You spend the first ten minutes of every application re-telling Claude who you are, what roles you target, what industries you avoid, what your style preferences are. With memory configured, all of that loads automatically. This is the difference between an assistant who knows you and one who is meeting you every day for the first time.

**What to do:**

1. Create a `CLAUDE.md` file at the root of your Cowork-mounted folder. This is the "operating constitution" Claude reads first in every thread. Include:
   - Who you are (one or two sentences)
   - What roles you target
   - Industries or companies you avoid
   - Your locked formatting and style preferences (for example: no em dashes, define acronyms on first use, multi-choice clarifying questions only)
2. Turn on Claude's auto-memory feature in the desktop app. This persists facts, preferences, and project context across threads automatically.
3. Save a few seed memories explicitly. Example: "I target Director and Head of PM roles in Payments, Fraud, and AI/ML. I prefer structured multi-choice clarifying questions with a copy-paste answer sheet."

The minimum above is enough for the resume workflow to operate well. If you want the deeper version (operating modes, session protocols, scheduled-task patterns), my [Cyberbrain guide](https://github.com/VeritasPlaybook/playbook) covers the full setup.

---

## Step 4: Build Your Career Brain Trust

**Why this matters:** This is the source of truth. Everything else pulls from it. Without a structured brain trust, the AI is guessing about your experience. With one, every application becomes a curation problem rather than a writing problem. You are not generating bullets from scratch. You are selecting and refining from a library of bullets, framings, and hooks you already wrote.

**What to do:**

The Career Brain Trust is a folder with this structure:

```
Brain Trust/
|
|-- INDEX.md                          # File map with tags per child file
|-- 0 How To Use.md                   # Tag glossary, acronyms, instructions
|-- 1 Identity.md                     # Headline, summary, positioning library
|-- 2 Chronology.md                   # Master dates and titles
|-- 5 Skills.md                       # Aggregated skill inventory
|-- 6 Achievements.md                 # Big numbers by employer
|-- 7 Education.md                    # Credentials and awards
|
|-- Experience/                       # One file per role
|   |-- 3.1 Most Recent Role.md
|   |-- 3.2 Second Most Recent Role.md
|   |-- 3.3 Third Most Recent Role.md
|
|-- Cover Letters/                    # One file per archetype
|   |-- 4.0 Patterns.md               # House-style cover letter skeleton
|   |-- 4.1 Banking Archetype.md
|   |-- 4.2 Startup Archetype.md
|   |-- 4.20 Reusable Hooks.md        # Modular building blocks
```

The INDEX is the navigation file. It has a table for every child file, with a Tags column. When the `resume-builder` skill runs, it reads the INDEX first, scans the JD for matching tags, then selectively loads only the three or four role files and one to three cover-letter archetypes that fit. This is what keeps the AI tool below context-window truncation limits, and what makes the load fast.

Three ways to build yours:

- **Empty template:** download the template, open the files, fill them in by hand. Slowest but most deliberate.
- **Setup prompt:** download the setup prompt, paste it into a fresh Claude thread, answer the interview questions, and Claude builds your brain trust by interview. Fastest path to a usable v1.
- **Example filled versions:** look at the three example Brain Trusts (a PM, an engineer, a marketer) for what a complete one looks like before you start. Useful as a reference even if you build from scratch.

All three are linked in the Deep Dives table at the end of this guide.

> **[Deep Dive: The Career Brain Trust, Structure and Why It Works](./Deep%20Dives/01%20-%20The%20Career%20Brain%20Trust%20Structure.md)**

---

## Step 5: Install the Skills

**Why this matters:** A skill is a reusable workflow Cowork can trigger. Instead of pasting a long prompt every time, you trigger the skill by phrase ("let us apply to Acme Fintech") and Cowork runs the whole multi-step workflow. Two skills power this guide's workflow: `resume-builder` (tailoring) and `update-brain-trust` (closing the loop). Both are free downloads.

**What to do:**

1. Download the two skill packages from the [GitHub repository](https://github.com/VeritasPlaybook/playbook) (linked in the Deep Dives table).
2. Install them in Cowork. Each skill is a folder containing a `SKILL.md` file with the workflow definition and any helper scripts. Cowork picks up the skill automatically once it is placed in the skills directory.
3. Verify the install by triggering each skill. A trigger phrase for `resume-builder` is something like "build a resume for Acme Fintech." A trigger phrase for `update-brain-trust` is "update the brain trust" or "log this application."

Full install steps with screenshots are in the deep dive.

> **[Deep Dive: Skill Installation Guide for Cowork](./Deep%20Dives/06%20-%20Skill%20Installation%20Guide%20for%20Cowork.md)**

---

## Step 6: Capture the Job Description

**Why this matters:** Every application starts with the Job Description (JD). Garbage in, garbage out: a partial or messy JD produces a partial or messy draft. The Job Description is the single most important input. How you capture it matters less than capturing it cleanly and completely.

**What to do:**

**Primary method:** copy and paste the JD from the company's careers page into a file named `Job Description.md` inside your project folder. This works everywhere, requires no setup, and gives you a clean text record you control.

**Recommended upgrade:** use the Claude in Chrome extension to capture the JD directly from the careers page. The extension can read the rendered page (JavaScript and all) and feed it into the Cowork thread without you having to manually paste. It is faster, and it captures formatting and links that the paste method sometimes strips.

**A note on Chrome plugin privacy:** the Claude in Chrome extension asks for permission per site, the first time you use it on each domain. You approve a site for one session or for always, and you can revoke at any time. You can deny it on sites you do not want it to touch. This is the same consent model as a normal Chrome extension. If you are still uncomfortable, the copy-paste method works for every JD and gives you the same end result with two extra clicks. Use what fits your comfort level.

---

## Step 7: Run the Resume-Builder Skill (Tailor and Collaborate)

**Why this matters:** This is where the actual tailoring happens, and where most people get the workflow wrong. The skill produces a first draft. The first draft is the starting point of the conversation, not the end of it. The magic is in the back-and-forth that follows: pushing back on phrasings, asking for alternatives, swapping a tone for the company archetype, swapping a metric for a stronger one. Treat the first draft as a proposal, not a result.

**What to do:**

1. Trigger the skill with a phrase like "let us apply to Acme Fintech for the Director of Product Payments role." Point it at the JD file from Step 6.
2. The skill reads the INDEX, selects matching role files and cover-letter archetypes, and produces a first draft of the combined cover letter and resume as a Word document in your project folder.
3. Open the draft. Read it as a human. Now the real work starts.
4. **Push back.** "I would never phrase it that way." "That metric needs context." "The tone is too formal for a startup like this one." Tell Claude what to change and why.
5. **Ask for alternatives.** "Give me three different framings of the second bullet." "Show me a punchier version of the opener." Pick the strongest, or merge two.
6. **Match the company archetype.** A banking application is formal and credentialed. A startup application is direct and punchy. A big-tech application is crisp and metrics-heavy. Tell Claude the archetype explicitly and ask it to rewrite to match.
7. Iterate until both of you agree the application is sharp. You will know when it is done. There is a moment where you read the draft and there is nothing left to change.

The reason this back-and-forth works as well as it does is the multi-choice clarifying-question pattern the skill uses to ask you the right things in the right format. That pattern is the engine behind the whole workflow. I wrote a full companion guide on it: ["The Context Prompt That Will Revolutionize Your Workflow"](./References/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md). If you want to understand why structured clarifying questions with copy-paste answer sheets beat free-form prompts every time, read it once. You will use the pattern across every other AI workflow you build, not just job applications.

**A short example of what good looks like.** A lightly anonymized snippet from a tailored application to a regulated fintech for a Director of Product role:

> *Cover opener:* "If you are looking for a Director of Product who has built zero-to-one machine-learning fraud platforms in regulated North American markets, owned the vendor stack end to end, and shipped through Engineering, Data Science, Compliance, and Legal in parallel, I am your guy."
>
> *Resume bullets (top of current role):*
> - Built a real-time, ML-powered fraud detection platform from 0 to 1, processing millions of transactions across regulated markets, anchored in supervised ML for live risk scoring at scale.
> - Implemented multi-acquirer payment orchestration with dynamic routing and automatic failover, materially improving acceptance and lowering cost per transaction.
> - Shipped an internal AI orchestration platform unifying communications, meeting intelligence, tasks, and organizational knowledge across existing data infrastructure.
> - Drove fraud rates well below industry benchmarks within 90 days through layered ML, 3D Secure 2.0, Account Name Inquiry, and rules optimization.

Every one of those bullets traces back to a canonical bullet in the Brain Trust, lightly rephrased for this specific JD. None of them were invented by Claude. None of them are filler. That is the bar.

> **[Deep Dive: The Resume-Builder Skill Workflow Walkthrough](./Deep%20Dives/02%20-%20The%20Resume-Builder%20Skill%20Workflow.md)**

---

## Step 8: External Company Research

**Why this matters:** The resume-builder thread holds your tailored application. External research is a different job and belongs in a different tool. Mixing them pollutes the main session's context with company facts you do not need in working memory, and the research tool you want for this (Perplexity, with its citations and live web access) is built for exactly that. The research also tells you whether to apply at all. Half the time, the most valuable output of this step is a "do not apply" decision that saves an hour.

**What to do:**

1. In the main Cowork thread, ask Claude to write you three Perplexity research prompts for this company.
2. Open [Perplexity Pro](https://www.perplexity.ai/) (or whatever Deep Research tool you use).
3. Paste the prompts. Use Deep Research mode for thorough investigation; regular mode is fine for quick sniffs.
4. Cover three angles:
   - **The company:** business model, recent news, financial signals, layoffs in the last 12 months, leadership turnover, public posture.
   - **The team:** what the role's likely team owns, what good looks like at similar companies, any team-specific signals from blog posts, podcasts, or conference talks.
   - **The role context:** is this a backfill or a new role, is the company hiring across the function or just this seat, what are common patterns at similar-stage companies in the same vertical.
5. Bring the findings back into the main Cowork thread. Save the markdown research output as a file in the project folder.
6. **Decide.** Is this company actually worth your hour? Any red flags? Cultural fit? If yes, refine the draft using the new context (echo back a mission phrase, reference a recent product move, soften or sharpen tone). If no, walk away.

**Alternative tools:** Perplexity is what I use. ChatGPT Deep Research, Gemini Deep Research, and Claude's own research mode all produce comparable output. The prompt patterns transfer cleanly. Pick the one you already pay for.

> **[Deep Dive: External Research with Perplexity (and Others)](./Deep%20Dives/04%20-%20External%20Research%20with%20Perplexity.md)**

---

## Step 9: Polish in Google Docs and Export PDF

**Why this matters:** The last ten percent of polish is human work. Claude can build the Word document and can build the PDF directly, but a human reading the document in Google Docs catches things Claude does not: a phrasing you would never use out loud, a spacing artifact, a line break in an awkward place, a date that needs a comma, a sentence that should be split. Skipping this step is the single most common way otherwise-great applications go out with avoidable rough edges.

**What to do:**

1. Open the Word document from your project folder. Upload it to Google Docs (or open it in Microsoft Word desktop if you prefer).
2. Fine-tune formatting: line breaks, spacing, font weight on the title block, page margins. Cover letter sits on page 1; resume runs page 2 and beyond. Aim for two pages total.
3. Read it out loud. Does it sound like you? Are there phrases the AI introduced that you would never use? Anything that reads stilted? Rewrite.
4. Check the cover letter opener. The first sentence has to land. Read it three times.
5. Spot-check every metric against your Brain Trust. Numbers must be canonical.
6. Export to PDF. Use the company's preferred filename pattern if specified, otherwise a clean `[Your Name] - [Role Title].pdf`.
7. Send.

> **[Deep Dive: Cover Letter and CV Format, What I Recommend and Why](./Deep%20Dives/05%20-%20Cover%20Letter%20and%20CV%20Format.md)**

---

## Step 10: Run the Update Brain Trust Skill (Close the Loop)

**Why this matters:** Without this step, you start every application from the same place you started yesterday's. The framings you discovered for last week's application are stuck in last week's thread. The new metric you used does not propagate. The cover-letter hook for the company archetype you had never written for before is gone the moment you close the tab. Closing the loop is what makes the next application start smarter than the last.

**What to do:**

1. Before you close the thread, trigger the `update-brain-trust` skill ("update the brain trust" or "log this application").
2. The skill will:
   - Pull the resume, cover letter, and Job Description (JD) from the thread.
   - Diff the tailored content against your Brain Trust's existing canonical and variant framings.
   - Ask you (in multi-choice format) which new variants to ingest, which canonical conflicts to resolve, and how to file the cover letter (new archetype or variant of an existing one).
   - Apply only the additive changes you approved, refresh the INDEX timestamp, and log the application to your application log with metadata you can search later.
3. Confirm the summary. Close the thread.

Over fifty applications, the brain trust accumulates: dozens of new variant framings per role, new big-number metrics, new cover-letter archetypes, new reusable hooks. The fiftieth application takes the same twenty minutes as the first, but the draft quality is dramatically higher because the system is pulling from a much richer source of truth.

> **[Deep Dive: The Update Brain Trust Loop, Why the Loop Matters](./Deep%20Dives/03%20-%20The%20Update%20Brain%20Trust%20Loop.md)**

---

# The Full Loop

Once all ten steps are in place, the system runs as a continuous cycle:

```
Career Brain Trust (your structured source of truth)
  --> Capture JD (copy-paste or Chrome plugin)
    --> Run resume-builder skill (Claude drafts and collaborates with you)
      --> External research (Perplexity Deep Research)
        --> Polish in Google Docs (human in the middle)
          --> Export PDF and send
            --> Run update-brain-trust skill (close the loop)
              --> back to Career Brain Trust (now sharper)
```

The first application takes a couple of hours because you are also setting up the brain trust. Every application after that is roughly twenty minutes. Each one feeds the next. Nothing exists in isolation, and the system is only as good as the weakest link in the chain, which is why the structure of the brain trust matters as much as the tailoring step itself.

---

# What I Learned

These are the lessons that compounded across many applications. The fuller version of each, with examples from real applications, lives in [Deep Dive 7](./Deep%20Dives/07%20-%20What%20I%20Learned%20Expanded.md).

**Pushback is a feature, not friction.** The AI that always agrees with you produces mediocre output. Challenge the first draft. Ask for three alternatives. Reject any phrasing you would not say out loud. The strongest applications I have ever sent were the ones where I argued with Claude the most.

**Lock decisions explicitly.** When something works, say "lock that in." When something fails, say "never do that again." Memory turns one-time corrections into permanent rules. The result over time is that the system stops repeating the same mistakes you have already corrected.

**Build skills, not prompts.** A prompt is a one-shot you have to remember to use. A skill is a reusable workflow that triggers itself when you say the right phrase. Anything you do more than twice should become a skill. The leverage compounds: you build the skill once and use it for years.

**Close the loop or you start from zero every time.** The `update-brain-trust` skill is what separates this workflow from "I used an AI chatbot to write a resume." A new framing you discovered for last week's application is no good to you if it does not get folded back into the source of truth. The loop is the system.

**Hard guard rules prevent the same mistake twice.** Some lessons are so important they belong as explicit rules the AI must follow on every run. "Never include any role that predates the relevant career pivot." "Never mention this specific past advisory engagement on this specific company's applications." "Never include a Summary section in the resume." Encode them once. Stop relearning them.

**Validate in human-readable form before shipping.** Never send the AI's first draft. The Google Docs polish step is non-negotiable. Reading a document in a document editor (not in a chat window) catches things you cannot catch any other way. The format is the readership.

**External research belongs outside the main session.** A different job needs a different tool. Perplexity is built for live research with citations. Keeping it out of the main Cowork thread keeps the main thread's context focused on tailoring, and lets Perplexity do what it is best at.

**Memory is the moat.** Without persistent memory, every conversation starts at zero and every conversation ends at zero. With memory configured, every conversation starts where the last one ended. This is the difference between a tool and a collaborator. Set up memory first; you will thank yourself by week two.

**Boring and reliable beats fancy and fragile.** A simple Word template that ports cleanly to PDF beats a beautiful template that breaks on every export. A flat folder structure beats a deeply nested one. The workflow you can run while tired beats the workflow you have to think about.

**The structured-question pattern compounds.** Multi-choice clarifying questions with a copy-paste answer sheet are the most leveraged thing in this entire system. Once you bake the pattern into your global instructions, every project benefits, not just job applications. Research projects. Writing tasks. Strategic planning. The full pattern is in the companion guide linked in Step 7.

**Different tones for different companies.** Banking applications are formal and credentialed. Startup applications are direct and punchy. Big-tech applications are crisp and metrics-heavy. Same you, different framing. Tell the AI the archetype explicitly. Saying "banking-style cover" or "startup-style cover" produces dramatically different drafts because the AI is anchoring on a known pattern.

**The structure is the product.** The Career Brain Trust folder structure, the INDEX with tags, the per-role and per-archetype child files: this is the actual product. Without the structure, the AI is guessing. With it, the AI is curating. Spend time on the structure upfront; the dividend pays every application after.

**Collaboration beats automation.** The point of this system is not to automate your job search away. It is to amplify your judgment with a tireless partner. The strongest applications come from a back-and-forth conversation, not a one-shot prompt. The system is the scaffolding. You are still the writer.

---

# Deep Dives

These companion guides go deeper into the design, tradeoffs, and iteration stories behind each step:

| Guide | What It Covers |
|-------|----------------|
| [The Career Brain Trust, Structure and Why It Works](./Deep%20Dives/01%20-%20The%20Career%20Brain%20Trust%20Structure.md) | The folder structure, why we split from a monolithic file, how the INDEX drives selective reads, the three ways to build yours |
| [The Resume-Builder Skill Workflow Walkthrough](./Deep%20Dives/02%20-%20The%20Resume-Builder%20Skill%20Workflow.md) | The 11-step workflow inside the skill, how JD tag matching works, guard rules, common pitfalls, customization |
| [The Update Brain Trust Loop, Why the Loop Matters](./Deep%20Dives/03%20-%20The%20Update%20Brain%20Trust%20Loop.md) | The 3-phase ingestion workflow, contradiction resolution, the compound effect over 50 applications |
| [External Research with Perplexity (and Others)](./Deep%20Dives/04%20-%20External%20Research%20with%20Perplexity.md) | Why research stays out of the main session, prompt patterns, red-flag detection, alternative tools |
| [Cover Letter and CV Format, What I Recommend and Why](./Deep%20Dives/05%20-%20Cover%20Letter%20and%20CV%20Format.md) | The one-page-cover plus two-page-CV combined format, template structure, Google Docs polish checklist, PDF export, ATS considerations |
| [Skill Installation Guide for Cowork](./Deep%20Dives/06%20-%20Skill%20Installation%20Guide%20for%20Cowork.md) | How Cowork skills work, install steps, verification, customization, common errors and fixes |
| [What I Learned (Expanded)](./Deep%20Dives/07%20-%20What%20I%20Learned%20Expanded.md) | Each of the 13 lessons expanded with examples from real applications, anonymized |

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

Based on "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0

## Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- LinkedIn: https://www.linkedin.com/in/malocilja/
- GitHub: https://github.com/VeritasPlaybook/playbook
- Investment Research: https://github.com/Veritas-Research/investment-research

*If you found this valuable, star the repo to help others find it.*
