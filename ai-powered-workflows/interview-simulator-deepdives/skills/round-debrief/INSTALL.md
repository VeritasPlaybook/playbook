>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the round-debrief skill

This skill captures a real interview round while it is still fresh, mines what the interviewer accidentally told you, and turns both into a handoff file that seeds the next round's build.

You have two ways to install it.

**Option A, recommended.** Open `Install with Claude.md` in this folder, paste the prompt inside into Claude, and let Claude do the copying and customizing with you. It asks multiple choice questions about your recall habits, recording setup, and how aggressive you want the handoff to be, then configures the skill to match. Most people should take this path.

**Option B, manual.** Follow the five steps on this page. It takes about ten minutes.

---

## Prerequisites

1. **Claude Desktop with skills support.** Skills load from a folder on your computer at startup.
2. **A round folder** for the round you just sat, named `[Company] - [Round Label]`, for example `Northwind Payments - Hiring Manager Round`. The debrief and the handoff are written here.
3. **`templates/Round Debrief.md` and `templates/HANDOFF.md` from this kit**, reachable from that folder.
4. **`_STATE.md` in that folder.** The debrief writes locked decisions and accuracy guards into it, and those are what a fresh thread reads when the next round starts.
5. **Time, within a few hours of the round.** A real prerequisite, not a suggestion. The interviewer's answers to your questions are the most valuable intelligence in the process and they decay noticeably overnight.

Optional but much better: a recording and transcript of the round, which turns the mining step from reconstruction into a mechanical read. Check your local rules and the other party's consent before recording anything.

You do not need a simulator or a cheat sheet installed for this skill to work.

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

A hedge worth taking seriously: this path has changed between application versions and may change again. If it is empty or missing after you install and restart, look in your application's settings for a skills or extensions section, which normally names the directory it reads from. Believe the application over this page.

---

## Step 2: Copy the folder

Copy the entire `round-debrief` folder, the one containing `SKILL.md`, into your skills directory. The folder itself, not just the file inside it.

When you are done you should have:

```
skills/
  round-debrief/
    SKILL.md
    INSTALL.md
    Install with Claude.md
```

The folder name must match the `name` field in the YAML frontmatter at the top of `SKILL.md`, which is `round-debrief`.

---

## Step 3: Restart

Quit Claude Desktop completely and reopen it. Closing the window is usually not enough. On Windows, quit from the system tray. On macOS, use Command and Q or quit from the menu bar.

Skills are read once at launch, so a skill copied in while the application is running stays invisible until the next start.

---

## Step 4: Customize the placeholders in SKILL.md

Open `SKILL.md` in a text editor and replace the square bracket placeholders. There are three:

- `[Your round folder]`. This changes every round, so either leave it as a placeholder and give Claude the path when you start the debrief, or point it at a parent folder such as `C:\Interviews\` and let Claude ask which round you mean.
- `[Your Story Bank folder]`. Used when promoting locked answers and proposing stories to add or retire.
- `[Your Career Brain Trust folder]`, if you have one. Delete the line if you do not.

Then make two decisions in the body of the file:

**The recall questionnaire timing in Step 5.** The default offers tomorrow morning, in two days, or skip. If you know you will not answer one, set the default to skip rather than pretending. A questionnaire you ignore produces a debrief with holes in it that look filled.

**The DRAFT warning in Step 8.** Leave it. People soften it because the next round's shape looks obvious in the hour after a good interview. It looks obvious because you do not yet know who is on the next panel, and every build made on that guess gets thrown away. If you change it, make it stronger.

Then either fill in `## Customization: Guard rules (optional)` or delete the two illustrative examples, since that block is read on every run and this skill already asks for a lot of recall under time pressure.

Do not edit the `description` field in the frontmatter. It is written so this skill triggers on past tense descriptions of a round that already happened, and not on preparation requests belonging to its three siblings.

---

## Step 5: Verify the install

Start a new conversation, point it at your round folder, and type:

```
I just finished my interview at Northwind Payments. Let us debrief it.
```

You should see Claude invoke the `round-debrief` skill by name, tell you roughly how long this takes, ask for the round basics quickly, and then ask for the question list in the order the questions were asked, numbered, in the interviewer's own wording. It should ask for that list before asking how you felt it went.

What you should NOT see is Claude opening with encouragement, or asking how it went overall, or grouping your questions by topic once you give them. The order is the data, and reordering it destroys the most useful signal in the whole file.

---

## Renaming the skill

You can rename it. Two things must change together, and changing one without the other breaks the install silently.

1. The folder name inside your skills directory.
2. The `name` field in the YAML frontmatter at the top of `SKILL.md`.

Both must be lowercase with hyphens instead of spaces. `round-debrief`, `interview-debrief`, and `post-round-capture` are all valid. `Round Debrief` and `round_debrief` are not.

If you rename it, update the `Do NOT use this skill for` clause in the other three skills in this kit, since they name their siblings explicitly to stay out of each other's way.

---

## Where to look if things break

**The skill never triggers.** Usually the application was not fully quit before restarting, or the folder went into the wrong directory. Ask Claude "what skills do you have available" and check the list.

**The interview-simulator skill triggers instead.** The two overlap in vocabulary because both involve interview questions. Tense separates them, past for this one and future for the simulator. Say "I already had the interview, debrief it." If it keeps happening, one of the two descriptions was edited.

**It tidies your question list.** Reordering into topic groups or smoothing the interviewer's clumsy phrasing destroys the signal, and the real wording is what routes a story correctly next time. Say "keep their exact wording and the exact order" and check Step 1 is intact.

**It invents a question you do not remember.** This quietly poisons the next round, because a plausible reconstruction is indistinguishable from a real memory a week later. Delete the invented entry and log the item as a topic with the wording missing.

**It starts building the next round.** Step 8 is a draft and nothing gets built until you say go. Stop it. The panel for the next round is probably still unknown, which is exactly why the rule exists.

**Nothing lands in `_STATE.md`.** Locked answers and accuracy guards go there as well as into the debrief, because it is the file a fresh thread reads first. Check the file exists and the folder is connected to the conversation.

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

Based on "Install the round-debrief skill," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
