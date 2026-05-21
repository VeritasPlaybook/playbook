# Install: Update Brain Trust skill

This skill closes the loop on a finished job application by folding the tailored resume and cover letter back into your Career Brain Trust. New framings get added to the right per-role file, new metrics get added to your achievements file, new cover-letter hooks get added to the reusable hooks library, and the application gets logged to your application log.

It runs at the end of an application thread, after the `resume-builder` skill (or any tailoring conversation) has produced the actual material.

You have two ways to install it. Pick whichever fits your comfort level.

**Option A (recommended): Install with Claude.** Open the file `Install with Claude.md` in this same folder. It contains a paste-into-Cowork prompt. Claude walks you through the configuration questions and edits the files for you.

**Option B: Manual install.** Follow the steps below.

You can rename this skill if `update-brain-trust` does not fit your naming. See "Renaming the skill" at the bottom.

---

## Prerequisites

1. Claude Desktop with Cowork mode enabled.
2. A Career Brain Trust folder you have set up (see the Career Brain Trust template in the same playbook).
3. The `resume-builder` skill installed first (or equivalent tailoring workflow) so you have application material to ingest.
4. Python 3 with `python-docx` installed (`pip install python-docx`) if the skill needs to split a combined `.docx` into separate cover and resume files for archive.

---

## Step 1: Locate your Cowork skills directory

Cowork loads skills from a known directory on your computer.

- On Windows the path is typically `%APPDATA%\Claude\skills\`.
- On macOS the path is typically `~/Library/Application Support/Claude/skills/`.

Open Cowork settings to confirm the exact path for your installation.

## Step 2: Copy this folder into the skills directory

Copy the entire `update-brain-trust` folder (the one containing this `INSTALL.md`) into your Cowork skills directory.

The folder name stays `update-brain-trust` (lowercase hyphen) because that matches the Cowork skill-naming convention. If you rename the folder, you must also rename the `name:` field in `SKILL.md` to match.

## Step 3: Restart Cowork

Quit and reopen Cowork. Skills register when Cowork starts.

## Step 4: Customize SKILL.md for your setup

Open `SKILL.md` in the copied folder and replace these placeholders with your actual paths:

- `[Your Career Brain Trust folder]` becomes the absolute path to your Career Brain Trust folder
- `[Your Applications folder]` becomes the folder where the `resume-builder` skill saves combined .docx files (where this skill reads from)
- `[Your Past Resumes folder]` becomes the folder where archived copies of past resumes and cover letters are saved
- `[Your Application Log path]` becomes the folder where `Application Log.md` is stored

If the folders do not exist yet, create them. The skill will create `Application Log.md` the first time it runs if the file is missing.

## Step 5: Seed the canonical facts cheat sheet (optional but recommended)

Scroll to the "Canonical facts cheat sheet" section near the bottom of `SKILL.md`. By default it contains placeholder rows showing the format.

Replace those rows with your own canonical facts once you have noticed at least one contradiction across your applications. Examples of the kinds of facts to track:

- A lifetime impact number you have quoted differently in different applications (lock to canonical, list the outdated variants).
- A company or product name you have spelled inconsistently.
- A role title or date range that has been quoted slightly differently.
- A framing verb that overclaims your involvement ("built" versus "contributed to") and which is canonical.

It is fine to start empty and grow this list one row at a time as you discover contradictions. The cheat sheet is the highest-leverage piece of meta-knowledge in the workflow because it is what stops you from re-introducing yesterday's mistakes.

## Step 6: Verify install

In a new Cowork thread that already has a finished tailored resume in context (or pointed at a folder with one), type a trigger phrase like:

> Update the brain trust with this application.

Claude should detect the skill and start Phase 1 by searching the thread for the most recent tailored `.docx` and asking you to confirm before proceeding.

If the skill does not trigger, open `SKILL.md` and confirm the `description:` field is intact. Cowork uses that field to decide whether to invoke the skill.

---

## Renaming the skill

If `update-brain-trust` does not fit your naming preference, rename it:

1. Rename the folder from `update-brain-trust` to your chosen name (lowercase hyphen format works best for Cowork: `loop-closer`, `ingest-application`, etc.).
2. Open `SKILL.md` and change the `name:` field in the YAML frontmatter to match the new folder name exactly.
3. Restart Cowork.

The trigger phrases listed in the `description:` field will still work.

---

## About the evals subfolder

This skill ships with an optional `evals/` subfolder. It is not required for install. If you want to run benchmark tests on your skill (for example, after you customize it heavily), see the README inside `evals/` for how to point it at your own fixtures.

If you do not care about evals, ignore the folder. It does not affect runtime behavior.

---

## Where to look if things break

- **Skill is not triggering:** check the `description:` field in `SKILL.md` is intact, and the folder is in the right Cowork skills directory.
- **Skill cannot find the application material:** the skill searches the current thread context for the most recent `.docx`. If your tailoring happened in a different thread, paste the resume and cover letter text directly into the next message when prompted.
- **Past Resumes folder is empty after a run:** check that `[Your Past Resumes folder]` is a real, writeable path on your computer. The skill creates files there but cannot create the folder itself.
- **Application Log.md formatting drifts over time:** the skill appends new entries. If the schema gets out of shape (extra blank lines, broken table), open the file and clean it manually; the next run will append cleanly from there.

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Tailored, Not Templated" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
