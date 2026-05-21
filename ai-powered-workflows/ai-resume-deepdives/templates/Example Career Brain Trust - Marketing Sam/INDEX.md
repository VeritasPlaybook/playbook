>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Career Brain Trust INDEX (Example: Marketing Sam)

**Purpose:** Master file map for Sam Whitford's Career Brain Trust. The resume-builder and update-brain-trust skills read this file first, then selectively load the child files relevant to the Job Description (JD) at hand.

**Folder root:** `[Sam's Job Search Folder]\Brain Trust\`
**Last updated:** 2026-05-21

**About this example:** This is a fictional Career Brain Trust for a persona, "Sam Whitford", a Senior Marketing Manager with 6 to 8 years of experience pivoting from traditional marketing (broadcast, print, retail) to digital and Product-Led Growth (PLG), targeting Director of Marketing or Head of Growth roles. Companies, dates, and metrics are illustrative. Use this as a model for what a filled Brain Trust looks like for a marketer mid-pivot.

The interesting thing about this persona is the pivot framing. Sam's Brain Trust deliberately keeps the traditional-marketing accomplishments canonical (those are the longest-tenured and best-defended wins), while building up newer digital and Product-Led Growth wins as the pivot evidence. The cover letter archetypes acknowledge the pivot head-on rather than hiding it.

---

## How to use this INDEX

1. **Always read** the top-level small files first (rows tagged `always_load: yes`).
2. **Selectively read** Experience and Cover Letters files by grep-matching the Job Description against the Tags column.
3. **Never read** the whole Career Brain Trust by default. Tool truncation kicks in around 25,000 tokens of output.

---

## Session Rules (always load)

| File | Tags | Always Load | Summary |
|---|---|---|---|
| `_session rules\acknowledge the pivot.md` | `#Rule` `#Pivot` | yes | For Product-Led Growth and Software-as-a-Service Job Descriptions, acknowledge the pivot from traditional marketing explicitly in the cover letter. Hiding it reads worse than naming it. |
| `_session rules\always use skill creator.md` | `#Rule` `#SkillUpdates` | yes | Locked rule: when updating any skill, always invoke skill-creator. |

---

## Top-Level Files (always load)

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `0 How To Use.md` | Section 0 | `#Reference` `#Acronyms` `#TagGlossary` | yes | Tag glossary, acronym definitions, maintenance habits, pivot framing notes |
| `1 Identity.md` | Section 1 | `#Identity` `#Positioning` `#Summaries` `#Headline` | yes | LinkedIn headline, professional summary, 8 alternate positioning statements tagged by angle |
| `2 Chronology.md` | Section 2 | `#Chronology` `#Dates` `#Titles` `#Canonical` | yes | Master career chronology table |
| `5 Skills.md` | Section 5 | `#Skills` `#Tools` `#TechStack` | yes | Aggregated skill inventory: Traditional, Digital, Product-Led Growth, Tools, Methodologies |
| `6 Achievements.md` | Section 6 | `#Achievements` `#BigNumbers` `#Metrics` | yes | Headline metrics organized by employer, with both traditional and digital wins, source attribution |
| `7 Education.md` | Section 7 | `#Education` `#Certifications` `#Awards` `#Languages` | yes | Bachelor of Arts in Communications, Reforge certificates (Growth Marketing, Retention and Engagement), Google Analytics and HubSpot certifications |

## Cover Letters always-load files

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `Cover Letters/4.0 Patterns.md` | Section 4 | `#CoverLetterStyle` `#Patterns` | yes | The recurring cover letter skeleton, with pivot-aware opening pattern |
| `Cover Letters/4.20 Reusable Hooks.md` | Section 4 | `#Hooks` `#Reusable` `#All` | yes | Modular building blocks: openers, brand-to-growth bridges, traditional-to-digital translation hooks |

---

## Experience Library (Section 3): selectively load by tag match

| File | Role | Dates | Tags | Summary |
|---|---|---|---|---|
| `Experience/3.1 Cordata Outfitters.md` | Cordata Outfitters, Senior Marketing Manager, Lifecycle and Direct-to-Consumer | Mar 2023 to Present | `#Marketing` `#Lifecycle` `#DTC` `#Retail` `#Mobile` `#Email` `#Push` `#Growth` `#PLG` `#Senior` `#Build` | Current role. The bridge role: came in as a brand marketer, built and now owns the direct-to-consumer (D2C) mobile-app lifecycle program from zero |
| `Experience/3.2 Mosswood and Co.md` | Mosswood & Co., Marketing Manager, Brand and Retail | Jun 2020 to Feb 2023 | `#Marketing` `#Brand` `#Retail` `#CPG` `#Broadcast` `#Print` `#InStore` `#RetailPartnerships` `#Manager` | Traditional brand marketing at a small-batch coffee company. Owned broadcast, print, in-store, and retail-partnership programs |
| `Experience/3.3 Aldercroft Media.md` | Aldercroft Media, Account Executive (promoted from Coordinator) | Aug 2018 to May 2020 | `#Marketing` `#Agency` `#Campaigns` `#CPG` `#Retail` `#Coordinator` `#Foundational` | First role. Agency-side account management across consumer packaged goods (CPG) and retail clients; foundational campaign-execution chops |

---

## Cover Letter Library (Section 4): selectively load by tag match

| File | Target | Tags | Summary |
|---|---|---|---|
| `Cover Letters/4.1 Product-Led Growth SaaS.md` | Pure-play Software-as-a-Service (SaaS) Product-Led Growth (PLG) companies (consumer apps, freemium SaaS, growth-led startups) | `#SaaS` `#PLG` `#Growth` `#Lifecycle` `#Pivot` | Pivot acknowledged head-on, leads with the Cordata Outfitters lifecycle wins, brand-marketing background framed as transferable foundation |
| `Cover Letters/4.2 Retail Digital Transformation.md` | Hybrid retail / Direct-to-Consumer (D2C) companies in the middle of their own digital transformation | `#Retail` `#DTC` `#Brand` `#Lifecycle` `#Transformation` | Leads with the traditional roots as a feature, not a bug; positions Sam as bilingual between brand and growth |

---

## Selective-read workflow for the resume-builder skill

Same general pattern. For Product-Led Growth and Software-as-a-Service Job Descriptions, also load `_session rules\acknowledge the pivot.md` so the cover letter handles the pivot framing correctly.

---

## Maintenance rules for the update-brain-trust skill

Standard pattern. One specific note for Sam: when ingesting a new application after Phase 1 of the pivot, append the new digital or Product-Led Growth metric to BOTH the relevant Experience file's Variant Framings AND `6 Achievements.md`. The pivot evidence is the asset that compounds fastest; treat it accordingly.

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

Based on the Marketing Sam example Career Brain Trust, part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
