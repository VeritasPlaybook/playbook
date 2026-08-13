>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the round-debrief skill with Claude

The assisted path. Instead of copying folders and editing placeholders yourself, you paste one prompt and Claude walks you through it, asks what it needs to know, and does the file work.

It takes about five minutes. Install this one early, before you need it. The value of a debrief collapses within about a day of the round, and the worst time to be editing a placeholder path is forty minutes after walking out of a panel with the interviewer's exact words still in your head.

If you would rather do it yourself, `INSTALL.md` in this folder has the manual steps.

---

## Before pasting

1. **Have this folder downloaded.** You need the `round-debrief` folder containing `SKILL.md` on your computer.
2. **Connect that folder to Claude**, so it can read `SKILL.md` and write the customized copy.
3. **Have `templates/Round Debrief.md` and `templates/HANDOFF.md` from the kit** somewhere Claude can read them.
4. **Know where your round folders live**, or decide now. One folder per round, named like `Northwind Payments - Hiring Manager Round`.
5. **Decide honestly whether you will answer a recall questionnaire the next day.** Roughly a third of a round comes back once you stop trying to remember it, but only if you answer the questions. If you know you will not, say so during install and the default becomes skip.
6. **Decide whether you record your rounds.** If you do, the mining step is dramatically better. Check your local rules and the other party's consent first.
7. **Start a fresh conversation.**

---

## The prompt

Copy everything inside the block below and paste it into Claude.

```
I want to install the round-debrief skill from the Build Your Own Interview Simulator kit.
The folder is connected to this conversation. Please read SKILL.md first, then help me install
and configure it.

Ask me these configuration questions before you change anything:

1. Where do my interview round folders live? Fixed path, or a parent folder you ask me about
   each session?
2. Where is my Story Bank, and is it shared across rounds or one per round?
3. Do I have a Career Brain Trust? If yes, where? If no, remove that reference.
4. Do I record and transcribe my interviews? If yes, where do the transcripts land, so the
   skill can look there rather than asking me to paste one.
5. What should the default be for the recall questionnaire, meaning tomorrow morning, in two
   days, or skip entirely? Recommend one based on my answer, and do not flatter me about it.
6. Do I want the debrief and the handoff written as two separate files, which is the default,
   or combined into one?
7. Do I have any guard rules to add, meaning standing corrections about how I habitually
   distort my own memory of a round, for example consistently underrating rounds immediately
   afterward?

Then do the following, in order:

A. Tell me exactly where my skills directory is on this operating system, and check whether
   it already exists.
B. Copy the round-debrief folder into that skills directory.
C. Edit the copy of SKILL.md in the skills directory so every square bracket placeholder is
   replaced with my real paths. Do not edit the original in the kit folder.
D. Apply my recall questionnaire default and my file structure choice.
E. Add my guard rules to the Customization section and delete the two illustrative examples
   if I gave you real ones.
F. Do not change the description field in the YAML frontmatter, and do not weaken the DRAFT
   ONLY warning in Step 8 or the rule against inventing a question I do not remember. Those
   two are the rules that protect the next round from being built on a guess.
G. Show me a summary of every change, with before and after for each placeholder.
H. Tell me to fully quit and restart Claude, and give me the exact trigger phrase to test with
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

Claude will tell you to fully quit and restart, because skills are read once at startup.

Then, after your next real round, start a conversation, point it at the round folder, and say "I just finished my interview at Northwind Payments, let us debrief it." The skill should ask for the round basics quickly and then ask for the question list, in the order the questions were asked, in the interviewer's own wording. It asks for the questions before it asks how you felt, because the order is the data and feelings reorder it.

The section that pays for the whole skill is what the interviewer said when answering your questions. That is where they stop performing and start describing their actual working life, and it is the specification for the next round.

Whatever the skill proposes for the next round is a draft. Nothing gets built until you say go, usually after you know who is on the next panel. When you do say go, the handoff file it wrote is what you paste into a fresh thread to bring it fully up to speed, and the loop starts again at the interview-research skill.

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

Based on "Install the round-debrief skill with Claude," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
