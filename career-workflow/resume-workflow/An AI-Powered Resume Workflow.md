**Last Updated:** January 30, 2026  
**Version:** 1.0  
**License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) (Attribution required for reuse)  
**Author:** [VeritasPlaybook](https://github.com/VeritasPlaybook)

> **Disclaimer:** This guide describes a practical workflow using Perplexity Pro for research and Claude Sonnet 4.5 for writing. I don’t work for either company and don’t receive any benefit if you use these tools. This is simply the setup that has worked best in practice.
>
> **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

For Table of Contents, click outline button on the right ----------------------------------------------------------------------------------------------^

---
# 1. Who This Guide Is For

This guide is for people switching roles or repositioning themselves for stronger opportunities, who are willing to do honest self-reflection about their work.

You don't need to be "good with AI." You only need:
- Curiosity
- A willingness to document what you've actually done
- The ability to follow prompts and answer questions clearly

**The goal:** Build a resume that is deeply tailored to a specific role, optimized for ATS, and still authentic to you.

---
# 2. High-Level Workflow

You’ll move through five main steps:

1. Build a **Master Profile** document about yourself  
2. Research the **company and role** using Perplexity  
3. Choose or validate a **resume template** (ATS-first)  
4. Draft the **resume** with Claude using an expert-in-the-loop loop  
5. Test and **refine** using ATS checks and focused iterations  

Research into best practices shows this “research first → write later → then validate” pattern is more effective than just pasting a job description into an AI and asking for a resume.
## 2.1 Quick Start (If You're in a Hurry)

**Absolute minimum version:**

1. **Brain dump** your experience into a doc (30 min)
2. **Research** the company with Perplexity Deep Research (5 min)
3. **Paste both** into Claude with the prompt from Section 6.2 (5 min)
4. **Answer** Claude's questions (10 min)
5. **Review** first draft and iterate (20 min)

**Total time: ~70 minutes**

The full workflow adds depth and produces better results, but this gets you 80% of the way there.


---
# 3. Step 1 – Build Your Master Profile Document

## 3.1 What the Master Profile Is

Think of this as your private “master resume plus career log.” It is not meant to be sent to anyone. It’s the raw material you feed into AI so it can shape a targeted resume later.

Research on “master resumes” recommends capturing everything: all roles, projects, and achievements, not just the highlights you’d show on a 2‑page resume. If you did it, can measure or talk about your impact or achievements, write it all down. There is no such thing as too much at this point.

## 3.2 Suggested Structure

Create a markdown or doc (word/google docs) file with sections like:

1. About you (1–2 paragraphs)
    
2. Work history (every role, even if you won’t use all of them)
    
3. Key projects
    
4. Skills
    
5. Education and certifications
    
6. Awards, speaking, writing, open‑source, volunteer work
    

Within work history and projects, you’ll write bullet points using a simple achievement structure.

## 3.3 Use STAR to Write Better Achievements

A very effective way to describe what you’ve done is the STAR method:

- Situation – context or problem
    
- Task – what you were responsible for
    
- Action – what you actually did
    
- Result – what happened, ideally with numbers
    

You don’t have to spell out each word in the final bullet, but you should think through them.

Example transformation:

- Weak:  
    “Worked on payments platform at JP Morgan.”
    
- STAR‑informed:  
    “Led the design of a new payments API platform for ISV partners, coordinating with 4 internal teams to launch on time and support 3 enterprise clients in the first 6 months.”
    

Same story, but now a hiring manager can see scope, ownership, and impact.

> **Pro tip:** When you’re stuck, start by writing the full STAR in a sentence or two, then compress it into a single bullet once the idea is clear.

## 3.4 Simple Self-Guided Template

For each role, answer:

1. What was the context when you joined?  
    (Company stage, team size, key products, target customers.)
    
2. What were you hired to do?
    
3. What are 3–7 things you can honestly say you improved, shipped, fixed, or grew?
    
4. For each of those, what changed in numbers?  
    (Revenue, cost, time saved, NPS, adoption, throughput, risk reduced, etc.)
    

You can keep this quite long. A 5–10 page Master Profile is normal and often useful.

## 3.5 (Optional) Prompt to Help You Structure Achievements

If you find it easier to write everything down first without worrying about structure, start with a brain dump. Just open a doc and write out what you did at each job in your own words—messy bullets, run-on sentences, whatever comes to mind. Don't worry about making it sound good yet.

Once you have that raw material, you can copy and paste it into Claude Sonnet 4.5 to help you structure and tighten it into proper STAR-format bullets.

**Recommended Settings:** 
- Model: Claude Sonnet 4.5
- Reasoning/Thinking: ON (helps it think through structure and compression) 

**Prompt:**
```
You are helping me structure my achievements for a future resume.

Here is a raw dump of my experience for one role:

[PASTE YOUR BRAIN DUMP HERE - OR WRITE ANYTHING OUT ]

Tasks:
1. Rewrite my points into STAR-style bullet points (Situation, Task, Action, Result).
2. Keep each bullet to 1–2 lines.
3. Focus on measurable outcomes where possible.
4. Do NOT invent numbers. If you think a metric is missing, ask me a question instead of guessing.
5. Return the bullets in markdown list format only.
```

> **Pro tip:** If the AI gives you “too pretty” bullets that don’t feel like you, edit them back toward your natural voice. Authenticity matters later in interviews.


---
# 4. Step 2 – Research the Company and Role 

Now you’ll build a “Company & Role Dossier” that tells you what actually matters for this specific opportunity. I like to call this the "Perplexity Deep Research Mode"

Research on effective applications shows that strong candidates go beyond the job description and understand the company’s mission, recent moves, and competitive context.

## 4.1 What You Want to Learn

At minimum, aim to cover:

1. Company mission, values, and culture
    
2. Products, services, and target customers
    
3. Recent news (funding, launches, leadership changes, major partnerships)
    
4. Market and competitors
    
5. What “good” looks like in this role and industry
    
6. Role‑specific skills, tools, and success metrics
    

For some roles, you may also care about:

- Tech stack
    
- How product and engineering or other functions work together
    
- Geographic or regulatory context
    

# 4.2 Deep Research Prompt (Company & Role Dossier)

**Recommended Setup:**
- Create a dedicated Space in Perplexity for this application (optional but recommended for organization)
  - Useful if you're applying to multiple roles and want to keep research separate
  - Not required for a single application
- Use **Deep Research** (click the Deep Research button, not regular search)
- This will take 3–5 minutes and produce a comprehensive report

**Prompt**
```
I am preparing a highly targeted resume for a specific role.

Goal:
Create a Company & Role Dossier that will help me tailor my resume.

Inputs:
1. Company: [Company Name]
2. Public Website: [Homepage URL]
3. Job Description: [Paste full JD or link]
4. My Target Role: [e.g., Senior Product Manager, Payments]

Tasks:
1. Summarize:
   - Company mission and key values
   - Main products/services and target customers
   - Recent notable events in the last 12–18 months (funding, launches, leadership changes, major partnerships).

2. Analyze the role:
   - Core responsibilities in this specific posting
   - Required and preferred skills
   - Typical success metrics for this role in this industry
   - Common pitfalls or failure modes for people in this role.

3. Map the competitive and market context:
   - 3–5 key competitors
   - What seems to differentiate this company
   - Any macro trends that make this role especially important now.

4. Extract language and signals:
   - Top 10–15 keywords and phrases from the job description.
   - Phrases that signal culture or values (e.g., "bias for action," "customer-obsessed").
   - Any red flags or unusual requirements.

Output:
Create a structured markdown dossier with sections:
- Company Snapshot
- Products & Customers
- Recent Moves
- Role Snapshot
- Skills & Success Signals
- Market & Competitors
- Keywords & Phrases
- Open Questions (things I might want to research further)
```

Save the output as something like:  
`[Company]_[Role]_Dossier.md`
(if you don't get anything; simply prompt "give to me in downloadable markdown" - worse case copy and paste into notion or any other notepad/doc tool you like)

> **Did you know:** Deep Research typically pulls from 20-30+ sources and synthesizes them into a coherent report, which saves you hours of manual research.

---
# 5. Step 3 – Choose and Validate a Resume Template

This step is technically optional, but in practice it has a big impact on how well your resume makes it through ATS systems.

## 5.1 What Matters for ATS in 2026

From current ATS optimization resources, a few patterns are consistent across systems:

- Prefer chronological or hybrid formats  
- Single column layout  
- Standard section titles (Work Experience, Education, Skills)  
- Simple fonts (Arial, Calibri, Times New Roman), 10–12 pt  
- No tables, text boxes, images, or multi-column tricks  
- File type: .docx is universally safest (see below)  

The design can still look clean, but structure and parse‑ability come first.

### 5.1.1 File Format: DOCX vs PDF

**The takeaway: When in doubt, use .docx unless the job posting specifically asks for PDF.**

**Why:**
Modern ATS platforms (Greenhouse, Lever, Workday) handle clean PDFs fine, but .docx is safer because:

1. **Universal compatibility** - Works across all systems, including legacy ATS like older Taleo
2. **PDF problems** - PDFs from design tools (Canva, Pages) or scanned docs often fail parsing
3. **Default expectation** - When in doubt, recruiters expect .docx

**Practical approach:**
- Keep both formats
- Submit .docx to online portals (default) - you can export from google docs if your using it
- Use PDF only if explicitly requested or emailing directly to a recruiter

> **Did you know:** Some ATS systems literally ignore content in headers, footers, and text boxes. Beautiful designs can become "blank" resumes to the software.

> **Pro tip:** Test your resume by copying all the text from your PDF and pasting it into a plain text editor. If it looks jumbled or out of order, ATS will struggle too.

# 5.2 Validate Your Existing Template (Or Skip to 5.3)

If you already have a resume template you like, run a quick validation check to make sure it's ATS-safe. If you don't have one yet, skip to Section 5.3.

### 5.2.1 ATS Validation Checklist

Open your current resume and check:

1. Is it single column?  
2. Are there any tables, text boxes, images, or icons?  
3. Are section headings standard and clear (e.g., "Work Experience" not "My Journey")?  
4. Is the font a common system font (Arial, Calibri, Times New Roman)?  
5. Is the file a .docx?  

If you answered "no" to any of these, either simplify your current template or choose a new one.

### 5.2.2 Optional: Ask AI to Validate Your Template

You can also paste your resume into Perplexity or Claude and ask:
```
You are acting as an ATS-oriented resume reviewer.

I will paste the text version of my current resume below. 

Tasks:
1. Ignore visual styling and focus on structure and content.
2. Identify any structural issues that could cause parsing problems (e.g., missing standard section headings, unusual ordering, overuse of symbols).
3. Suggest a clean section order for a [Target Role] in [Country/Region].
4. Suggest improvements to make this more ATS-friendly.

Here is my resume:
[PASTE TEXT-ONLY VERSION HERE]
```

> **Pro tip:** Copy your resume text and paste it into a plain text editor (like Notepad). If the structure looks messy or jumbled, that's what ATS will see too.

# 5.3 If You Need a New Template

You don’t need Perplexity to design a resume visually, but you can use it to get a skeleton structure specific to your role and geography.

**Example prompt:**
```
I am a [Role, e.g., Senior Product Manager] applying in [Country/Region].

Goal:
Recommend an ATS-friendly resume structure for my profile.

Constraints:
1. Single-column, reverse chronological format.
2. Standard section headings only.
3. Prioritize clarity of impact and leadership.

Tasks:
1. Propose an ordered list of sections for my resume.
2. For each section, describe:
   - What content should go there.
   - How many bullets or lines to aim for.
3. Suggest one example layout for the top third of the first page (above the fold) that makes my value obvious quickly.
4. Do NOT write the actual resume content yet. Focus only on structure and layout.
```

You’ll use this structure later when you ask Claude to write the actual content.

> **Pro tip:** Save the agreed‑on structure as a short “Resume Template Spec” file and keep it next to your Master Profile and Company Dossier. That way you always know what shape you’re writing into.

---
# 6. Step 4 – Draft the Resume with Claude Sonnet 4.5

This is where you combine everything: who you are, what the company needs, and how you want to present it.

A key principle here: don’t let Claude write anything until it has:

- Read your Master Profile
    
- Read the Company & Role Dossier
    
- Understood your resume template/structure
    
- Asked you clarifying questions
    

## 6.1 Prepare Your Inputs

Have these ready to paste or attach:

1. Master Profile document (Step 1)
    
2. Company & Role Dossier (Step 2)
    
3. Resume Template Spec (Step 3)
    
4. The actual job description or link
    

## 6.2 First Prompt – Context and Q&A Only

Start with something like this:
```
You are helping me write a targeted, ATS-friendly resume.

I will provide:
1. A Master Profile document describing my experience.
2. A Company & Role Dossier for the job I’m targeting.
3. A Resume Template Spec that describes the structure we’ll use.
4. The actual job description.

Goals:
- Create one highly targeted resume for this specific role.
- Maintain my authentic voice.
- Prioritize clarity, impact, and ATS compatibility.

Rules:
1. First, read and ingest all inputs.
2. Do NOT write the resume yet.
3. After reading, ask me 5–10 focused clarifying questions about:
   - Which experiences to prioritize.
   - Any missing metrics you need.
   - How to handle career pivots or gaps.
   - Tone preferences (more technical vs more business, etc.).
4. Only when I confirm that your understanding is correct will we move to writing.

Here is my Master Profile:
[PASTE OR ATTACH]

Here is the Company & Role Dossier:
[PASTE OR ATTACH]

Here is the Resume Template Spec:
[PASTE OR ATTACH]

Here is the job description:
[PASTE OR ATTACH]
```

Then answer the questions honestly, even if some answers are “I don’t know” or “I’d rather de‑emphasize that experience.”

> **Pro tip:** When Claude asks vague or confusing questions, don’t fight through them. Ask it to restate the question more concretely, or tell it what you _think_ it’s really trying to get at.

## 6.3 Second Prompt – Confirm Strategy Before Writing

Once the clarifying questions are done, you can ask Claude to summarize its plan:

```
Based on everything you’ve read and my answers, please:

1. Summarize in 5–7 bullet points:
   - Which roles and projects you plan to emphasize.
   - How you’ll position my background relative to this role.
   - How you’ll reflect the company’s values and keywords without sounding generic.

2. Confirm:
   - The resume format and section order we’ll use.
   - Any remaining open questions you still have.

Do NOT write the resume yet. I will review and confirm this plan first.
```

If the plan looks off, correct it directly in natural language (e.g., “I want less emphasis on X, more on Y”). Then, when you’re happy:

## 6.4 Third Prompt – Write the First Draft
**Prompt:**
```
Now please write the full resume draft.

Constraints:
1. Follow the agreed section order and structure.
2. Keep the resume to [1 or 2] pages worth of content.
3. Use concise bullet points (1–2 lines each).
4. Focus on accomplishments and outcomes, not job duties.
5. Integrate relevant keywords from the job description naturally.
6. Keep formatting ATS-friendly:
   - No tables, text boxes, or unusual characters.
   - Standard section headings.

Voice:
- Confident but not overhyped.
- Clear, concrete, and specific.
- Avoid clichés and buzzwords where possible.

Output:
- Provide the resume in plain markdown or text format that I can paste into Word or Google Docs.

```

> **Did you know:** In head‑to‑head tests, Claude often produces resumes that balance ATS keywords and natural language better than some other general models, which tend to over‑optimize for keywords or use generic phrasing.

---
# 7. Step 5 – Test, Score, and Refine

Now you have a strong draft. The last step is to make sure:

- ATS can parse it well
    
- The content is specific, verifiable, and non‑generic
    

## 7.1 Run an ATS Check

Use an ATS checker tool of your choice and upload:

- The job description
    
- Your resume draft
    

Look at:

- Overall match score
    
- Missing hard skills or keywords
    
- Formatting warnings
    

You don’t need a perfect score, but aiming for a solid match (often around 80–85% or better) is a reasonable target in many tools.

## 7.2 Ask AI to Flag Generic or Risky Content

You can go back to Perplexity or Claude and ask:

```
You are reviewing this resume for quality and authenticity.

Tasks:
1. Identify any bullet points that:
   - Sound generic or interchangeable.
   - Could apply to almost any candidate.
   - Might be hard to verify based on typical evidence.

2. For each such bullet:
   - Explain why it’s weak.
   - Suggest 1–2 ways to make it more concrete or specific, using only the information already present.
   - If you truly need more detail from me, ask a targeted question.

Here is the resume:
[PASTE RESUME TEXT]
```

You can then either:

- Strengthen those bullets with your own edits, or
    
- Answer the follow‑up questions and let AI draft tighter versions.
    

> **Pro tip:** Any bullet that you would struggle to defend with a real story in an interview is a candidate for revision or removal.

## 7.3 (Optional) Create Two Variants

If you’re applying to a lot of similar roles, it can be useful to maintain:

- One “core” version of your resume
    
- One “variant” that leans slightly more technical, strategic, or leadership‑heavy
    

You can track which one seems to generate more callbacks over time.

---

# 8. Tool Setup and Alternatives

## Recommended Stack

**This guide uses:**
- **Perplexity Pro** - Company/role research, market analysis
- **Claude Sonnet 4.5** - Resume structuring, drafting, Q&A loops

**Don't have these exact tools?** Use any strong research tool + any long-context writing model. The key is the *pattern*:

1. Capture rich profile of yourself
2. Deeply understand company/role
3. Decide on clear structure
4. Force AI to ask questions before writing
5. Validate and iterate

The workflow matters more than the specific tools.

---
# 9. Why This Workflow Works

From the research you pulled together earlier:

- Using a detailed “master resume” or career document gives AI far better raw material and reduces hallucinations or invented achievements.
    
- Candidates who research company mission, values, recent moves, and competitors produce more tailored, compelling resumes and interview stories.
    
- ATS‑friendly structure (single column, standard headings, simple fonts) remains critical in 2026, even as tools get more sophisticated.
    
- Iterative Q&A with AI before writing significantly improves output quality versus one‑shot prompts.
    
- Separating research, writing, and validation phases mirrors how strong analysts and PMs work in other domains, and transfers well to resume building.
    

This workflow essentially treats your job search like a product:  
- you collect data
- understand the user (hiring manager / company)
- design the interface (resume structure)
- ship and iterate

---
# 10. What To Do After You Have This Resume

Once you’ve gone through all five steps and you have a resume you’re happy with, a few next moves make the process compound over time:

1. Save a “core” version and keep it updated
    
    - When you ship something meaningful at work, add it to your Master Profile.
        
    - Periodically refresh your resume for new types of roles you might want next.
        
2. Build a simple application log
    
    - Track which resume version you used, which company, which role, and whether you got interviews.
        
    - Over time, notice patterns: which types of bullets, structures, or emphasis seem to get more traction.
        
3. Reuse your research
    
    - The Company & Role Dossier is also raw material for cover letters, LinkedIn tweaks, and interview prep.
        
    - You can ask AI to turn the same dossier into a tailored cover letter or a “talk track” for interviews.
        
4. Tighten the loop
    
    - When you get feedback (explicit or implicit), feed it back into this workflow.
        
    - For example: “These roles seem to care more about X than Y; let’s rebalance my resume for future applications.”

# 11. Frequently Asked Questions

**Q: How long does this take?**
A: First time: 2-3 hours. Subsequent resumes: 45-60 minutes (you reuse Master Profile and just update research).

**Q: Can I do this without paid AI tools?**
A: Yes, but I DO NOT RECOMMEND IT. Your job search is worth $20/30. Give up something for one month, do it proper.

**Q: Do I need a new resume for every application?**
A: For your top 5-10 dream roles: yes, customize fully. For others: use a "core" version with minor keyword tweaks.

**Q: What if I have career gaps or am changing industries?**
A: Address directly in your Master Profile. Tell Claude in Section 6.2 how you want to position it (transferable skills, intentional pivot, etc.).

**Q: How do I know if my resume is working?**
A: Track callback rate. If <10% for roles you're qualified for, revisit ATS optimization (Step 5) or ask for resume reviews.

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
Original: https://github.com/VeritasPlaybook/playbook/blob/main/career-workflow/resume-workflow/An%20AI-Powered%20Resume%20Workflow.md
License: CC BY 4.0

# Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- 💼 [LinkedIn](https://github.com/Veritas-Research/investment-research)
- 🐙 [GitHub](https://github.com/VeritasNotes)
- 📊 [Investment Research]([https://github.com/VeritasResearch](https://github.com/Veritas-Research/investment-research))

---

*If you found this valuable, star ⭐ the repo to help others find it.*
