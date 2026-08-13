>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Install the cheat-sheet-builder skill with Claude

The assisted path. Instead of copying folders and editing placeholders yourself, you paste one prompt and Claude walks you through it, asks what it needs to know, and does the file work.

It takes about five minutes and it is worth taking here because of the colour encoding. If you have a colour vision difference, or know a particular colour reads badly on your second monitor, change it now. Changing it during install is much easier than after four versions of a page already use it.

If you would rather do it yourself, `INSTALL.md` in this folder has the manual steps.

---

## Before pasting

1. **Have this folder downloaded.** You need the `cheat-sheet-builder` folder containing `SKILL.md` on your computer.
2. **Connect that folder to Claude**, so it can read `SKILL.md` and write the customized copy.
3. **Have `templates/Cheat Sheet.html` from the kit** somewhere Claude can read it. The skill builds from that template rather than generating a page from scratch, because the template already carries the encoding and the tab structure.
4. **Know where your Story Bank is.** The skill refuses to build a card from a resume line alone, which is correct, so it needs real story content to work from.
5. **Know how you will read the page during a call.** Second monitor, tablet, or phone. If everything happens on one screen, say so, because it changes how much should go on the page.
6. **Start a fresh conversation.**

---

## The prompt

Copy everything inside the block below and paste it into Claude.

```
I want to install the cheat-sheet-builder skill from the Build Your Own Interview Simulator kit.
The folder is connected to this conversation. Please read SKILL.md first, then help me install
and configure it.

Ask me these configuration questions before you change anything:

1. Where do my interview round folders live? Fixed path, or a parent folder you ask me about
   each session?
2. Where is my Story Bank, and is it shared across rounds or one per round?
3. Do I have a Career Brain Trust? If yes, where? If no, remove that reference.
4. What device will I read the cheat sheet on during a live call, and how much screen space
   will it get?
5. Do I want to keep the default colour encoding, meaning green for verbatim, amber for the
   honest limit line, blue for numbers, purple for competency pills, red band for do not do
   this, and red border for a landmine? If I have a colour vision difference or a preference,
   propose an alternative palette that keeps one meaning per treatment.
6. Do I want the default tab structure, meaning Opening, one tab per story card, Triggers,
   Numbers, Landmines, and Questions to ask them, or do I need one extra tab for my round type?
7. Where should new versions be saved, and what naming pattern do I want, for example
   Cheat Sheet v2.html?
8. Do I have any guard rules to add, meaning standing corrections such as two numbers that must
   never share a card, or a credential that must always be written in the past tense?

Then do the following, in order:

A. Tell me exactly where my skills directory is on this operating system, and check whether
   it already exists.
B. Copy the cheat-sheet-builder folder into that skills directory.
C. Edit the copy of SKILL.md in the skills directory so every square bracket placeholder is
   replaced with my real paths. Do not edit the original in the kit folder.
D. Apply my colour encoding and tab structure choices, and keep the word labels on every block
   regardless of what I chose for colours.
E. Add my guard rules to the Customization section and delete the two illustrative examples
   if I gave you real ones.
F. Do not change the description field in the YAML frontmatter, and do not weaken the golden
   rule that a long card gets sharpened rather than extended, or the rule that a shipped version
   is copied forward rather than edited. Those two rules are what keep the page usable.
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

Then start a new conversation, point it at a round folder, and say "build my cheat sheet from my Story Bank and the last mock run." You should see the skill read the run log and the Story Bank, then present a sorted list of artifact gaps in four repair types, meaning missing content, missing routing, missing ending, and missing boundary. It should pause and ask which to fix before it writes anything.

Version one is an untested hypothesis. Every card on it gets flagged as untested, and the rule is that you never lead with a card flagged as written but never said out loud. The page only becomes good after mocks have broken it a few times, which is why this skill pairs with the interview-simulator skill rather than standing alone.

One habit is worth building on day one. When a run exposes a hole, fix the page, not your memory. The note "I should remember that number" changes nothing. The edit does.

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

Based on "Install the cheat-sheet-builder skill with Claude," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
