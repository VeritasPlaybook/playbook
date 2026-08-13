>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this template for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Start Here: your [ROUND LABEL] practice bot

*The front door. If you are building a simulator for someone else, rewrite this file in their name, and assume it is the only file they read. Keep it under two pages. Everything below is a working default you can edit.*

---

This folder is a self contained interview practice bot for your [ROUND LABEL] with [COMPANY]. It runs inside your assistant. Setup takes three minutes.

# Step 1: put this folder somewhere you can find it

Move the whole folder somewhere sensible, Documents is fine. Keep the files together, they reference each other by name.

# Step 2: create a project and connect this folder

Open your assistant, create a new project, name it `[COMPANY] [ROUND LABEL]`, and connect this folder so the assistant can read and write here. Connected, not uploaded. Write access matters, because it keeps its own notes between sessions.

# Step 3: start the bot

Pick one of the two simulator templates, `Simulator - Mock Kit.md` or `Simulator - Super Simulator.md`, copy it into your round folder, and rename the copy to `Simulator.md`. The boot command below looks for that exact name.

Then paste this into the chat and send it:

> Read `_STATE.md`, then `Simulator.md`, `Company and Role Brief.md`, and `Story Bank/INDEX.md`, and let's get started.

That is the whole boot command. Paste it again at the start of every new session, because a new chat starts with no memory of the last one. The files are the memory.

# Step 4: the intake conversation, once

The first thing the bot does is interview you, not the other way around. It fills in the parts of your Story Bank marked `NEEDS REAL DETAIL`, the specifics only you know: what was broken, what you decided, what the number was before and after.

Answer out loud if you can. Twenty five minutes here is the highest value part of setup. Nothing in your Story Bank was invented, so a line marked `NEEDS REAL DETAIL` is a question, not a claim.

# Step 5: run mocks

Say any of these to the bot:

- **"Run a mock"** starts a graded practice round. It asks two questions first: coaching or realistic mode, and short or full length.
- **"Rapid fire"** runs twelve to fifteen short questions with no teaching. Good for crispness.
- **"Deep dive on [topic]"** drills one area, escalating in difficulty.
- **"Grade only"** grades an answer you already gave without running a full round.
- **"Where am I"** reads the run log back to you: what you have covered, what you have not, and what you keep getting wrong.
- **"Update state"** writes everything down before you close the session. Do this every time.

# A few things that make this work better

**Say your answers out loud.** Dictate, or talk and transcribe. Typing lets you edit as you go, which hides the problems you are trying to find: running long, burying the point, trailing off without landing.

**Do not worry about typos.** The bot is told to assume garbled words are transcription artifacts and to grade what you meant, never how it came out on screen.

**Take one fix per run.** It gives you six scores, two things that worked, and one highest leverage fix. Take that one. A list of six corrections produces zero corrections.

**Feed it more research and it gets sharper.** The `Prompt Library` folder has prompts to run in a research tool. Paste results into `Company and Role Brief.md` or `Interviewer Dossier.md`, then tell the bot you updated them.

**It remembers between sessions, but only if you let it.** Everything it learns goes into `_STATE.md` and the run log at the bottom of `Simulator.md`. Close a session without saying "update state" and that session is gone.

# What is in this folder

| File | What it is |
|---|---|
| `_STATE.md` | The anchor. What is known, what is decided, what has been drilled. Read first, always |
| `Company and Role Brief.md` | What you know about the company, the role, and what you must not assert out loud |
| `Interviewer Dossier.md` | One per human in the room. Who they are and what they are really testing |
| `Story Bank/INDEX.md` | Routing file for your stories. Which cards exist and what each one proves |
| `Story Bank/` | The cards themselves. This is your material |
| `Simulator.md` | The bot: persona, question bank, rubric, run modes, run log |
| `Kickoff Prompt.md` | Paste this into a fresh thread to start a full mock |
| `Quick Drill Prompt.md` | The night before or the morning of. Short, surgical, no teaching |
| `Questions to Ask Them.md` | What you ask at the end, and why each one signals what it signals |
| `Cheat Sheet.html` | The only thing you look at during the real call. Open it on a second screen |
| `Round Debrief.md` | Fill this in within a few hours of the real round, while it is fresh |
| `HANDOFF.md` | Seeds the next round's folder |

# One warning

Some of the research files could be wrong. Research tools are confident and occasionally invent things, particularly about people. Anything unverified is listed in the **Do not assert** section of `Company and Role Brief.md`, with a safer phrasing. Stay inside that list.

Say "I do not know, and I do not think that is public" whenever it is true. It reads as senior. Bluffing does not, and it is detectable inside one follow up question.

The research makes you fast and hard to rattle. The judgment has to be yours.

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

If you use or adapt this template, please include:

Based on "Start Here," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
