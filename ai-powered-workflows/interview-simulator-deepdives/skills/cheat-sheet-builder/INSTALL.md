>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the cheat-sheet-builder skill

This skill produces the single self contained HyperText Markup Language (HTML) page you glance at during a live interview, and it versions that page every time a mock run exposes something the page did not have.

You have two ways to install it.

**Option A, recommended.** Open `Install with Claude.md` in this folder, paste the prompt inside into Claude, and let Claude do the copying and customizing with you. It asks multiple choice questions about your tab structure, colour encoding, and versioning preferences, then configures the skill to match. Most people should take this path.

**Option B, manual.** Follow the five steps on this page. It takes about ten minutes.

---

## Prerequisites

1. **Claude Desktop with skills support.** Skills load from a folder on your computer at startup.
2. **A round folder**, one per round, named `[Company] - [Round Label]`, for example `Northwind Payments - Product Sense Round`.
3. **`templates/Cheat Sheet.html` from this kit**, reachable from that folder. The skill builds from the template rather than generating a page from scratch, because the template already carries the semantic encoding and the tab structure.
4. **A Story Bank with real content in it.** The hard prerequisite. The skill refuses to build a card from a resume line alone, and rightly so, because a card you cannot defend under a follow up looks identical on the page to one that has survived five runs.
5. **A way to read a web page while you talk.** A second monitor, a propped up tablet, or a phone. On one screen this artifact loses most of its value, worth knowing before you build it.

Optional but much better: a run log with at least one graded mock in it, from the interview-simulator skill. Without one, version one is an untested hypothesis and every card on it gets flagged as untested.

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

Create the `skills` folder if it does not exist.

A hedge worth taking seriously: this path has moved between application versions and could move again. If it is empty or missing after you install and restart, check your application's settings for a skills or extensions section, which usually names the directory it reads from. Believe the application over this page.

---

## Step 2: Copy the folder

Copy the entire `cheat-sheet-builder` folder, the one containing `SKILL.md`, into your skills directory. Copy the folder itself, not just the file inside it.

When you are done you should have:

```
skills/
  cheat-sheet-builder/
    SKILL.md
    INSTALL.md
    Install with Claude.md
```

The folder name must match the `name` field in the YAML frontmatter at the top of `SKILL.md`, which is `cheat-sheet-builder`.

---

## Step 3: Restart

Quit Claude Desktop completely and reopen it. Closing the window is usually not enough, because the application keeps running in the background. On Windows, quit from the system tray. On macOS, use Command and Q or quit from the menu bar.

Skills are read once at launch. A skill copied in while the application is running will not appear until the next start.

---

## Step 4: Customize the placeholders in SKILL.md

Open `SKILL.md` in a text editor and replace the square bracket placeholders. There are three:

- `[Your round folder]`. This changes every round, so either leave it as a placeholder and give Claude the path each session, or point it at a parent folder such as `C:\Interviews\` and let Claude ask which round you mean.
- `[Your Story Bank folder]`. Point at a shared Story Bank rather than a per round copy if you have one.
- `[Your Career Brain Trust folder]`, if you have one. Delete the line if you do not, rather than leaving a path that will not resolve.

Then make two decisions in the body of the file:

**The colour encoding table in Step 5.** The colours are arbitrary and changeable. What must not change is that each treatment means exactly one thing everywhere on the page. If you have a colour vision difference, change the palette now rather than fighting it later, and keep the word labels regardless, because they make the encoding survive a washed out screen share.

**The tab structure in Step 3.** The default is Opening, one tab per story card, Triggers, Numbers, Landmines, and Questions to ask them. Add one tab if your round type needs it, for example metrics for a product sense round. Resist adding more, because tab count is the quiet way a glance tool becomes a study document.

Then either fill in `## Customization: Guard rules (optional)` or delete the two illustrative examples, since that block is read on every run.

Do not edit the `description` field in the frontmatter. It keeps this skill from triggering on work belonging to its three siblings.

---

## Step 5: Verify the install

Start a new conversation, point it at your round folder, and type:

```
Build my cheat sheet from my Story Bank and the last mock run.
```

You should see Claude invoke the `cheat-sheet-builder` skill by name, read `_STATE.md`, the run log, and the Story Bank index, then present a sorted list of artifact gaps in four repair types, meaning missing content, missing routing, missing ending, and missing boundary. It should pause and ask which gaps to fix in this version before writing anything.

What you should NOT see is a finished HTML file appearing immediately with no questions asked, and you should NOT see it editing an existing version in place. Both mean the skill did not load.

---

## Renaming the skill

You can rename it. Two things must change together, and changing one without the other breaks the install silently.

1. The folder name inside your skills directory.
2. The `name` field in the YAML frontmatter at the top of `SKILL.md`.

Both must be lowercase with hyphens instead of spaces. `cheat-sheet-builder`, `glance-sheet`, and `one-pager-builder` are all valid. `Cheat Sheet Builder` and `cheat_sheet_builder` are not.

If you rename it, update the `Do NOT use this skill for` clause in the other three skills in this kit, because they name their siblings explicitly so the four do not answer each other's requests.

---

## Where to look if things break

**The skill never triggers.** Usually the application was not fully quit before restarting, or the folder landed in the wrong directory. Ask Claude "what skills do you have available" and check the list.

**It edits version one instead of copying it forward.** Step 7 is being skipped. The point of versioning is not backup, it is seeing which run caused which change and therefore whether a change helped. Say "copy it forward, never edit a shipped version" and check Step 7 is intact.

**The page keeps getting longer.** The golden rule in Step 4 is not firing. Every version should name what came out as well as what went in. If four versions have only added, you have a study document with tabs. Cut back to five beats per card and re-derive.

**Reasoning and question banks appear on the page.** Those belong in the simulator file. Have it move them rather than delete them, because the content is usually good and only in the wrong artifact.

**Cards appear that you cannot defend.** The skill built from a resume line, which it should refuse to do. Check the Story Bank actually has content, then rebuild.

**The colours stop meaning anything.** Somebody used green for something that was not verbatim. Once that happens every green box has to be read to be classified, which defeats the mechanism. Fix the offending block rather than adding a new colour for it.

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

Based on "Install the cheat-sheet-builder skill," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
