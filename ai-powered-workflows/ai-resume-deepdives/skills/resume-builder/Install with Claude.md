# Install with Claude: Resume Builder skill

Paste the prompt below into a fresh Cowork thread to have Claude install and configure this skill for you. Claude will ask the configuration questions in multi-choice format, edit the SKILL.md placeholders, generate a build script tailored to your template, and verify install.

If you prefer to install manually instead, see `INSTALL.md` in this same folder.

---

## Before pasting

1. Copy the entire `resume-builder` folder into your Cowork skills directory. The location depends on your operating system; check Cowork settings if unsure (typically `%APPDATA%\Claude\skills\` on Windows or `~/Library/Application Support/Claude/skills/` on macOS).
2. Confirm you have an Application Template .docx saved somewhere on your computer.
3. Confirm you have a Career Brain Trust folder set up. If not, set one up first using the Career Brain Trust template in this same playbook. This skill depends on the folder structure.
4. Open a fresh Cowork thread pointed at your workspace folder.
5. Paste the prompt below.

---

## The prompt

```
I just copied the `resume-builder` skill into my Cowork skills directory. I need you to configure it for my setup and verify the install.

Please walk me through this in multi-choice format with a copy-paste answer sheet (Q1: A, Q2: B, etc. plus an answer sheet at the end I can fill in once).

Configuration questions I need you to ask me:

1. The absolute path to my Career Brain Trust folder. If I do not have one yet, stop here and point me at the Career Brain Trust template in the same playbook so I can build it first.
2. The absolute path to my Templates folder (the folder holding my Application Template .docx file).
3. The absolute path to my Applications folder (where tailored output should save).
4. My name as it should appear on the resume signature line.
5. Whether I want any hard guard rules added to the skill (for example: never include certain past roles, never mention certain past projects on certain companies' applications, always frame a lapsed certification in past tense). Open free-text answer if yes; skip if no.

After I answer, you should:

a. Open the SKILL.md inside the `resume-builder` skill folder and replace every `[Your Career Brain Trust folder]`, `[Your Templates folder]`, `[Your Applications folder]`, and `[Your Name]` placeholder with my actual values.

b. If I added guard rules in question 5, append them under the "Customization: Guard rules" block at the bottom of SKILL.md as plain bullet points. Keep the block short.

c. Look at my Application Template .docx and write me a Python build script using python-docx (per Step 9 in the SKILL.md). Save it to `scripts/build_application.py` in the skill folder. Make sure to handle the two traps Step 9 describes: title-table duplication and bullet numId mismatch. Parse the template's word/numbering.xml first to find a numId that actually exists, and check whether the title table already contains a portfolio link before appending. Confirm python-docx can open my template successfully before declaring the script ready.

d. Verify install by surfacing the trigger phrase pattern. Confirm to me that a sample phrase like "let us apply to Acme Fintech for the Director role" would trigger the skill, and explain how I would know it triggered (you would start with Step 0 asking for company name, role title, and JD format).

Important rules while you do this work:

- Use multi-choice questions with copy-paste answer sheets for every question.
- Never produce drafts or take write actions before I confirm.
- No em dashes anywhere in your output.
- Define acronyms in full on first use.

Start by asking me the five configuration questions.
```

---

## What happens after install

Once the configuration is applied and the build script is in place, every future job application is a single Cowork thread pointed at a project folder for that application. Trigger the skill with a phrase like "let us apply to [Company] for the [Role] role" and Claude runs the 11-step workflow.

If anything in the install breaks, the troubleshooting section at the bottom of `INSTALL.md` covers the common failure modes.

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Tailored, Not Templated" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
