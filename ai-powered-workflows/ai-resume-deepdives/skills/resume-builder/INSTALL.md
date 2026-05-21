# Install: Resume Builder skill

This skill produces a tailored resume and cover letter as a single Word document (.docx) from a Job Description (JD), using your Career Brain Trust as the source of truth.

You have two ways to install it. Pick whichever fits your comfort level.

**Option A (recommended): Install with Claude.** Open the file `Install with Claude.md` in this same folder. It contains a paste-into-Cowork prompt. Claude walks you through the configuration questions, edits the files for you, and verifies install. Faster, less manual work.

**Option B: Manual install.** Follow the steps below if you prefer to see every change before it happens.

You can rename this skill if `resume-builder` does not fit your naming. See "Renaming the skill" at the bottom of this file.

---

## Prerequisites

1. Claude Desktop with Cowork mode enabled.
2. A Career Brain Trust folder you have set up. If you do not have one yet, see the Career Brain Trust template in the same playbook and build it first; this skill depends on the folder structure.
3. A `.docx` Application Template you want all output to use. Any single-file template works. The skill is template-agnostic. You will generate a small build script tailored to your template (see Step 5 below).
4. Python 3 with `python-docx` installed if you want to use the generated build script approach. Install with `pip install python-docx`.

---

## Step 1: Locate your Cowork skills directory

Cowork loads skills from a known directory on your computer.

- On Windows the path is typically `%APPDATA%\Claude\skills\`.
- On macOS the path is typically `~/Library/Application Support/Claude/skills/`.

Open Cowork settings to confirm the exact path for your installation; the location can vary by Claude Desktop version.

## Step 2: Copy this folder into the skills directory

Copy the entire `resume-builder` folder (the one containing this `INSTALL.md`) into your Cowork skills directory.

The folder name stays `resume-builder` (lowercase hyphen) because that matches the Cowork skill-naming convention. If you rename the folder, you must also rename the `name:` field in `SKILL.md` to match. See "Renaming the skill" below.

## Step 3: Restart Cowork

Quit and reopen Cowork. Skills register when Cowork starts.

## Step 4: Customize SKILL.md for your setup

Open `SKILL.md` in the copied folder and replace these placeholders with your actual paths and personal details:

- `[Your Career Brain Trust folder]` becomes the absolute path to your Career Brain Trust folder
- `[Your Templates folder]` becomes the absolute path to the folder that holds your Application Template .docx
- `[Your Applications folder]` becomes the folder where you want tailored applications saved
- `[Your Name]` becomes your name as it should appear on the resume signature line

If you have any hard guard rules you want enforced on every application (for example: never include certain past roles, never reference certain past projects on certain companies' applications, always frame a lapsed certification in past tense), add them under the "Customization: Guard rules" block at the bottom of `SKILL.md`. By default there are no guard rules active.

## Step 5: Generate a build script for your template

The skill does NOT ship with a generic build script, because every `.docx` template has different style names, numbering definitions, and structural quirks. You will generate one tailored to your template in a single Cowork prompt.

Open a Cowork thread pointed at the folder holding your `.docx` template. Paste this:

> Look at my template at `[Your Templates folder]/Application Template.docx`. Write me a Python script using python-docx that takes a JSON payload with cover paragraphs and resume role blocks, builds the .docx exactly matching the template's styles, and saves it to `[Your Applications folder]/[Company] - [Role].docx`. Use the bullet numId my template actually defines (parse word/numbering.xml). Skip any title-table append; the template already has my portfolio link if present.

Save the resulting script as `scripts/build_application.py` inside this skill folder.

A minimal reference example showing the bare-bones structural pattern is at `scripts/example_build.py` in this same folder. It is educational, not production. Use it as a comparison point when reviewing whatever Claude generates.

## Step 6: Verify install

In a new Cowork thread, type a trigger phrase like:

> Let us apply to Acme Fintech for the Director of Product Payments role.

Claude should detect the skill and start the 11-step workflow at Step 0 by asking for the company name, role title, and JD format.

If the skill does not trigger, open `SKILL.md` and confirm the `description:` field is intact. Cowork uses that field to decide whether to invoke the skill.

---

## Renaming the skill

If `resume-builder` does not fit your naming preference, rename it:

1. Rename the folder from `resume-builder` to your chosen name (lowercase hyphen format works best for Cowork: `application-builder`, `cover-and-resume`, etc.).
2. Open `SKILL.md` and change the `name:` field in the YAML frontmatter to match the new folder name exactly.
3. Restart Cowork.

The trigger phrases listed in the `description:` field will still work because they are detected from natural-language patterns, not the skill name itself.

---

## Where to look if things break

- **Skill is not triggering:** check the `description:` field in `SKILL.md` is intact, and the folder is in the right Cowork skills directory.
- **Build script fails:** open the script and check the paths match your actual folders. Most template-specific bugs come from the `numId` mismatch described in Step 9 of `SKILL.md`.
- **Output looks wrong (bullets render as plain indented text):** Trap B from Step 9 fired. The build script is using a `numId` that does not exist in your template's `word/numbering.xml`. Regenerate the script with Claude in a Cowork thread, this time explicitly asking it to parse `numbering.xml` first.
- **Duplicated portfolio link in the title table:** Trap A from Step 9 fired. The build script is appending a link the template already contains. Regenerate the script and tell Claude to skip the title-table append.
- **Brain trust files not found:** check that your Career Brain Trust folder structure matches the file names referenced in `SKILL.md` (spaces in filenames, not underscores).

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Tailored, Not Templated" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
