---
name: resume-builder
description: Use this skill whenever the user wants to apply for a job, build a tailored resume and cover letter, or create an application package from a Job Description (JD). Trigger phrases include "I want to apply for X role", "build a resume for X", "tailor a resume", "make a cover letter for X", "help me apply", "let us apply to X", "X is hiring", "I found a job at X", or any request referencing a JD and asking for application material. Always trigger when the user references a JD and wants tailored application output, even if the exact wording differs. Do NOT use this skill for LinkedIn profile rewrites or for editing existing applications without a fresh JD.
---

# Resume Builder skill

This skill produces a tailored combined resume and cover letter as a single Word document (.docx) from a Job Description (JD), using a Career Brain Trust as the source of experience, metrics, and reusable phrasings.

The workflow has 11 steps. Follow them in order. Steps 2 and 6 require the user's input; pause and wait. Step 9 is intentionally a teaching step rather than a hardcoded script, because every user has a different .docx template and a one-size script either locks readers into the author's template or hides the trade-offs that matter.

---

## Step 0: Confirm intake

Confirm back to the user in one line:

- Company name
- Role title
- JD format (paste, .pdf upload, or URL)

If the JD is a URL, use WebFetch to retrieve it. If a .pdf, use the pdf skill or the Read tool. If pasted, capture it verbatim into context.

---

## Step 1: Read the Career Brain Trust (selective, INDEX-driven)

The Career Brain Trust is a folder of small markdown files: per-role experience, per-archetype cover letters, identity, chronology, skills, achievements, education. It is structured this way so the skill can load only the few files relevant to the JD at hand, rather than the whole corpus. Tool output truncation kicks in around 25,000 tokens, so a monolithic single-file brain trust eventually breaks silently.

The selective-read workflow:

**1a. Read the INDEX first.** Always read `[Your Career Brain Trust folder]/INDEX.md` before anything else. This is the file map with a Tags column per child file.

**1b. Read all always-load files.** These are small and required for any application:

- `[Your Career Brain Trust folder]/0 How To Use.md` (acronyms and tag glossary)
- `[Your Career Brain Trust folder]/1 Identity.md` (headline, summary, library of alternate positioning statements)
- `[Your Career Brain Trust folder]/2 Chronology.md` (canonical dates, titles, any data discrepancies)
- `[Your Career Brain Trust folder]/5 Skills.md` (skill inventory)
- `[Your Career Brain Trust folder]/6 Achievements.md` (big numbers by employer)
- `[Your Career Brain Trust folder]/7 Education.md` (credentials, languages, public profiles)
- `[Your Career Brain Trust folder]/Cover Letters/4.0 Patterns.md` (house-style skeleton)
- `[Your Career Brain Trust folder]/Cover Letters/4.20 Reusable Hooks.md` (modular building blocks)

**1c. Extract JD signals.** From the JD, surface: industry tags, function tags, seniority, technical keywords, tone hints.

**1d. Selectively read Experience files.** Grep the INDEX Tags column against JD signals. Read only the 3 to 4 Experience files whose Tags overlap most strongly with the JD. Always include the most recent role file (numbered 3.1) regardless of overlap, because the most recent role is almost always relevant.

**1e. Selectively read Cover Letters files.** Grep the INDEX Tags column for 1 to 3 archetype files whose Tags overlap most strongly with the JD.

**1f. Apply guard rules.** If the user has configured guard rules in the customization block at the bottom of this SKILL.md, apply them here. By default there are none active. Guard rules are how readers prevent the skill from making the same mistake twice across applications.

**1g. Surface in one or two sentences:** "Strongest brain trust angles for this JD: [X], [Y]. Reading [list of selectively-loaded files]."

---

## Step 2: Generate a deep research prompt

Generate ONE comprehensive Deep Research prompt the user will run in Perplexity Pro (or equivalent, like ChatGPT Deep Research or Gemini Deep Research) to gather company and role context. Output this prompt as a markdown code block the user can copy.

The prompt must:

- Cover the company's business model, products, recent news (last 6 months), tech stack, culture signals, mission, and recent strategic moves
- Cover the role context: where this role sits in the org, what the team likely owns, what good looks like, common patterns at similar companies
- Skip interviewer and hiring manager research unless the hiring manager is explicitly named in the JD
- Instruct the research tool to output a single self-contained markdown file with clear section headers
- Instruct the research tool to cite sources inline

After delivering the prompt, tell the user: "Drop the markdown result back as a chat attachment when ready."

PAUSE HERE. Wait for the attachment.

---

## Step 3: Read research, mine for hooks

When the user drops the markdown result, read it carefully. Pull out:

- 2 to 3 mission-aligned phrases the user can echo in the cover letter
- 1 to 2 product or strategic moves to reference as proof of attention
- Any culture or language patterns (for example: "high-agency", "lean team")
- Any technical specifics that match the user's brain trust (tech stack overlap)

---

## Step 4: Fit and risks check (BEFORE drafting)

Scan the JD requirements against the user's brain trust. Identify 2 to 3 gaps or weak spots. For each:

- Name the gap precisely
- State the closest analogue from the brain trust
- Propose a handling option (minimize, reframe, address head-on, skip)

Present as a numbered list. Note that the user will confirm handling in Step 6.

---

## Step 5: Build a keyword coverage map

Pull keywords from the JD (technical terms, tools, methodologies, soft skills, domain terms). For each, map where it will land in the application:

| JD keyword | Where it lands |
|------------|----------------|
| [keyword 1] | Cover reason X, Core Competencies, [Role] bullet Y |
| [keyword 2] | Cover reason Z, Core Competencies |

Show this table to the user before drafting. Ask if any keyword is missing or weak.

---

## Step 6: Expanded clarifying questions

Use the AskUserQuestion tool with these five questions, always with copy-paste answer sheet format:

1. **Positioning angle** (lead with strongest credential, balance two strongest credentials, niche translation angle, custom for this JD)
2. **Which 3 best-fit examples to keep** (give 3 options drawn from the brain trust)
3. **Fit and risks acceptance** (confirm handling chosen in Step 4 or change)
4. **Tone slider** (formal, balanced, punchy)
5. **Anything to specifically emphasize or avoid** (open option)

PAUSE HERE. Wait for answers.

---

## Step 7: Draft the cover letter

Cover letter house style (default; the user can override in the customization block at the bottom of this SKILL.md):

- Opener: "If you are looking for [tailored description of the role], I am your match."
- Header: "What makes me your ideal candidate?"
- Four bolded reasons (use brain trust Cover Letters folder hooks; tailor each to the chosen positioning angle)
- Each reason is 2 to 4 sentences
- Closing: "If you feel I would be an asset to [their mission], please reach out. I would love to discuss how I can add value."
- Sign off: "Sincerely, [Your Name]"
- Target length: 330 to 400 words
- NO em dashes. NO en dashes. Use pipe separators with double spaces ("  |  ") for inline lists.
- Common acronyms (Product Manager (PM), Machine Learning (ML), Artificial Intelligence (AI), Vice President (VP), Application Programming Interface (API)) appear as acronyms without definition for technical hiring audiences once defined on first use. Specialized acronyms (anything industry-specific) defined in full on first use, then shorthand.
- NO name-dropping in the cover letter: no specific executives by name, no target company vendor stack callouts. Lean on the user's own portfolio for technical fluency signals.
- Cover letter has NO title block table; vertically push the body down with approximately four empty paragraphs above the "Dear ..." line.

Weave portfolio or GitHub evidence into the relevant paragraph as prose, not a bullet list, if the user has a public portfolio.

---

## Step 8: Draft the resume body

Resume structure (page 2 and beyond):

1. **Title block table** (preserve from template, do not rebuild): name, city, email, LinkedIn, portfolio link
2. **Core Competencies** (Heading 1): ONE wrapped block of pipe-separated competencies, max 3 lines at body font size. Not three paragraphs. Only competencies the user can defend with concrete experience AND that match the JD. Roughly 10 to 14 items.
3. **Experience** (Heading 1): roles in canonical chronological order from the Career Brain Trust Experience folder
4. **Advisory Engagements** (Heading 1): optional section if the user has advisory roles to surface
5. **Education** (Heading 1)
6. **Certifications and Awards** (Heading 1): optional section

**NEVER include a Summary section.** The cover letter handles positioning. The resume goes from title block directly to Core Competencies. A Summary section duplicates the cover letter and burns the recruiter's first 10 seconds on prose they have already seen.

Role header format: bold company-and-title line, italic dates-and-location line. NO Heading 2 or Heading 3 styles.

Bullet format: normal paragraph with the template's bullet numbering. Use the `numId` the template actually defines (see Step 9 for why this matters).

**Verbatim sources:** every bullet must be traceable to a Career Brain Trust framing. Do NOT fabricate metrics. Use canonical numbers; if a number conflicts with what the user said in chat, surface the conflict and ask which is authoritative.

---

## Step 9: Build the .docx

This skill does NOT bundle a generic build script, because every user has a different .docx template, and a one-size script either locks readers into the author's template or hides the trade-offs that actually matter.

Instead, here is what the build step needs to do, and how to get a working build script for the user's specific template. Ask Claude in the same Cowork thread to write this script (Claude can do it from the user's actual template in under a minute).

**What the build script must do:**

1. Open the user's `.docx` template with `python-docx`.
2. Preserve the section properties (`sectPr`) and any prefilled title table at the bottom of the template.
3. Strip the rest of the body.
4. Insert the cover letter paragraphs first, with approximately four empty leading paragraphs above the "Dear ..." line for vertical positioning.
5. Insert a hard page break.
6. Insert the title table block at the top of page 2 (move it from its original position).
7. Add the resume content using the template's actual style names ("Heading 1" for section headers, normal paragraphs with the template's bullet numbering for resume bullets).
8. Save to the configured output folder using `[Company] - [Role].docx` naming.

**Two non-obvious traps worth telling Claude about when it writes the script:**

**Trap A: Title table duplication.** If the template already contains the user's portfolio link or social handles in its title table, naive "append link to title" helper code will duplicate them on every build. The script should either skip that helper entirely, or detect the existing hyperlink before appending.

**Trap B: Bullet `numId` mismatch.** Most `.docx` templates define a small number of numbering definitions in `word/numbering.xml`, often only `numId="1"`. If the script hardcodes a different `numId` (a common copy-paste mistake from generic python-docx tutorials), bullets render as plain indented text. The script should parse the template's `numbering.xml` and use a `numId` the template actually defines.

**How to get the script written.** In the same Cowork thread where this skill is running, ask Claude:

> Look at my template at `[Your Templates folder]/Application Template.docx`. Write me a Python script using python-docx that takes a JavaScript Object Notation (JSON) payload with cover paragraphs and resume role blocks, builds the .docx exactly matching the template's styles, and saves it to `[Your Applications folder]/[Company] - [Role].docx`. Use the bullet numId my template actually defines (parse word/numbering.xml). Skip any title-table append; the template already has my portfolio link.

Save the generated script alongside this SKILL.md as `scripts/build_application.py` for future re-use.

A minimal reference example showing the bare-bones structural pattern (open template, strip body, page break, save) is at `scripts/example_build.py` in this skill folder. It is educational, not production. Use it as a comparison point when reviewing whatever Claude generates for your template.

---

## Step 10: Verify

After build, verify:

- Count em dashes (must be 0) and en dashes (must be 0).
- Acronym hygiene: common technical acronyms appear bare for technical hiring audiences once defined on first use; specialized acronyms are defined in full on first use.
- Dates match the brain trust canonical chronology.
- JD keywords from the Step 5 coverage map all appear in the doc. Allow 1 to 3 misses for company-specific terminology the user cannot defend.
- No fabricated metrics. Every number traces to the brain trust.
- NO Summary section appears in the resume.
- Open the .docx and visually check bullets render with bullet markers, not as plain indented text. If they render as plain text, Trap B fired; revisit the build script.
- Check the title table for duplicated portfolio links. If there are two, Trap A fired.
- Optionally run a .docx validator if one is available.

If anything fails, fix and re-verify before delivering.

---

## Step 11: Deliver

Provide:

- The `computer://` link to the file at `[Your Applications folder]/[Company] - [Role].docx`
- A short summary of: positioning angle used, how fit gaps were handled, keyword coverage at a glance
- An offer: "Open it, review, and tell me what to adjust."

---

## Customization: Guard rules (optional)

By default, this skill has no guard rules. Many users want hard rules that prevent the skill from making the same mistake twice. Add yours here as plain bullet points. Examples of the kinds of rules people use:

- "Never include roles from before [year] on the tailored resume."
- "For [target company] applications, never mention [past advisory engagement] anywhere."
- "Always frame [lapsed certification] in past tense."

These are illustrative only. Add your own based on what you discover across applications. Keep this block short; it is read on every run.

---

## Reference files

- Career Brain Trust folder root: `[Your Career Brain Trust folder]/` (configure during install)
- INDEX (read first): `[Your Career Brain Trust folder]/INDEX.md`
- Application template: `[Your Templates folder]/Application Template.docx`
- Output folder: `[Your Applications folder]/`
- Reference build script stub: `scripts/example_build.py` (in this skill folder)
- Real build script for your template: `scripts/build_application.py` (you generate this in Step 9)

---

## Locked preferences for this skill (default; override during install)

- Combined single .docx output (cover letter page 1, resume page 2 and beyond). Never produce separate cover and resume files.
- File naming: `[Company] - [Role].docx`.
- No em dashes. No en dashes. Pipe separator with double spaces ("  |  ").
- Acronym pattern: common technical acronyms (PM, ML, AI, VP, API) appear bare for technical hiring audiences once defined on first use; specialized acronyms defined in full on first use, then shorthand.
- No name-dropping in cover letters: no specific executives by name, no target company vendor stack callouts.
- NEVER include a Summary section in the resume.
- Core Competencies is ONE wrapped block, max 3 lines, only defendable items.
- Two-page maximum. Cover letter 330 to 400 words. Four bolded reasons.
- Always ask clarifying questions with Q1: A, B, C and copy-paste answer sheet format.
- Never produce output without explicit approval to proceed.
