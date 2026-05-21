>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this prompt for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Career Brain Trust Setup Prompt

This is the interview prompt you paste into a fresh AI thread to build your Career Brain Trust by interview. The AI will walk you through phase by phase, ask multi-choice clarifying questions, and produce the file structure described in the Career Brain Trust Template.

---

## How to use this prompt

1. Open a fresh thread in your AI tool (Claude in Cowork mode is the canonical setup; ChatGPT, Gemini, and Perplexity will also work if you adjust the file-writing instructions to match what your tool can do).
2. Point the tool at the parent folder where you want your Career Brain Trust to live (e.g., `[Your Job Search Folder]\Brain Trust\`).
3. Copy everything inside the `## The prompt` section below.
4. Paste it as the first message in the thread.
5. Answer the AI's interview questions one phase at a time.
6. The AI saves files as you go. Open them after each phase to verify they look right.
7. When the interview ends, you have a working version one of your Brain Trust.

If you do not have AI tooling that can write files to your computer, paste the prompt anyway. The AI will generate the files as markdown blocks in the chat. You then copy each block into a file in the right location by hand. Slower, but it still works.

---

## The prompt

> You are helping me build a Career Brain Trust: a structured folder of small markdown files that holds my professional identity, my career chronology, my role-by-role experience with canonical bullets and variant framings, my skills inventory, my big-number achievements, my education and certifications, and my reusable cover letter archetypes.
>
> The point of this folder is to be the source of truth for an AI-driven resume tailoring workflow. A future thread will read a Job Description, scan an INDEX file in this folder, and selectively load the three or four role files and one to three cover letter archetypes that best match the Job Description. Then it drafts a tailored resume and cover letter from my actual content. Garbage in, garbage out: the better this Brain Trust is, the sharper every tailored application will be.
>
> Your job in this thread is to interview me one phase at a time and produce a working version one of every file in the folder. We will iterate later. Do not try to make every file perfect on the first pass. Get something usable in place; we will sharpen over time as I run real applications through it.
>
> ### Rules for the interview
>
> 1. Walk me through one phase at a time. Do not skip ahead. Do not produce more than one phase's files at once.
> 2. Use multi-choice clarifying questions whenever possible. Format each question as `Q1: A, B, C, or D`. At the end of each round of questions, give me a copy-paste answer sheet (e.g., `Q1: A, Q2: B, Q3: C`) so I can respond quickly.
> 3. After each phase, save the file or files for that phase to the right location. Show me the file path and confirm the file was saved before moving on.
> 4. If I do not yet have content for a section (e.g., I have no certifications), use generic placeholders in brackets like `[No certifications yet]` rather than making something up.
> 5. Never invent metrics, employers, dates, or accomplishments. If I am not sure of a number, write `[verify]` next to it.
> 6. Avoid em dashes anywhere in the output. Use commas, periods, parentheses, or colons instead. Do not substitute double hyphens.
> 7. Define acronyms in full the first time they appear in any file (e.g., "Product Manager (PM)"), then use the acronym for the rest of that file.
> 8. Use spaces in filenames, not underscores. Use Title Case for top-level file names (e.g., `1 Identity.md`, not `1_identity.md`).
> 9. Match the file structure described below exactly. Do not invent extra files until I ask.
>
> ### Folder structure to produce
>
> ```
> Brain Trust/
> |
> |-- INDEX.md
> |-- 0 How To Use.md
> |-- 1 Identity.md
> |-- 2 Chronology.md
> |-- 5 Skills.md
> |-- 6 Achievements.md
> |-- 7 Education.md
> |
> |-- Experience/
> |   |-- 3.1 [Most Recent Role].md
> |   |-- 3.2 [Second Most Recent Role].md
> |   |-- 3.3 [Third Most Recent Role].md
> |   (one file per role; use 3.A1, 3.A2 for advisory or off-LinkedIn roles)
> |
> |-- Cover Letters/
>     |-- 4.0 Patterns.md
>     |-- 4.20 Reusable Hooks.md
>     |-- 4.1 [First Archetype].md
>     |-- 4.2 [Second Archetype].md
>     (add more archetype files over time)
> ```
>
> ### Interview phases
>
> Walk me through these phases in order. At the start of each phase, briefly explain what that phase is for and what I'll get out of it.
>
> **Phase 1: Identity (file `1 Identity.md`).**
> Ask me about my current LinkedIn headline, my two-or-three-sentence professional summary, and my top three positioning angles (e.g., builder, scale, domain specialist, generalist, leader, hands-on, mission-aligned, pivot). For each angle I name, ask me to draft one short positioning statement. Save the file. Move on.
>
> **Phase 2: Chronology (file `2 Chronology.md`).**
> Ask me to list every role I have held in reverse chronological order: title, employer, start date, end date, location. Get the full list before drafting. Then save the file with a master chronology table. Ask if there are any date or title discrepancies you should record.
>
> **Phase 3: Per-role deep dive (files `Experience/3.1 [Role].md`, `3.2`, `3.3`, etc., one at a time).**
> For each role, in reverse chronological order, ask:
> - What are the three to six bullets you most want a hiring manager to see? Get them in my voice. These become the canonical bullets.
> - What are the headline metrics you can defend in an interview? (e.g., "Reduced fraud rate by X percent within 90 days.")
> - What are two or three reusable phrasings or hooks from this role that show up in your cover letters?
> - What are the most useful tags for this role (function, domain, technical, stage)?
> Save the file. Confirm. Move to the next role.
>
> **Phase 4: Skills (file `5 Skills.md`).**
> Ask me to list skills across function, technical, domain, leadership, tools, methodologies, languages. Use multi-choice questions to nominate likely skills based on what I described in Phase 3, then let me confirm or edit. Save the file.
>
> **Phase 5: Achievements (file `6 Achievements.md`).**
> Ask me, for each employer, what are the two or three big-number metrics I would put in a headline if I could pick only that many. For each one, ask where the number comes from (the source). Save the file.
>
> **Phase 6: Education (file `7 Education.md`).**
> Ask about degrees, certifications (active and lapsed), awards, languages, and public profile URLs. Save the file.
>
> **Phase 7: Cover letter foundation (files `Cover Letters/4.0 Patterns.md` and `4.20 Reusable Hooks.md`).**
> Ask me which company archetypes I most often apply to (banking, startup, big tech, developer-facing platform, mission-driven nonprofit, agency, etc.). Pick two to start with. For each, ask:
> - What is the tone for this archetype?
> - What three to four bolded reason headlines tend to recur across applications to this archetype?
> Save `4.0 Patterns.md` with the four-part skeleton (opener, header, bolded reasons, closing). Save `4.20 Reusable Hooks.md` with the openers, breadth blocks, credibility blocks, reason headers, and closings I've used. Then create `4.1 [First Archetype].md` and `4.2 [Second Archetype].md` with the archetype-specific notes.
>
> **Phase 8: INDEX and How To Use (files `INDEX.md` and `0 How To Use.md`).**
> Now that everything else is built, generate the INDEX with the routing table (file paths, tags, summaries) and the How To Use file with the tag glossary and acronym definitions. Save both.
>
> ### Closing the loop
>
> At the end of Phase 8, summarize what we built: which files exist, where they live, and any sections I marked `[verify]` or left as placeholders. Recommend the three to five highest-value things I could add or refine first if I want to invest another half hour now. Otherwise, we are done; the Brain Trust is ready for the resume-builder skill to use.
>
> Begin Phase 1 now. Ask me your first round of multi-choice clarifying questions about my identity.

---

## Tips for the human running the interview

A few things that make the interview go faster:

- Have your current LinkedIn profile open in a tab. Most of Phase 1 and Phase 2 lift from there directly.
- Have your most recent resume open. Phase 3 leans on canonical bullets you've already written.
- Block out roughly an hour. The interview is faster than building from scratch, but it still benefits from focused time. Splitting it across two sessions is fine if you need a break after Phase 3.
- If a question stumps you, answer "skip for now" and the AI will leave a placeholder you can fill in later. Do not pause the whole interview because one role's variant framings are not coming to you.
- After every phase, open the file the AI just saved. Confirm it looks right before moving on. Catching a mistake one phase later is much cheaper than catching it five phases later.

---

## What to do after the interview

Once you have a working version one of your Brain Trust:

1. Open the empty `Application Log.md` file (kept outside the Brain Trust folder, in the parent job-search folder). This is where the update-brain-trust skill will log every application.
2. Install the resume-builder and update-brain-trust skills in your AI tool of choice (Cowork instructions are in Deep Dive 6 of the main guide).
3. Run your first tailored application end to end. The first application will surface gaps in your Brain Trust you did not anticipate. That is normal. Note what was missing.
4. Update the relevant files. Re-run a different application. Each cycle sharpens the source of truth.

The Brain Trust is never "done." It is a living document that gets sharper every time you close the loop after an application.

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

If you use or adapt this prompt, please include:

Based on the Career Brain Trust Setup Prompt, part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
