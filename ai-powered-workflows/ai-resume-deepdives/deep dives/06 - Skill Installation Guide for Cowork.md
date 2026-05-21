>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Skill Installation Guide for Cowork

This deep dive covers the conceptual layer that applies to any Cowork skill. The main guide referenced two specific skills (`resume-builder` and `update-brain-trust`) in [Step 5](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md#step-5-install-the-skills) and pointed you here for the install details. Each of those skill packages ships with its own per-skill install instructions (`INSTALL.md` and `Install with Claude.md`). This deep dive does not duplicate those files; it covers what is true about every Cowork skill so the per-skill instructions make sense.

By the end of this deep dive you should understand: how Cowork skills work, what the `SKILL.md` file does and what its frontmatter does, where Cowork looks for skill folders on your filesystem, the generic install pattern that applies to any skill, how trigger phrases work, the most common install errors and how to fix them, and how to customize a skill once it is installed. At the bottom, there is a short list of the two skills shipped with this guide, with direct links to their per-skill install files.

---

# How Cowork Skills Work

A Cowork skill is a reusable workflow Claude can run on demand. Conceptually a skill is two things at once: a recognizable pattern Claude triggers on (the description that decides when the skill applies) and a multi-step workflow Claude follows when it triggers (the body of the skill file).

In practice this means you do not have to remember and re-paste a long prompt every time you want to do the same kind of work. You install the skill once. After that, you describe the situation in your own words ("let us apply to Acme Fintech for the Director of Product role") and Cowork matches your description against the installed skills, picks the one that fits, and runs its workflow.

The benefit compounds across applications. A skill is the difference between thinking "what was that prompt I had for tailoring a resume?" every Monday morning, and just saying "let us apply to Acme Fintech" and having Claude take it from there. The skill is the leverage; you only have to set it up once.

A skill is not a black box. You can read its workflow, edit its instructions, add your own steps, swap default settings, and lock new guard rules in. The skill file is plain Markdown. There is no compiled binary, no opaque dependency, no vendor lock-in. If you can read Markdown, you can read and modify a skill.

A skill is also not the same thing as a chat. A chat is one-off; a skill is a reusable workflow. A chat ends when you close the tab; a skill persists until you uninstall it. Anything you find yourself doing more than twice in chats is a candidate for becoming a skill.

---

# The SKILL.md File

Every Cowork skill lives in its own folder, and every skill folder has a file named `SKILL.md` at its root. This file is the skill itself. It has two parts: the frontmatter at the top, and the workflow in the body.

**The frontmatter.** A small YAML block at the very top of the file, bracketed by triple dashes, defining:

- `name`: the canonical name of the skill (for example, `resume-builder` or `update-brain-trust`). Lowercase with hyphens.
- `description`: a one or two paragraph description that explains what the skill does, when it should trigger, and what kinds of user requests it should match. This description is the most important part of the skill because it is what Cowork uses to decide whether to invoke the skill on a given user request.

A typical frontmatter block looks like:

```
---
name: example-skill
description: |
  Use this skill when the user asks you to do X. Triggers include 
  phrases like "do X", "help me with X", "I need X". Always use this 
  skill in those contexts, even if the user does not say "skill". 
  Do NOT use this skill for unrelated tasks like Y.
---
```

A few things to notice. The description starts with "Use this skill when," which is the canonical Cowork pattern. The description lists the trigger phrases the user is likely to actually say. The description also includes a "do NOT" clause to keep the skill from triggering on unrelated work. All three of these matter. A description that is too vague triggers on everything (annoying). A description that is too narrow triggers on nothing (useless). A description without a "do NOT" clause sometimes collides with similar skills.

**The body.** Below the frontmatter, the workflow itself, written in plain Markdown. The body explains what the skill should do step by step, what files to read, what clarifying questions to ask, what outputs to produce, and where to save them. The body can be as short as a few paragraphs or as long as a small handbook, depending on the complexity of the workflow.

The body can also reference helper files in the same skill folder. A `scripts/` subfolder holds executable helper scripts (for example, a Python script that builds a Word document). A `references/` subfolder holds reference documents the skill loads on demand (for example, a style guide or a template). A `evals/` subfolder holds evaluation scripts that test the skill against known inputs.

The two skills in this guide use this structure. Each has a `SKILL.md` at the root, plus one helper file: `scripts/example_build.py` in the `resume-builder` skill, and `evals/README.md` in the `update-brain-trust` skill.

---

# Where Cowork Looks for Skill Folders

Cowork looks for installed skills in a specific directory on your filesystem. The exact path depends on your operating system and your Cowork version, but on most installations it is something like:

```
[OS user profile]/Claude/skills/
```

or, for the per-project skills directory:

```
[Your Cowork project folder]/.claude/skills/
```

Each skill is one folder inside that directory. The folder name should match the `name` field in the skill's frontmatter (`resume-builder`, `update-brain-trust`, and so on). Cowork scans these directories at thread start and indexes every skill it finds. The skill is then available for triggering in any conversation in that Cowork project (or globally if installed in the user-profile directory).

Two install scopes to know about:

- **User-scope skills** (installed in the OS-level Claude directory): available in every Cowork thread you open on this computer. Good for skills you use across many projects.
- **Project-scope skills** (installed in the `.claude/skills/` subfolder of a specific project): available only in that specific Cowork project. Good for skills with project-specific configuration or guards.

For the two skills shipped with this guide, install them at user scope unless you have a specific reason to scope them to a single project. The `resume-builder` and `update-brain-trust` skills are designed for any job search project, so global availability is the default.

---

# The Generic Install Pattern

Every Cowork skill installs the same way. The per-skill `INSTALL.md` file in each skill folder walks the specific paths and trigger phrases for that skill. The pattern below applies to any skill you ever install.

**Step 1: Download the skill folder.** The skill ships as a folder containing `SKILL.md` and any helper files. You can clone the repository that hosts it, download a specific folder, or pull the files directly from a release. The folder must include `SKILL.md` at its root or Cowork will not see it.

**Step 2: Place the folder in your Cowork skills directory.** For user scope, copy the folder into your OS-level Claude skills directory. For project scope, copy it into `.claude/skills/` inside your Cowork project. The folder name should match the skill's `name` field.

**Step 3: Restart Cowork or open a new thread.** Cowork indexes skills at thread start. If you copy a skill in mid-conversation, you may need to start a new thread before the skill becomes available.

**Step 4: Verify the install.** Ask Claude in a fresh thread: "What skills do you have available?" Claude should list the installed skill by name. If it does not appear, see the common errors section below.

**Step 5: Test the trigger.** Use a phrase you would naturally say, drawn from the skill's description. If the skill is `resume-builder`, try "let us apply to Acme Fintech for the Director of Product role." If Claude invokes the skill, you are done. If Claude tries to help conversationally without invoking the skill, the description's trigger phrases are not matching your phrasing. You can either rephrase, or edit the skill description to include more of your natural phrasings.

The whole install is a copy operation plus a verification. There is no compilation step, no dependency install, no configuration UI. The skill file is the skill.

---

# How Trigger Phrases Work

Trigger phrases are how Cowork decides whether to invoke a skill on a given user request. They are not exact matches; they are descriptions of the kinds of phrasings the skill should respond to. Cowork uses the model itself to do the matching, not a hard regex.

In the skill's `description` field, the trigger phrases live as a list of natural phrasings the user might use. For example, the `resume-builder` skill includes phrases like "I want to apply for X role," "build a resume for X," "tailor a resume for X," "help me apply to X," and "let us apply to X." A user does not have to use any of those exact phrases; they just have to say something close enough that Cowork's matching pass recognizes the intent.

The shape of a strong trigger phrase list:

- Five to ten natural phrasings the user might actually say.
- A short "always use this skill in [context]" reinforcement.
- A "do NOT use this skill for [context]" exclusion to prevent collisions with similar skills.

The trigger phrases also reflect how you actually talk. If you tend to say "let us" instead of "let's," put "let us" in the description so the matching is robust. If you usually start applications by saying "I found a job at X," put that phrasing in the trigger list. The skill should match your real language patterns, not the language patterns a generic user would use.

You can update the trigger phrases at any time by editing the `SKILL.md` file's description field. Save the file, restart Cowork or open a new thread, and the updated triggers take effect.

---

# Common Errors and Fixes

A handful of failure modes show up across most readers when installing skills for the first time. Each one is fixable in a minute or two.

**The skill does not appear when you ask "What skills do you have available?"** The folder is probably not in the right directory. Verify the folder is in the OS-level Claude skills directory (for user scope) or the project's `.claude/skills/` directory (for project scope). Verify the folder contains a file named exactly `SKILL.md` at its root. Restart Cowork or open a new thread after fixing.

**The skill appears but does not trigger when you say the trigger phrase.** The skill's description has trigger phrases that do not match your natural phrasing. Open `SKILL.md`, look at the trigger phrases in the description field, and either rephrase your request to match the listed phrases or add your natural phrasing to the description.

**The skill triggers but stops with an error mid-workflow.** The skill is trying to read a file that does not exist (often a Career Brain Trust file that has not been built yet) or call a helper script that is not installed. Check the skill's workflow body to see what it expects in your filesystem, and build or install the missing piece.

**Two skills trigger on the same request.** The descriptions are colliding. Edit one or both descriptions to include "do NOT use this skill for [the other skill's purpose]" clauses. Re-test.

**The skill triggers on requests it should not respond to.** The description is too broad. Tighten the description to be more specific about when the skill applies, and add "do NOT use this skill for X" exclusions.

**The skill folder name does not match the `name` field in the frontmatter.** Cowork will still find the skill, but the indexing is cleaner if the folder name and the `name` field match. Rename one or the other to match.

**The frontmatter is malformed (broken Yet Another Markup Language, or YAML).** A missing colon, a stray quote, or a tab where a space should be will cause Cowork to fail to parse the skill. The error usually shows up as "skill failed to load" rather than "skill not found." Open the file, look at the frontmatter block at the top, and check for syntax errors. Online YAML validators can help if you are not sure.

**The skill loads but the workflow body is empty.** Open `SKILL.md` and verify the body has actual instructions below the frontmatter. An empty body means the skill triggers but does nothing.

If a fix is not in the list above, the per-skill `INSTALL.md` file usually has a "troubleshooting" section with skill-specific issues. Check there before searching forums or filing issues.

---

# Customizing Skills

A skill you installed is yours to modify. There is no central registry that updates if you change a local copy. Customization happens in three places:

**In the skill's frontmatter description.** Edit the description to add trigger phrases that match your natural language, or to add "do NOT" exclusions that prevent collisions with similar skills. Restart Cowork or open a new thread for changes to take effect.

**In the skill's workflow body.** Edit the body to change default settings (the number of bullets per role, the resume length curve, the file naming pattern), add new steps to the workflow, or remove steps you do not want. The body is plain Markdown; treat it like editing any other document.

**In helper files in the skill folder.** If the skill references a `scripts/` or `references/` folder, the contents of those folders are also yours to modify. Replace a template, swap a script, update a reference. The skill picks up the changes the next time it runs.

A common customization for the two skills shipped with this guide: adding your own guard rules to the `_session rules/` folder in your Career Brain Trust (covered in [Deep Dive 1](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/deep%20dives/01%20-%20The%20Career%20Brain%20Trust%20Structure.md)) so the skills honor your specific constraints on every run. You do not need to modify the skill itself to do this; the skill reads `_session rules/` files automatically as long as they live in the right place.

A rule of thumb. Before modifying the skill itself, ask whether the change belongs in your Career Brain Trust (content), in a `_session rules/` file (constraint), or in `SKILL.md` (default behavior). Most of the time, the answer is in the Brain Trust or in the session rules. The skill itself rarely needs to change.

---

# Skills Covered by This Guide

Two skills ship with this guide, each in its own folder with a `SKILL.md`, an `INSTALL.md`, an `Install with Claude.md`, and one supporting file. The per-skill `INSTALL.md` is the canonical install reference. The `Install with Claude.md` is the AI-assisted version that walks you through the install conversationally.

**The `resume-builder` skill.** Tailors a combined cover letter and resume for a specific Job Description, drawing from your Career Brain Trust. Folder: `skills/resume-builder/`.

- [Skill folder](https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/ai-resume-deepdives/skills/resume-builder/)
- [INSTALL.md (manual install)](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/skills/resume-builder/INSTALL.md)
- [Install with Claude.md (AI-assisted install)](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/skills/resume-builder/Install%20with%20Claude.md)

**The `update-brain-trust` skill.** Closes the loop after every application by folding new framings, metrics, and cover letter hooks back into your Career Brain Trust. Folder: `skills/update-brain-trust/`.

- [Skill folder](https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/ai-resume-deepdives/skills/update-brain-trust/)
- [INSTALL.md (manual install)](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/skills/update-brain-trust/INSTALL.md)
- [Install with Claude.md (AI-assisted install)](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/skills/update-brain-trust/Install%20with%20Claude.md)

The recommended order is to install `resume-builder` first, run it once on a test Job Description, then install `update-brain-trust`. That way you have a tailored application to feed into the `update-brain-trust` skill on its first run, which makes the loop step real instead of abstract.

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

If you use or adapt this deep dive, please include:

Based on "Skill Installation Guide for Cowork," part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md
License: CC BY 4.0
