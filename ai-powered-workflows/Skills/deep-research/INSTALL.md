# Install: Deep Research skill

You have three ways to install it. Pick whichever fits.

**Option A (recommended): upload the package.** One file, no editing.
**Option B: Install with Claude.** Open `Install with Claude.md` in this folder and paste its prompt into a new chat.
**Option C: manual copy.** For Claude Code, or if you prefer files.

The skill needs no configuration. There are no paths or keys to fill in.

---

## Prerequisites

1. A Claude plan with Skills enabled (Claude desktop, claude.ai, or Claude Code).
2. Web search and web fetch turned on. The skill cannot research without them.
3. Sub-agents are strongly recommended. Where the platform does not support them, the skill still runs, but raw pages land in the main conversation and cost more.

---

## Option A: upload the package

1. Download `deep-research.skill` from this folder.
2. In Claude, open Settings and find the Skills section (usually under Capabilities).
3. Upload the file. If the uploader only accepts `.zip`, rename the file to `deep-research.zip` first. It is the same file.
4. Make sure the skill is toggled on.

Menu names move around between app versions. If you cannot find Skills, search the app's help for "upload a skill".

## Option C: manual copy

**Claude Code:** copy this whole folder to `~/.claude/skills/deep-research/` (all your projects) or `.claude/skills/deep-research/` inside one project.

**Claude desktop or claude.ai:** use Option A.

The folder name and the `name:` field at the top of `SKILL.md` must match. If you rename one, rename the other.

---

## Verify the install

Start a new chat and type:

> Do a deep research run on whether standing desks improve productivity.

Claude should restate the question neutrally, then either offer a Scan (if you did not name a depth) or ask a short set of scoping questions. It should **not** start searching before you say yes. If it answers straight from memory, the skill did not trigger: check it is toggled on, and that the `description:` field in `SKILL.md` is intact, because that field is what Claude uses to decide when to load the skill.

---

## Customizing

Open `SKILL.md` and scroll to **CUSTOMIZING**. The common changes are saving Deep runs to your notes app, adding source routing for your own field, and adding your house writing style.

---

## Where to look if things break

- **Skill never triggers:** say "deep research" or "/deep-research" explicitly. Casual phrasing like "look this up" is deliberately excluded.
- **Runs feel expensive:** check the cost note at the end of each run. Most questions are Scans. Let the skill talk you down a tier.
- **Report cites something that looks wrong:** that is what the verification pass is for, and it only runs on Standard and Deep. Ask for a Standard run, or ask Claude to verify that specific claim against the source.

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Deep Research skill" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
