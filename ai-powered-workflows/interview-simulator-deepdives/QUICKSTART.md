>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Quickstart: An Interview Simulator in Ninety Minutes

This is the compressed version of [Build Your Own Interview Simulator](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md). Use it when the interview is tomorrow or the day after and there is no time to build the full system.

It produces a working practice bot and a one page cheat sheet. It skips the two pass research cross validation, the tagged question bank, the mode menu, and the multi round handoff. Those are what make the full version compound across a whole job search. For one interview in forty eight hours, this is enough.

If you have three or more days, close this file and read the main guide instead. The extra two hours is worth it.

---

# What you need before you start

Claude with Cowork mode, or any assistant that can read and write files in a folder you point it at. A deep research tool, or your assistant's own research mode. Your resume. Ninety minutes, ideally split across two sittings rather than one.

---

# Minute 0 to 10: Set up and answer five questions

Create a folder named `[Company] - [Round]`. Copy the `Templates` folder from this kit into it. Connect the folder to a project in your assistant.

Open `_STATE.md` and answer these five, guessing where you have to and marking every guess:

1. Who is in the room, and what is their function?
2. How long is it, and is it live or a take home?
3. What did the recruiter call this round?
4. What decision does it make? Screening, deep assessment, or final approval?
5. What are you most afraid they will ask?

If your recruiter is reachable, email them questions one through four right now, before you build anything else. The answer often arrives before you finish the build and it will change what you build.

---

# Minute 10 to 30: One research pass

Open `Prompt Library` and run two prompts in your research tool: `01 - Company and Role Deep Research` and `02 - Interviewer Deep Research`. Fill in the placeholders honestly, including the parts about your own gaps, because a research tool that knows your weak spots gives you a usable fit assessment rather than a flattering one.

Two things you must not skip even in the compressed version:

**Demand the split.** The output must separate what is verified with a source link from what is inferred. If it hands you a blended narrative, ask it again.

**Write the "do not assert" list.** Anything the research asserted without a source goes into `Company and Role Brief.md` under **Do not assert**, with the safe substitute phrasing beside it. This takes five minutes and it is the difference between sounding prepared and being confidently wrong about a stranger's career.

Then spend ten minutes using the product. Sign up. Walk the flow. Notice where it is awkward. No research tool can do this for you and it is worth more than another twenty minutes of reading.

---

# Minute 30 to 60: Five story cards

Open `Story Bank/INDEX.md` and the card template. You are building five cards, not nine.

Paste your resume into the assistant and say this:

> Read my resume and the round description in `_STATE.md`. Draft five Story Bank cards from the template, filling in only what my resume actually supports. Mark everything else `NEEDS REAL DETAIL` with a specific question. Do not invent numbers, outcomes, or decisions. Then interview me to fill the gaps, two to four questions at a time, and wait for my answer before asking more.

That instruction is doing three jobs. It gets you a scaffold fast, it refuses to fabricate, and it turns the gaps into a queue of questions rather than blanks you have to stare at.

Then answer the questions out loud, by dictation, for twenty five minutes. The parts you fumble while dictating are the parts you will fumble in the room, which is useful information for free.

Before you move on, check three things. Every card has a real number you could defend if pushed. At least one card is about a decision **you** made, not a project you were on. One card is a failure card that ends on the lesson and not on the grievance.

---

# Minute 60 to 75: Build and run the simulator

Copy `Simulator - Mock Kit.md` into your folder and fill in the persona: who they are, what they test, what wins them, what loses them. Four lines. Do not write an essay.

Then paste `Kickoff Prompt.md` into a fresh thread and run one mock, out loud, in realistic mode, short length.

The four rules that matter most are already in the template, and they are the reason it will not feel like a friendly chat: one question per turn then stop and wait, no hints and no telling you which story to use, grading at the end rather than after each answer, and ignoring transcription artifacts if you dictate.

Take exactly one fix from the grade. Not the whole list. One.

---

# Minute 75 to 90: Cheat sheet, then one more run

Say this to the assistant:

> Read the run log. Build me `Cheat Sheet.html` from the template, using what I actually struggled with in that run. Glance tool only: opening script, one headline line per story, my numbers, my honest boundary lines, a trigger table mapping question phrasings to which story to lead with, and the landmines. No reasoning, no question bank.

Then run one more mock with the sheet open beside you. This second run is the one that matters, because now you are testing the sheet, not whether you remember your stories.

If there is any time left after that, drill only the endings. Say the last sentence of each story out loud until it lands cleanly and you stop talking afterward. Trailing off is the most common and most fixable delivery failure.

---

# What you gave up, and what to add first if you get another day

The compressed version skips the second research pass, so your intelligence has an unknown error rate: stay inside the "do not assert" list and you will be fine. It skips question identifiers and tags, so run three will feel a lot like run one. It skips the mode menu, the coverage tracker, and the handoff file, so nothing carries into the next round.

If you find an extra day, add these in order. First, the second research pass and the reconciliation, because being wrong out loud is the worst outcome available to you. Second, four more story cards to close your coverage gaps. Third, the tagged question bank with a no repeat rule, which is what makes later reps harder instead of merely repetitive. Everything else can wait until the next company.

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

If you use or adapt this guide, please include:

Based on "Quickstart: An Interview Simulator in Ninety Minutes," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
