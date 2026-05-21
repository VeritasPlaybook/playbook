>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Career Brain Trust INDEX (Example: PM Jordan)

**Purpose:** Master file map for Jordan Chen's Career Brain Trust. The resume-builder and update-brain-trust skills read this file first, then selectively load the child files relevant to the Job Description (JD) at hand.

**Folder root:** `[Jordan's Job Search Folder]\Brain Trust\`
**Last updated:** 2026-05-21

**About this example:** This is a fictional Career Brain Trust for a persona, "Jordan Chen", a Senior Product Manager (PM) in Business-to-Business Software-as-a-Service (B2B SaaS) with 6 to 8 years of experience, targeting Lead Product Manager or Group Product Manager roles. Companies, dates, and metrics are illustrative. Use this as a model for what a filled Brain Trust looks like at middle depth.

---

## How to use this INDEX

1. **Always read** the top-level small files first (rows tagged `always_load: yes`).
2. **Selectively read** Experience and Cover Letters files by grep-matching the Job Description against the Tags column.
3. **Never read** the whole Career Brain Trust by default. Tool truncation kicks in around 25,000 tokens of output.

---

## Session Rules (always load)

| File | Tags | Always Load | Summary |
|---|---|---|---|
| `_session rules\never include early roles.md` | `#Rule` `#Chronology` | yes | Never include Jordan's pre-PM analyst role (2018) on a tailored resume. PM journey starts at Quantile Insights (Aug 2019). |
| `_session rules\always use skill creator.md` | `#Rule` `#SkillUpdates` | yes | Locked rule: when updating any skill, always invoke skill-creator. |

---

## Top-Level Files (always load)

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `0 How To Use.md` | Section 0 | `#Reference` `#Acronyms` `#TagGlossary` | yes | Tag glossary, acronym definitions, maintenance habits |
| `1 Identity.md` | Section 1 | `#Identity` `#Positioning` `#Summaries` `#Headline` | yes | LinkedIn headline, professional summary, 8 alternate positioning statements tagged by angle |
| `2 Chronology.md` | Section 2 | `#Chronology` `#Dates` `#Titles` `#Canonical` | yes | Master career chronology table and 2 data discrepancy resolutions |
| `5 Skills.md` | Section 5 | `#Skills` `#Tools` `#TechStack` | yes | Aggregated skill inventory: Product, Developer Workflow, Healthcare SaaS, Analytics, Leadership |
| `6 Achievements.md` | Section 6 | `#Achievements` `#BigNumbers` `#Metrics` | yes | Headline metrics organized by employer with source attribution |
| `7 Education.md` | Section 7 | `#Education` `#Certifications` `#Awards` `#Languages` | yes | BA Cognitive Science from University of Vermont, Reforge Growth Series alum, languages, public profiles |

## Cover Letters always-load files

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `Cover Letters/4.0 Patterns.md` | Section 4 | `#CoverLetterStyle` `#Patterns` | yes | The recurring four-part cover letter skeleton |
| `Cover Letters/4.20 Reusable Hooks.md` | Section 4 | `#Hooks` `#Reusable` `#All` | yes | Modular building blocks: openers, breadth blocks, credibility blocks, reason headers |

---

## Experience Library (Section 3): selectively load by tag match

| File | Role | Dates | Tags | Summary |
|---|---|---|---|---|
| `Experience/3.1 Tessera.md` | Tessera, Senior Product Manager, Developer Workflow | Dec 2023 to Present | `#Product` `#DeveloperTools` `#Platform` `#SaaS` `#AI` `#Workflow` `#Integrations` `#Build` `#Scale` `#Senior` | Current role. Real-time code review interface, workflow automation engine, AI task assistant, 6 new connectors, customer council |
| `Experience/3.2 Brightline Health Systems.md` | Brightline Health Systems, Product Manager, Clinician Workflow | Mar 2021 to Nov 2023 | `#Product` `#VerticalSaaS` `#Healthcare` `#EHR` `#Compliance` `#HIPAA` `#Build` `#Usability` | Clinician documentation workflow, Electronic Health Records (EHR) integrations, inbox redesign, HIPAA-compliant patient messaging |
| `Experience/3.3 Quantile Insights.md` | Quantile Insights, Associate Product Manager | Aug 2019 to Feb 2021 | `#Product` `#Analytics` `#B2BSaaS` `#NLQ` `#SDK` `#0to1` `#Onboarding` `#Foundational` | Natural-language query feature, embedded analytics Software Development Kit (SDK), product spec template, onboarding research program |

---

## Cover Letter Library (Section 4): selectively load by tag match

| File | Target | Tags | Summary |
|---|---|---|---|
| `Cover Letters/4.1 Developer-First SaaS.md` | Developer-facing platforms (Linear, GitHub, Vercel, PlanetScale, and similar) | `#DeveloperTools` `#Platform` `#Builder` `#Technical` | Direct register, builder voice, technical depth signal, integrations breadth, AI-in-the-loop framing |
| `Cover Letters/4.2 Vertical SaaS.md` | Vertical Software-as-a-Service (healthcare, legal, construction, education) | `#VerticalSaaS` `#Domain` `#Usability` `#Compliance` `#Trust` | Domain empathy first, usability and trust signals, compliance fluency, change-management acknowledgment |

---

## Selective-read workflow for the resume-builder skill

When tailoring a resume for a Job Description, the skill should:

1. Read this INDEX file.
2. Read all `always_load: yes` files (6 top-level files plus 2 Cover Letters always-load files).
3. Extract Job Description signals (industry, function, seniority, technical keywords, tone).
4. Grep this INDEX's Tags columns for matches against JD signals.
5. Read only the 2 or 3 Experience files whose Tags overlap most strongly with the JD.
6. Read only the 1 or 2 Cover Letters files whose Tags overlap most strongly with the JD.

**Default load (for any JD):** about 8 always-load files plus 2 or 3 role files plus 1 or 2 cover letter files = 11 to 13 small files. Combined token count well under the 25,000-token tool truncation limit.

---

## Maintenance rules for the update-brain-trust skill

When ingesting a new application:

1. Read the relevant Experience file and append a new Variant Framing entry.
2. If the application introduced a new metric or number, append to `6 Achievements.md`.
3. If the application introduced a new cover letter archetype, create a new `4.NN [Archetype].md` file and add a row above.
4. If the application reused an existing archetype, append a Variant Framings note inside that archetype file.
5. If the application surfaced a new positioning statement, append it to Section 1C in `1 Identity.md`.
6. Update the **Last updated** date at the top of this INDEX.
7. Append the application entry to `Application Log.md` (outside this folder).
8. Save copies of the tailored resume and cover letter to `Past Resumes/` (outside this folder).

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

If you use or adapt this example, please include:

Based on the PM Jordan example Career Brain Trust, part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
