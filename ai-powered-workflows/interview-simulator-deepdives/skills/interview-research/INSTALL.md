>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the interview-research skill

This skill builds the intelligence layer for one specific interview round, producing a Company and Role Brief, one Interviewer Dossier per human in the room, and an explicit written list of claims you are not allowed to assert out loud.

You have two ways to install it.

**Option A, recommended.** Open `Install with Claude.md` in this folder, paste the prompt inside into Claude, and let Claude do the copying and customizing with you. It asks multiple choice questions about your folder layout and research tools, then configures the skill to match. Most people should take this path, because Step 4 below decides whether the skill is useful, and answering questions is easier than guessing at what a placeholder wants.

**Option B, manual.** Follow the five steps on this page. It takes about ten minutes.

---

## Prerequisites

1. **Claude Desktop with skills support.** Skills are read from a folder on your computer at startup. If your version has no skills folder, this skill will not load.
2. **A round folder**, one per round rather than per company, named `[Company] - [Round Label]`, for example `Northwind Payments - Hiring Manager Round`.
3. **The templates from this kit** in that folder, in particular `_STATE.md`, `Company and Role Brief.md`, and `Interviewer Dossier.md`.
4. **The Prompt Library folder** from this kit, somewhere Claude can read it. The skill builds prompts from it rather than writing them from scratch each time.
5. **At least one deep research tool.** Claude's own research mode counts. A second, different tool is strongly recommended, because the reconciliation step depends on having two independent passes to compare.

You do not need a Career Brain Trust for this skill. That one matters for the Story Bank and the simulator.

---

## Step 1: Locate your skills directory

On Windows, open a File Explorer window and paste this into the address bar:

```
%APPDATA%\Claude\skills\
```

On macOS, open Finder, press Command and Shift and G together, and paste:

```
~/Library/Application Support/Claude/skills/
```

If the `skills` folder does not exist, create it.

A hedge worth taking seriously: this location has moved between application versions, and it may move again. If the path above is empty or missing after you install a skill and restart, check your application's settings for a skills or extensions section, which usually names the exact directory it reads from. Trust the application over this page.

---

## Step 2: Copy the folder

Copy the entire `interview-research` folder, the one containing `SKILL.md`, into your skills directory. Copy the folder itself, not just the file inside it.

When you are done you should have:

```
skills/
  interview-research/
    SKILL.md
    INSTALL.md
    Install with Claude.md
```

The folder name matters. It should match the `name` field in the YAML frontmatter at the top of `SKILL.md`, which is `interview-research`. If you want a different name, see the renaming section below and change both.

---

## Step 3: Restart

Quit Claude Desktop completely and reopen it. Closing the window is usually not enough, because the application keeps running. On Windows, quit from the system tray. On macOS, use Command and Q, or quit from the menu bar.

Skills are read once at startup. A skill copied into the folder while the application is running will not be seen until you restart.

---

## Step 4: Customize the placeholders in SKILL.md

Open `SKILL.md` in any text editor and replace the square bracket placeholders with your real paths. There are three:

- `[Your round folder]`. Because this changes every round, either leave it as a placeholder and give Claude the path each session, or point it at a parent folder such as `C:\Interviews\` and let Claude ask which round you mean.
- `[Your Career Brain Trust folder]`, if you have one. Delete the line if you do not, rather than leaving a path that will not resolve.
- `[Your Story Bank folder]`. A shared folder is better than a per round copy, because the Story Bank is the only part of this kit that is fully reusable.

Then scroll to `## Customization: Guard rules (optional)` and either add your own guard rules or delete the two illustrative examples, because that block is read on every run.

Do not change the `description` field in the frontmatter. It decides whether the skill triggers, and it is written to be distinct from the other three skills in this kit so they do not fight each other.

---

## Step 5: Verify the install

Start a new conversation and type:

```
I have an interview at Northwind Payments next week. Help me research the company and the interviewers.
```

You should see Claude invoke the `interview-research` skill by name, then ask you the Step 1 questions about the round, meaning the company, the exact role title, who is in the room, format, length, what the recruiter called it, and where it sits in the loop. It should offer those as multiple choice where possible with a copy and paste answer sheet, and it should accept "I am guessing" as an answer.

What you should NOT see is Claude immediately producing a company summary from memory. If that happens, the skill did not load. Check Step 3 and Step 1 again.

---

## Renaming the skill

You can rename it. Two things have to change together, and changing one without the other breaks the install silently.

1. The folder name inside your skills directory.
2. The `name` field in the YAML frontmatter at the top of `SKILL.md`.

Both must be lowercase with hyphens instead of spaces. `interview-research`, `round-intel`, and `pre-interview-research` are all valid. `Interview Research` and `interview_research` are not.

If you rename it, also update the `Do NOT use this skill for` clause in the descriptions of the other three skills in this kit, because they name their siblings explicitly to avoid triggering on each other's work. A skill whose sibling names are wrong still works, but it will occasionally answer a question that belonged to a different skill.

---

## Where to look if things break

**The skill never triggers.** Usually the application was not fully quit before restarting, or the folder went into the wrong directory. Ask Claude "what skills do you have available" and see whether it is listed.

**The wrong skill triggers.** Usually the interview-simulator skill answering a research request, or the reverse. The exclusion clauses at the end of each description keep them apart, and editing a description to make it read better is the usual way this gets broken.

**Claude claims it did the research.** It should not. This skill builds the prompts and consumes the output you paste back. If findings appear without you running anything, the skill did not load or its Step 2 was edited. Say "you did not actually run any research, show me the prompts to run."

**Claude cannot find your files.** Confirm the folder is connected to the conversation, then confirm the Step 4 placeholders point at paths that exist. A placeholder left as `[Your round folder]` produces a polite failure that looks like a permissions problem and is not.

**Everything works but the output is thin.** Almost always the research prompts were run without the hypothesis and the name collision warning filled in. Those two fills are the difference between a summary and an interrogation.

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

If you use or adapt this material, please include:

Based on "Install the interview-research skill," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
