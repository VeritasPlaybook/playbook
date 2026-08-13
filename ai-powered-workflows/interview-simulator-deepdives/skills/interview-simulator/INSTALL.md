>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the interview-simulator skill

This skill builds a mock interview simulator for one specific round, then runs graded practice interviews against it and writes the results into a run log that makes the next run harder than the last one.

You have two ways to install it.

**Option A, recommended.** Open `Install with Claude.md` in this folder, paste the prompt inside into Claude, and let Claude do the copying and customizing with you. It asks multiple choice questions about your round, build size, and grading preferences, then configures the skill to match. Most people should take this path, because this skill has more configuration surface than the other three and the defaults are opinionated.

**Option B, manual.** Follow the five steps on this page. It takes about ten minutes.

---

## Prerequisites

1. **Claude Desktop with skills support.** Skills are read from a folder on your computer at startup. If your version has no skills folder, this skill will not load.
2. **A round folder**, one per round rather than per company, named `[Company] - [Round Label]`, for example `Northwind Payments - Executive Panel`.
3. **The templates from this kit** in that folder, in particular `_STATE.md`, `Simulator - Mock Kit.md`, and `Simulator - Super Simulator.md`.
4. **The Question Banks folder** from this kit, somewhere Claude can read it. The tagged probes are what stop run six from being identical to run two.
5. **A Story Bank**, even a rough one. This is the prerequisite that blocks you. Without stories carrying defensible numbers, the simulator becomes a generic question bot in a costume.
6. **A way to speak your answers.** Typing your practice answers produces a false positive every time, because typing lets you edit and speaking does not.

Optional but much better: a Company and Role Brief and one Interviewer Dossier per person, produced by the interview-research skill.

---

## Step 1: Locate your skills directory

On Windows, open File Explorer and paste this into the address bar:

```
%APPDATA%\Claude\skills\
```

On macOS, open Finder, press Command and Shift and G together, and paste:

```
~/Library/Application Support/Claude/skills/
```

Create the `skills` folder if it is not there.

A hedge worth taking seriously: this location has changed between application versions and may change again. If the path above is empty or missing after you install and restart, look in your application's settings for a skills or extensions section, which normally names the exact directory it reads from. Believe the application over this page.

---

## Step 2: Copy the folder

Copy the entire `interview-simulator` folder, the one containing `SKILL.md`, into your skills directory. The folder, not just the file.

When you are done you should have:

```
skills/
  interview-simulator/
    SKILL.md
    INSTALL.md
    Install with Claude.md
```

The folder name must match the `name` field in the YAML frontmatter at the top of `SKILL.md`, which is `interview-simulator`.

---

## Step 3: Restart

Quit Claude Desktop completely and reopen it. Closing the window is usually not enough. On Windows, quit from the system tray. On macOS, use Command and Q or quit from the menu bar.

Skills load once at startup. A skill copied in while the application is running is invisible until the next launch.

---

## Step 4: Customize the placeholders in SKILL.md

Open `SKILL.md` in a text editor and replace the square bracket placeholders. There are three:

- `[Your round folder]`. Since this changes every round, either leave it as a placeholder and give Claude the path each session, or point it at a parent folder such as `C:\Interviews\` and let Claude ask which round you mean.
- `[Your Story Bank folder]`. Point at a shared Story Bank rather than a per round copy. It is the only fully reusable artifact in this kit and it improves every round, which only happens if there is one of it.
- `[Your Career Brain Trust folder]`, if you have one. Delete the line if you do not.

Then make three decisions in the body of the file, because these are the ones that change how the mock feels:

**The knowledge constraint in Step 4.** Tick exactly one box. The honest default for most rounds is "know my current title and employer only." Ticking "have read my resume closely" feels good and removes the exact skill you need to practise.

**The rubric dimensions in Step 5.** Dimensions one and six are fixed as Structure and Communication and presence. Tune two through five to your round type, using the suggested sets in the skill.

**The transcription artifact rule in the locked preferences.** Delete it if you type, keep it if you dictate. Left in when you type, it makes the grader too forgiving about wording.

Then either fill in `## Customization: Guard rules (optional)` or delete the two illustrative examples, because that block is read on every run including every mock.

Do not edit the `description` field in the frontmatter. It is written to be distinct from the other three skills so they do not trigger on each other's work.

---

## Step 5: Verify the install

Start a new conversation, point it at your round folder, and type:

```
Run a mock.
```

You should see Claude invoke the `interview-simulator` skill by name, read `_STATE.md`, report which inputs exist and which are missing, and then ask exactly two scoping questions, meaning coaching or realistic, and short or full length. After you answer, it should ask one interview question and stop.

The clearest sign it is working is that it stops after one question. The clearest sign it is not is a reply containing two questions, a hint about which story to use, or a compliment on your answer. Any of those three means the skill did not load or its rules were edited.

---

## Renaming the skill

You can rename it. Two things must change together, and changing one without the other breaks the install quietly.

1. The folder name inside your skills directory.
2. The `name` field in the YAML frontmatter at the top of `SKILL.md`.

Both must be lowercase with hyphens instead of spaces. `interview-simulator`, `mock-runner`, and `practice-round` are all valid. `Interview Simulator` and `interview_simulator` are not.

If you rename it, update the `Do NOT use this skill for` clause in the other three skills in this kit, because they name their siblings explicitly to stay out of each other's way.

---

## Where to look if things break

**The skill never triggers.** Usually the application was not fully quit before restarting, or the folder went into the wrong directory. Ask Claude "what skills do you have available" and check the list.

**It asks two questions in one turn.** This is the failure that ruins runs, because you will quietly answer the easier one and never notice. Say "one question per turn, then stop." If it recurs, the rule in Step 7 was edited, or the simulator file has grown large enough to be truncated and its worked answers need moving into a separate file.

**It tells you which story to use.** The no hints rule is not being read, same causes as above. Scaffolding hides the defects the run exists to find, so fix this rather than tolerate it.

**It grades after every answer.** Deferred grading is the most commonly lost rule, usually because a mid run request for feedback moved it into a coaching posture. Restart the run and pick realistic mode.

**It flags your garbled words.** The transcription artifact rule was deleted or never applied. Put it back, or the grader spends its feedback budget on your microphone.

**Run six feels identical to run two.** The probe identifiers were dropped when the bank was assembled, so the no repeat rule has nothing to work with. Rebuild the bank with identifiers and tags intact.

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

Based on "Install the interview-simulator skill," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
