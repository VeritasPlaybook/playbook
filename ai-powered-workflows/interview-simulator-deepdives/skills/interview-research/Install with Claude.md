>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the interview-research skill with Claude

The assisted path. Instead of copying folders and editing placeholders yourself, you paste one prompt and Claude walks you through it, asks what it needs to know, and does the file work.

It takes about five minutes and produces a better result than the manual path, because the placeholders in `SKILL.md` decide whether the skill is useful, and answering questions about your setup is easier than guessing what a placeholder wants.

If you would rather do it yourself, `INSTALL.md` in this folder has the manual steps.

---

## Before pasting

1. **Have this folder downloaded.** You need the `interview-research` folder containing `SKILL.md` sitting somewhere on your computer, not just open in a browser tab.
2. **Connect that folder to Claude**, so Claude can read `SKILL.md` and write the customized copy. In Claude Desktop this means adding the folder to the conversation or project.
3. **Know where your interview folders live**, or decide now. One folder per round rather than per company, named like `Northwind Payments - Hiring Manager Round`. A parent folder such as `C:\Interviews\` also works.
4. **Know whether you have a Career Brain Trust and a Story Bank**, and where they are. If you have neither, that is fine, just be ready to say so.
5. **Know which research tools you have access to.** The skill assumes one, works better with two different ones, and will tell you honestly what it cannot verify with only one.
6. **Start a fresh conversation.** A clean thread avoids Claude carrying over assumptions from whatever you were doing before.

---

## The prompt

Copy everything inside the block below and paste it into Claude.

```
I want to install the interview-research skill from the Build Your Own Interview Simulator kit.
The folder is connected to this conversation. Please read SKILL.md first, then help me install
and configure it.

Ask me these configuration questions before you change anything:

1. Where do my interview round folders live? Should the skill use a fixed path, or a parent
   folder it asks me about each session?
2. Do I have a Career Brain Trust? If yes, where is it? If no, remove that reference.
3. Do I have a Story Bank? If yes, is it shared across rounds or one per round, and where is it?
4. Which deep research tools do I have access to, and will I be running the second
   cross validation pass or skipping it?
5. Do I want the skill to write the Interviewer Dossier as one file per person, or all
   interviewers in a single file?
6. Do I have any guard rules to add, meaning standing corrections such as a name collision
   with a public figure, or two companies with similar names I keep confusing?
7. Do I want the default confidence markers kept as VERIFIED, INFERRED and UNVERIFIED, or
   renamed to something I will read faster?

Then do the following, in order:

A. Tell me exactly where my skills directory is on this operating system, and check whether
   it already exists.
B. Copy the interview-research folder into that skills directory.
C. Edit the copy of SKILL.md in the skills directory so every square bracket placeholder is
   replaced with my real paths, based on my answers. Do not edit the original in the kit folder.
D. Add my guard rules to the Customization section, and delete the two illustrative examples
   if I gave you real ones.
E. Do not change the description field in the YAML frontmatter, because it is what keeps this
   skill from colliding with the other three skills in the kit.
F. Show me a summary of every change you made, with before and after for each placeholder.
G. Tell me to fully quit and restart Claude, and give me the exact trigger phrase to test with
   and what I should expect to see.

Important rules while you do this work:

- Ask me questions as multiple choice with lettered options, and give me a copy and paste
  answer sheet at the end so I can reply quickly.
- Never produce a draft, edit a file, or take any action before I have confirmed my answers.
- No em dashes and no en dashes anywhere in your output.
- Define every acronym in full the first time you use it, then use the short form.
- If you cannot find a file or a folder, say so and ask me. Do not guess at a path.
```

---

## What happens after install

Claude will tell you to fully quit and restart. Do that, because skills are read once at startup and a skill copied in while the application is running stays invisible.

Then start a new conversation, point it at a round folder, and say something like "I have an interview at Northwind Payments next week, help me research the company and the interviewers." You should see the skill trigger by name and immediately start asking about the round rather than producing a company summary from memory.

From there the skill runs eight steps. It confirms the round, builds the research prompts to run in your own tools, ingests two passes, reconciles them into agreed, contradicted and unverified, writes the Company and Role Brief and the Interviewer Dossiers, and writes the list of things you are not allowed to assert out loud with the safe phrasing to use instead.

The natural next step is the interview-simulator skill, which turns those artifacts into practice rounds. If you have not built your Story Bank yet, build it before the simulator, because it is the only layer in this kit that carries over to every interview you will ever do.

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

Based on "Install the interview-research skill with Claude," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
