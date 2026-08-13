>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the interview-simulator skill with Claude

The assisted path. Instead of copying folders and editing placeholders yourself, you paste one prompt and Claude walks you through it, asks what it needs to know, and does the file work.

It takes about five minutes. This skill has more configuration surface than the other three, because the rubric, the knowledge constraint, and the grading rules all change how a mock feels, so the assisted path is worth taking even if you would normally do it manually.

If you would rather do it yourself, `INSTALL.md` in this folder has the manual steps.

---

## Before pasting

1. **Have this folder downloaded.** You need the `interview-simulator` folder containing `SKILL.md` on your computer, not just open in a browser tab.
2. **Connect that folder to Claude**, so it can read `SKILL.md` and write the customized copy.
3. **Know where your interview round folders live**, or decide now. One folder per round rather than per company, named like `Northwind Payments - Executive Panel`.
4. **Know where your Story Bank is.** The one input that genuinely matters. Without stories carrying numbers you can defend under a follow up, the simulator becomes a generic question bot in a costume.
5. **Know what round type you are building for first.** Behavioural, product sense case, technical deep dive, hiring manager, or executive panel. The rubric is tuned to it.
6. **Decide how you will speak your answers.** Dictation, voice input, or talk and transcribe. Typing your practice answers produces a false positive every time, because typing lets you edit and speaking does not.
7. **Start a fresh conversation.**

---

## The prompt

Copy everything inside the block below and paste it into Claude.

```
I want to install the interview-simulator skill from the Build Your Own Interview Simulator kit.
The folder is connected to this conversation. Please read SKILL.md first, then help me install
and configure it.

Ask me these configuration questions before you change anything:

1. Where do my interview round folders live? Fixed path, or a parent folder you ask me about
   each session?
2. Where is my Story Bank, and is it shared across rounds or one per round?
3. Do I have a Career Brain Trust? If yes, where? If no, remove that reference.
4. What round type am I building for first, so you can tune rubric dimensions two through five?
5. What should the panel know about me? Options are that they have read my resume closely, know
   my current title and employer only, have seen a public profile and a referral note, or know
   nothing except that I passed the screen. Tell me which one you recommend and why before
   I choose.
6. Do I dictate my answers or type them? If I type, remove the transcription artifact rule.
7. Do I want the default of exactly one highest leverage fix per run, or more than one?
8. Do I have any guard rules to add, meaning standing corrections such as a number that belongs
   to one role and not another, or a credential that is past tense?

Then do the following, in order:

A. Tell me exactly where my skills directory is on this operating system, and check whether
   it already exists.
B. Copy the interview-simulator folder into that skills directory.
C. Edit the copy of SKILL.md in the skills directory so every square bracket placeholder is
   replaced with my real paths. Do not edit the original in the kit folder.
D. Tune the rubric dimensions to my round type and show me the six dimensions before you write
   them, including which two the round cannot forgive a low score on.
E. Apply my knowledge constraint choice, and remove the transcription artifact rule only if
   I said I type.
F. Add my guard rules to the Customization section and delete the two illustrative examples
   if I gave you real ones.
G. Do not change the description field in the YAML frontmatter, and do not weaken any of the
   rules in the RUN loop, meaning one question per turn, no hints, no praise openers, and
   deferred grading. Those four rules are the skill.
H. Show me a summary of every change, with before and after for each placeholder.
I. Tell me to fully quit and restart Claude, and give me the exact trigger phrase to test with
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

Claude will tell you to fully quit and restart. Do that, because skills are read once at startup.

Then start a new conversation, point it at your round folder, and say "run a mock." The clearest sign it is working is that it asks exactly two scoping questions, meaning coaching or realistic and short or full length, then asks one interview question and stops. The clearest sign something is wrong is two questions in one turn, a hint about which story to use, or a compliment on your answer.

The first run will feel worse than you expect. That is the point, and why the skill produces an artifact gap list at the end. Those gaps are the input to the cheat-sheet-builder skill, the natural next install.

Space your reps. Three runs across three days beats five in one evening, by a wide margin, and the run log is what makes run four harder than run two rather than identical.

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

Based on "Install the interview-simulator skill with Claude," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
