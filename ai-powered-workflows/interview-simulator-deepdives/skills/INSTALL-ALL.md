>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install all four skills

This is the default path. Most people should install all four skills, in one sitting, with one prompt.

Because they hand off to each other. Research produces the dossiers the simulator builds its personas from. The simulator produces the artifact gap list the cheat sheet builder consumes. The cheat sheet is the only thing you look at during the real round, and the debrief mines that round into the specification for the next one, restarting the loop at research. Installing one gives you a good tool. Installing all four gives you a system that compounds across a hiring loop, because each round's output is the next round's input.

Installing all four together is also less work than one at a time, because six configuration questions are shared and you answer them once instead of four times.

---

## What each one does

- **interview-research.** Builds the prompts for your deep research tools, ingests two passes, reconciles them into agreed, contradicted and unverified, and writes the Company and Role Brief, the Interviewer Dossiers, and the list of things you must not assert out loud.
- **interview-simulator.** Builds the simulator file, then runs graded mock interviews against it, one question per turn, no hints, graded only at the end, with a run log that makes run four harder than run two.
- **cheat-sheet-builder.** Turns your Story Bank and your mock run gaps into the single self contained HyperText Markup Language (HTML) page you glance at during the live call, and versions it every time a run exposes a hole.
- **round-debrief.** Captures the real round while it is fresh, mines what the interviewer gave away, and writes the handoff file that seeds the next round's build.

---

## The prompt

Copy everything inside the block below and paste it into a fresh Claude conversation, with the `Skills` folder from this kit connected.

```
I want to install all four skills from the Build Your Own Interview Simulator kit. The Skills
folder is connected to this conversation. It contains interview-research, interview-simulator,
cheat-sheet-builder and round-debrief, each with its own SKILL.md.

Read all four SKILL.md files first. Then install and configure them in this order:
interview-research, interview-simulator, cheat-sheet-builder, round-debrief.

Ask me the six shared configuration questions ONCE, up front, and reuse the answers across all
four skills:

1. Where do my interview round folders live? Fixed path, or a parent folder you ask me about
   each session?
2. Where is my Story Bank, and is it shared across rounds or one per round?
3. Do I have a Career Brain Trust? If yes, where? If no, remove that reference from all four.
4. Do I dictate my answers or type them?
5. Do I have any guard rules that apply across all four skills, meaning standing corrections
   such as a number that belongs to one role and not another, or a credential that is past tense?
6. What round am I preparing for right now, meaning company, round label, format and length,
   so you can tune anything round specific?

Then ask me only the skill specific questions that the shared answers do not already cover.
There are four of these and no more. Which research tools I have and whether I will run the
second cross validation pass. What the panel should know about me. Whether I want the default
colour encoding on the cheat sheet. What my default should be for the recall questionnaire
after a real round.

Then do the following, in order:

A. Tell me exactly where my skills directory is on this operating system, and check whether
   it exists.
B. Copy all four skill folders into it, keeping each SKILL.md inside its own folder.
C. Edit the copies in the skills directory so every square bracket placeholder is replaced
   with my real paths. Do not edit the originals in the kit folder.
D. Apply my skill specific answers to the right skills.
E. Add my guard rules to the Customization section of each skill, and delete the illustrative
   examples where I gave you real ones.
F. Do not change any description field in any YAML frontmatter. Those descriptions name each
   other explicitly so the four skills do not trigger on each other's work.
G. Do not weaken any rule written in capital letters in any of the four files.
H. Show me one summary table of every change across all four skills.
I. Tell me to fully quit and restart Claude, then give me the four trigger phrases to test
   each skill with and what I should expect to see for each.

Important rules while you do this work:

- Ask me questions as multiple choice with lettered options, and give me a copy and paste
  answer sheet at the end so I can reply quickly.
- Never produce a draft, edit a file, or take any action before I have confirmed my answers.
- No em dashes and no en dashes anywhere in your output.
- Define every acronym in full the first time you use it, then use the short form.
- If you cannot find a file or a folder, say so and ask me. Do not guess at a path.
```

---

## If you only want one

Sometimes you only need one piece. Use the table to pick, then open that skill's own `Install with Claude.md`.

| If this is your situation | Install this one | Why |
|---|---|---|
| You have a round booked and no idea who is interviewing you | interview-research | Turns names and a job posting into a posture you can prepare against |
| You know the round cold and just need reps | interview-simulator | The only one that produces practice rather than documents |
| Your stories are solid but you freeze reaching for the right one | cheat-sheet-builder | The trigger table fixes routing, which is usually the real problem |
| You just walked out of a round and round two is coming | round-debrief | The intelligence decays in about a day and this captures it |
| Your interview is tomorrow | interview-simulator | A rough mock you run twice beats a beautiful build finished at midnight |
| You have no interview booked at all | cheat-sheet-builder | It forces the Story Bank work, which is the only fully reusable layer |

You can add the others later. The skills read each other's files rather than each other's memory, so a skill installed in week three picks up everything the earlier ones wrote.

---

## After install

Fully quit Claude and restart. Skills are read once at startup, so a skill copied in while the application is running stays invisible until the next launch.

Then test all four with the trigger phrases Claude gives you. The most useful early check is the simulator: say "run a mock" and it should ask exactly two scoping questions, then ask one interview question and stop. If it asks two questions at once, hints at which story to use, or compliments your answer, something did not load correctly. Fix it before you build habits against a broken loop.

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

Based on "Install all four skills," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
