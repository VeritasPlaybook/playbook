>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Career Brain Trust INDEX (Example: Engineer Alex)

**Purpose:** Master file map for Alex Rivera's Career Brain Trust. The resume-builder and update-brain-trust skills read this file first, then selectively load the child files relevant to the Job Description (JD) at hand.

**Folder root:** `[Alex's Job Search Folder]\Brain Trust\`
**Last updated:** 2026-05-21

**About this example:** This is a fictional Career Brain Trust for a persona, "Alex Rivera", a Senior Backend Engineer (Go primary, Python secondary) with 5 to 7 years of experience, targeting Staff Engineer roles. Companies, dates, and metrics are illustrative. Use this as a model for what a filled Brain Trust looks like at middle depth for an engineering individual contributor (IC).

---

## How to use this INDEX

1. **Always read** the top-level small files first (rows tagged `always_load: yes`).
2. **Selectively read** Experience and Cover Letters files by grep-matching the Job Description against the Tags column.
3. **Never read** the whole Career Brain Trust by default. Tool truncation kicks in around 25,000 tokens of output.

---

## Session Rules (always load)

| File | Tags | Always Load | Summary |
|---|---|---|---|
| `_session rules\code samples on github.md` | `#Rule` `#Portfolio` | yes | When the Job Description asks for code samples, always link to the GitHub profile in the cover letter, not just the resume. |
| `_session rules\always use skill creator.md` | `#Rule` `#SkillUpdates` | yes | Locked rule: when updating any skill, always invoke skill-creator. |

---

## Top-Level Files (always load)

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `0 How To Use.md` | Section 0 | `#Reference` `#Acronyms` `#TagGlossary` | yes | Tag glossary, acronym definitions, maintenance habits |
| `1 Identity.md` | Section 1 | `#Identity` `#Positioning` `#Summaries` `#Headline` | yes | LinkedIn headline, professional summary, 7 alternate positioning statements tagged by angle |
| `2 Chronology.md` | Section 2 | `#Chronology` `#Dates` `#Titles` `#Canonical` | yes | Master career chronology table |
| `5 Skills.md` | Section 5 | `#Skills` `#Tools` `#TechStack` | yes | Aggregated skill inventory: Languages, Distributed Systems, Databases, Cloud, Methodologies |
| `6 Achievements.md` | Section 6 | `#Achievements` `#BigNumbers` `#Metrics` | yes | Headline metrics organized by employer with source attribution |
| `7 Education.md` | Section 7 | `#Education` `#Certifications` `#Awards` `#Languages` | yes | Bachelor of Science in Computer Science from Oregon State University, Amazon Web Services certification, open-source contributions |

## Cover Letters always-load files

| File | Section | Tags | Always Load | Summary |
|---|---|---|---|---|
| `Cover Letters/4.0 Patterns.md` | Section 4 | `#CoverLetterStyle` `#Patterns` | yes | The recurring cover letter skeleton (shorter and more pragmatic than Product Manager letters) |
| `Cover Letters/4.20 Reusable Hooks.md` | Section 4 | `#Hooks` `#Reusable` `#All` | yes | Modular building blocks: openers, technical-depth signals, code-portfolio anchors, mentorship blocks |

---

## Experience Library (Section 3): selectively load by tag match

| File | Role | Dates | Tags | Summary |
|---|---|---|---|---|
| `Experience/3.1 Beacon Pay.md` | Beacon Pay, Senior Backend Engineer | Jul 2023 to Present | `#Engineering` `#Backend` `#FinTech` `#Payments` `#Go` `#Distributed` `#Postgres` `#Citus` `#Idempotency` `#RFC` `#Mentor` `#Scale` `#Senior` | Current role. Transaction processing service in Go, idempotency primitives, Postgres-to-Citus migration, payment routing, Request-for-Comments (RFC) ownership, mentorship |
| `Experience/3.2 Lumen Streams.md` | Lumen Streams, Software Engineer | Mar 2021 to Jun 2023 | `#Engineering` `#Backend` `#Streaming` `#Infrastructure` `#Go` `#Python` `#Kafka` `#gRPC` `#ServiceMesh` `#SDK` `#Scale` | Real-time stream ingestion in Go, exactly-once semantics, gRPC service mesh migration, first Python Software Development Kit (SDK), hiring-loop work |
| `Experience/3.3 Hearthstone Labs.md` | Hearthstone Labs, Software Engineer | Sep 2019 to Feb 2021 | `#Engineering` `#Backend` `#Python` `#FastAPI` `#0to1` `#Startup` `#CICD` `#Foundational` | Early-stage Python work: core Representational State Transfer (REST) API in FastAPI, Continuous Integration / Continuous Deployment (CI/CD) pipeline, migration tooling, headcount growth from 4 to 14 |

---

## Cover Letter Library (Section 4): selectively load by tag match

| File | Target | Tags | Summary |
|---|---|---|---|
| `Cover Letters/4.1 Backend Infrastructure.md` | Backend infrastructure and developer platforms (Cloudflare, Fly.io, Vercel, PlanetScale, Sentry, and similar) | `#Backend` `#Infrastructure` `#Platform` `#Go` `#Distributed` | Technical-depth-first opener, code-portfolio anchor, distributed-systems credibility, mentorship as supporting line |
| `Cover Letters/4.2 Fintech Payments.md` | Fintech and payments infrastructure (Stripe, Modern Treasury, Mercury, Adyen, and similar) | `#FinTech` `#Payments` `#Go` `#Distributed` `#Idempotency` `#Compliance` | Payments-specific credibility (idempotency, reconciliation, multi-acquirer routing), regulatory familiarity, on-call discipline |

---

## Selective-read workflow for the resume-builder skill

When tailoring a resume for a Job Description, the skill should:

1. Read this INDEX file.
2. Read all `always_load: yes` files.
3. Extract Job Description signals (language, distributed-systems primitives, scale, on-call expectations, mentorship).
4. Grep the Tags columns for matches.
5. Read only the 2 or 3 Experience files whose Tags overlap most strongly with the JD.
6. Read only the 1 or 2 Cover Letters files whose Tags overlap most strongly with the JD.

---

## Maintenance rules for the update-brain-trust skill

Same pattern as the other examples. After each application:

1. Append a Variant Framing to the relevant Experience file.
2. Append new metrics to `6 Achievements.md`.
3. Create or update the relevant Cover Letters archetype file.
4. Update positioning statements in `1 Identity.md` when surfaced.
5. Refresh the **Last updated** date here.
6. Append the entry to `Application Log.md` (outside this folder).

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

Based on the Engineer Alex example Career Brain Trust, part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook
License: CC BY 4.0
