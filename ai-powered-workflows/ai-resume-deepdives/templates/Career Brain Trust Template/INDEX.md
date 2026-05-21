>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this template for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Career Brain Trust INDEX

**Purpose:** Master file map for your Career Brain Trust. Your resume-builder and update-brain-trust skills read this file first, then selectively read the child files relevant to the Job Description (JD) at hand.

**Folder root:** `[Your Brain Trust Folder Path]`
**Last updated:** [YYYY-MM-DD]

---

## How to use this INDEX

1. **Always read** the top-level small files first (rows tagged `always_load: yes`).
2. **Selectively read** Experience and Cover Letters files by grep-matching the Job Description (JD) against the Tags column.
3. **Never read** the whole Career Brain Trust by default. Tool truncation kicks in around 25,000 tokens of output.

This selective-read pattern is what lets the system stay fast and accurate even when your Brain Trust grows to 30 or 40 files. The INDEX is the routing table. Every other file is leaf content the skills load on demand.

---

## Session Rules (always load)

| File | Tags | Always Load | Summary |
|---|---|---|---|
| `_session rules\always use skill creator.md` | `#Rule` `#SkillUpdates` `#Workflow` | yes | Locked rule: when updating any skill, always invoke skill-creator. Never stage SKILL.md files in a stray "Skill Updates" folder. |

Add your own session rules here over time. Each one is a one-line policy your skills should honor on every run. Examples of common session rules:

- Never include a Summary section on the resume (assume the cover letter does that job).
- Core Competencies on the resume is one wrapped block, maximum three lines.
- Never include any role that predates a specific career pivot date.
- For applications to a specific company, never mention a specific past advisory engagement.
- Treat any lapsed certification as past tense ("formerly Certification-X-certified 20YY to 20YY").

These rules are how you stop relearning the same lessons. Encode each one as a small file, list it here, and the skills will load it every session.

---

## Top-Level Files (always load)

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `0 How To Use.md` | Section 0 | `#Reference` `#Acronyms` `#TagGlossary` | yes | Tag glossary, acronym definitions, instructions for filling in and maintaining the Brain Trust |
| `1 Identity.md` | Section 1 | `#Identity` `#Positioning` `#Summaries` `#Headline` | yes | LinkedIn headline, professional summary, library of alternate positioning statements tagged by angle |
| `2 Chronology.md` | Section 2 | `#Chronology` `#Dates` `#Titles` `#Canonical` | yes | Master career chronology table, with any data discrepancy resolutions |
| `5 Skills.md` | Section 5 | `#Skills` `#Tools` `#TechStack` | yes | Aggregated skill inventory across function, tools, domains, leadership |
| `6 Achievements.md` | Section 6 | `#Achievements` `#BigNumbers` `#Metrics` | yes | Headline metrics organized by employer, with source attribution |
| `7 Education.md` | Section 7 | `#Education` `#Certifications` `#Awards` `#Languages` | yes | Degrees, certifications, awards, languages, public profile links |

## Cover Letters always-load files

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `Cover Letters/4.0 Patterns.md` | Section 4 | `#CoverLetterStyle` `#Patterns` | yes | Your recurring cover letter skeleton (opener, header, bolded reasons, closing) |
| `Cover Letters/4.20 Reusable Hooks.md` | Section 4 | `#Hooks` `#Reusable` `#All` | yes | Modular building blocks: openers, breadth blocks, credibility blocks, reusable reason headers |

---

## Experience Library (Section 3): selectively load by tag match

Add one row per role. Use the same numbering scheme: `3.1` is your most recent role, `3.2` is the second most recent, and so on. Off-LinkedIn or advisory roles can use `3.A1`, `3.A2`, etc.

| File | Role | Dates | Tags | Summary |
|---|---|---|---|---|
| `Experience/3.1 Most Recent Role.md` | [Most Recent Title at Most Recent Employer] | [Month YYYY to Present] | `#Tag1` `#Tag2` `#Tag3` | One-sentence summary of the role and its standout contributions |
| `Experience/3.2 Second Most Recent Role.md` | [Title at Prior Employer] | [Month YYYY to Month YYYY] | `#Tag1` `#Tag2` `#Tag3` | One-sentence summary |
| `Experience/3.3 Third Most Recent Role.md` | [Title at Earlier Employer] | [Month YYYY to Month YYYY] | `#Tag1` `#Tag2` `#Tag3` | One-sentence summary |

Add more rows as you add more role files.

---

## Cover Letter Library (Section 4): selectively load by tag match

Add one row per archetype. Use `4.1`, `4.2`, etc. The archetype is the company shape, not the specific company. Examples of common archetypes:

- Banking (formal, credentialed, regulatory tone)
- Startup (direct, punchy, builder voice)
- Big Tech (crisp, metrics-heavy, scale framing)
- Developer-facing platform (technical-depth signal, builder voice)
- Mission-driven nonprofit or impact (mission echo, values match)

| File | Target | Tags | Summary |
|---|---|---|---|
| `Cover Letters/4.1 Archetype One.md` | [Archetype name, e.g., Banking] | `#Banking` `#Formal` | Short description of when to use this archetype |
| `Cover Letters/4.2 Archetype Two.md` | [Archetype name, e.g., Startup] | `#Startup` `#Builder` | Short description of when to use this archetype |

Add more rows as you add more archetype files. Real reusable archetypes tend to emerge after about ten applications. Until then, the Generic archetype plus this Patterns file is enough.

---

## Selective-read workflow for the resume-builder skill

When tailoring a resume for a Job Description, the skill should:

1. Read this INDEX file.
2. Read all `always_load: yes` files (top-level plus the two Cover Letters always-load files).
3. Extract Job Description (JD) signals: industry, function, seniority, technical keywords, tone.
4. Grep this INDEX's Tags columns for matches against JD signals.
5. Read only the three or four Experience files whose Tags overlap most strongly with the Job Description.
6. Read only the one to three Cover Letters files whose Tags overlap most strongly with the Job Description.
7. Optionally read a specific Section 3 file if you explicitly name a role in your clarifying-question answers, even if tag overlap is weak.

**Default load (for any Job Description):** roughly 8 always-load files plus 3 to 4 role files plus 1 to 3 cover letter files. Combined token count well under the 25,000-token tool truncation limit.

---

## Maintenance rules for the update-brain-trust skill

When ingesting a new application, the skill should:

1. Read the relevant Experience file (e.g., `3.1 Most Recent Role.md`) and append a new Variant Framing entry to its "Variant Framings" block.
2. If the application introduced new metrics or numbers, append to `6 Achievements.md` under the matching employer header.
3. If the application introduced a new cover letter archetype, create a new file `Cover Letters/4.NN [Archetype].md` and add a row to the Cover Letter Library table in this INDEX.
4. If the application reused an existing archetype, append a Variant Framings note inside that archetype file.
5. If the application surfaced a new positioning statement, append it to the positioning library in `1 Identity.md`.
6. Update the **Last updated** date at the top of this INDEX.
7. Append the application entry to an `Application Log.md` file (kept outside the Brain Trust folder, in your job-search root).
8. Save copies of the tailored resume and cover letter files to a `Past Resumes/` folder (also outside the Brain Trust folder).

The point of these rules is that the system additively gets sharper without rewriting your canonical content. New material lands as variants. Canonical bullets only change if you explicitly say so.

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

If you use or adapt this template, please include:

Based on the Career Brain Trust template, part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
