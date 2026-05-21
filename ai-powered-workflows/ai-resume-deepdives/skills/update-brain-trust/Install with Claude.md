# Install with Claude: Update Brain Trust skill

Paste the prompt below into a fresh Cowork thread to have Claude install and configure this skill for you. Claude will ask the configuration questions in multi-choice format, edit the SKILL.md placeholders, and verify install.

If you prefer to install manually instead, see `INSTALL.md` in this same folder.

---

## Before pasting

1. Copy the entire `update-brain-trust` folder into your Cowork skills directory. The location depends on your operating system; check Cowork settings if unsure (typically `%APPDATA%\Claude\skills\` on Windows or `~/Library/Application Support/Claude/skills/` on macOS).
2. Confirm you have a Career Brain Trust folder set up. If not, set one up first using the Career Brain Trust template in the same playbook.
3. Open a fresh Cowork thread pointed at your workspace folder.
4. Paste the prompt below.

---

## The prompt

```
I just copied the `update-brain-trust` skill into my Cowork skills directory. I need you to configure it for my setup and verify the install.

Please walk me through this in multi-choice format with a copy-paste answer sheet (Q1: A, Q2: B, etc. plus an answer sheet at the end I can fill in once).

Configuration questions I need you to ask me:

1. The absolute path to my Career Brain Trust folder. If I do not have one yet, stop here and point me at the Career Brain Trust template in the same playbook so I can build it first.
2. The absolute path to my Applications folder (where the resume-builder skill saves combined .docx files; this skill reads from there).
3. The absolute path to my Past Resumes folder (where archived copies of resumes and cover letters are saved). If it does not exist, ask me whether to create it.
4. The absolute path to my Application Log folder (where Application Log.md is stored). If it does not exist, ask me whether to create it.
5. Whether I want to seed the canonical facts cheat sheet now (yes with at least one fact I will dictate, or skip and seed later as I notice contradictions across applications).

After I answer, you should:

a. Open the SKILL.md inside the `update-brain-trust` skill folder and replace every `[Your Career Brain Trust folder]`, `[Your Applications folder]`, `[Your Past Resumes folder]`, and `[Your Application Log path]` placeholder with my actual values.

b. Create any folders I confirmed in questions 3 and 4 if they do not already exist.

c. If I provided canonical facts in question 5, replace the placeholder rows in the "Canonical facts cheat sheet" section of SKILL.md with my actual rows. If I skipped, leave the placeholder rows in place with a note that I will seed them later as contradictions surface.

d. Verify install by surfacing the trigger phrase pattern. Confirm to me that a sample phrase like "update the brain trust with this application" would trigger the skill, and explain how I would know it triggered (you would start Phase 1 by searching the current thread for the most recent tailored .docx file).

Important rules while you do this work:

- Use multi-choice questions with copy-paste answer sheets for every question.
- Never produce drafts or take write actions before I confirm.
- No em dashes anywhere in your output.
- Define acronyms in full on first use.

Start by asking me the five configuration questions.
```

---

## What happens after install

Run this skill at the end of every job application thread, after the `resume-builder` skill (or any tailoring conversation) has produced the actual material. Trigger phrases include "update the brain trust", "ingest this into the brain trust", "fold this back into the brain trust", or "log this application". Claude runs the three-phase workflow: ingest, clarify, update.

Over many applications the brain trust accumulates: new variant framings per role, new metrics, new cover letter archetypes, new reusable hooks. The system gets sharper every time you close the loop.

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Tailored, Not Templated" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
