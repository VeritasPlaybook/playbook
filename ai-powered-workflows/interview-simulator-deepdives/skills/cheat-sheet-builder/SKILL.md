---
name: cheat-sheet-builder
description: Use this skill whenever the user wants to create, update, or version the single page HyperText Markup Language cheat sheet they will glance at during a live interview. Trigger phrases include "build my cheat sheet", "update the cheat sheet", "make me a one pager for the call", "the sheet did not have what I needed", "add a card to my cheat sheet", "version two of the cheat sheet", "what should I have in front of me on the call", "turn my stories into a glance sheet", and "fix the trigger table". Always trigger when the user is asking for the artifact they read on a second screen while talking, or asking to fold a mock run's artifact gaps back into that artifact, even if the exact wording differs. Do NOT use this skill for gathering research about the company or the interviewers, which is the interview-research skill, for building or running the mock itself, which is the interview-simulator skill, or for capturing what happened in a real round that has already been sat, which is the round-debrief skill.
---

# Cheat Sheet Builder skill

This skill turns a Story Bank, a simulator run log, and a list of artifact gaps into a single self contained HyperText Markup Language (HTML) file the user reads on a second screen while talking, then versions that file every time a mock exposes a hole.

The workflow has 8 steps. Run them in order. Steps 2, 4 and 6 pause for the user. Steps 1, 3, 5, 7 and 8 run without stopping.

The reframe that makes this skill work, and that most preparation methods miss: the mock is not the product. The mock is a test harness, and the cheat sheet is the thing under test. Every run should produce at least one note of the form "the sheet did not have what I needed here," and each note becomes an edit with a version number.

---

## Step 1: Read the run log and the Story Bank

Read, in this order:

1. `[Your round folder]/_STATE.md`, in full, including the artifact versions table.
2. The run log at the bottom of `[Your round folder]/Simulator.md`, newest entries first.
3. `[Your Story Bank folder]/INDEX.md`, in full.
4. The individual cards that the coverage map says the round will actually test, at most five at a time.
5. The current `[Your round folder]/Cheat Sheet.html`, if one exists.

If no run log exists yet, say so plainly and continue. A version one built before any mock is legitimate, just an untested hypothesis, and every card on it gets flagged as untested in Step 7.

If no Story Bank exists, stop and say so. This skill cannot invent stories. NEVER build a cheat sheet card from a resume line alone: a card the user cannot defend under a follow up is worse than a missing card, and on the sheet it looks identical to a card that has survived five runs.

---

## Step 2: Identify the artifact gaps from the last run

Pull the artifact gap list from the most recent run log entry. Each gap is a moment where the user reached for the sheet and the sheet did not have it.

Sort every gap into one of four repair types, because the repair differs and choosing the wrong one is how sheets bloat:

| Gap type | What it looks like in the log | The repair |
|---|---|---|
| Missing content | Reached for a number that was not on the sheet | Add it to the numbers box of the owning card |
| Missing routing | Told a good story that answered a slightly different question | Add a row to the trigger table, not a new card |
| Missing ending | Trailed off, did not land, kept going after the point | Write the closing line box for that card |
| Missing boundary | Overclaimed, or got defensive on a follow up | Write the honest limit line for that card |

Then look for gaps missing from the log because the user did not notice them. Two are common. A card never reached for across three runs is probably dead weight. A competency the round tests that no card owns is the highest priority gap in the file, and it is invisible in the run log, because you cannot log reaching for something you never had.

Present the sorted gap list and your proposed repairs.

PAUSE HERE. Wait for the user to confirm which gaps to fix in this version.

---

## Step 3: Build or update the sheet from the template

Start from `templates/Cheat Sheet.html`. One self contained file, no dependencies, no external stylesheet, no font download, no script that needs a network. It has to open instantly on a second screen with the wifi struggling.

The tab structure is fixed. Opening, one tab per story card, Triggers, Numbers, Landmines, Questions to ask them.

**Card anatomy is identical on every card**, six elements in the same order:

1. **The competency pill.** What this card owns, two or three competencies, at the top, so scanning tabs is scanning for what a story proves rather than what it is about.
2. **The headline box**, labelled SAY THIS FIRST, THEN STOP. One sentence, outcome in it, verbatim. The instruction to stop lives in the label because stopping is the part people fail.
3. **Five short beats.** Situation, what was actually broken, the call made and the option rejected, what shipped and who had to be moved, the result and what would be done differently. NEVER write these as prose. Prose gets read aloud, and reading aloud sounds like reading aloud.
4. **The closing line box.** Verbatim, the last sentence, then silence.
5. **The numbers box.** The metrics on their own, separated from the narrative, because sometimes only the number is needed and reading a story to extract one is exactly the failure this sheet prevents.
6. **The boundary box.** The honest limit line, pre written. For PM Jordan's chargeback card at Northwind Payments, "I did not own the model itself, I owned the decision thresholds and the appeal path." When the follow up lands, the user is not deciding whether to admit a limit, they are reading a line they chose while calm.

Only the headline and the closing line are verbatim. Everything between is improvised over a fixed skeleton.

NEVER add a section to one card for its own good reasons. A card that breaks the anatomy breaks the scan pattern for every other card on the sheet.

---

## Step 4: Enforce the golden rule, sharpen rather than extend

Every repair has two forms. You can add words, or make the existing words do the job. Default to the second.

The rule: **a card that is too long gets sharpened, never extended.** If a card already has five beats and the gap says a sixth idea is missing, replace the weakest of the five, or compress two beats into one to free the slot. Adding a sixth beat is how a glance tool becomes a study document across four versions, and the user will not notice, because each addition was justified.

Apply three hard limits:

- ONLY glanceable content. If a block cannot be found and used in two seconds while the user is mid sentence, it does not belong on the sheet.
- NO reasoning. Explanations, rationale, and "why this works" notes live in the simulator file or the Story Bank. On the sheet they are noise the eye has to skip past.
- NO question banks and NO rubrics. Those are the simulator's job. A cheat sheet with a question bank on it is a study document with tabs.

Length test, applied to every card before it ships: read it at speaking pace and time it. If a beat list takes more than about fifteen seconds to scan, it is too long, regardless of how good the content is.

Present each card you propose to sharpen, showing what comes out as well as what goes in.

PAUSE HERE. Wait for the user to approve the sharpen decisions.

---

## Step 5: Hold the semantic encoding

Every visual treatment means exactly one thing, and it means that thing everywhere on the sheet.

| Treatment | Means, always |
|---|---|
| Green bordered box | Say this out loud, word for word |
| Amber bordered box | The honest limit line, the thing you admit rather than dodge |
| Blue bordered box | Numbers |
| Purple pill | The competencies this card owns |
| Red band | Do not do this |
| Red bordered block | A landmine, meaning a thing that ends rounds |

The specific colours are arbitrary. The mapping never varying is not. The user is training a lookup reflex, and reflexes train on visual form rather than meaning. Under pressure the eye is doing shape and colour matching, not reading, and that is the entire mechanism behind two second retrieval.

ONE MEANING PER VISUAL TREATMENT. The first time green is used for something that is not verbatim, every green box on the sheet has to be read in order to be classified. That does not degrade one card, it converts the whole sheet back into a document, and the user will not notice, because they know what they meant.

Two rules protect the encoding:

- **No decorative styling.** If something needs emphasis and no existing class fits, it belongs inside an existing class or it does not belong on the sheet. A tenth treatment invented for one special case is followed by an eleventh.
- **Label every block in words as well as colour.** SAY THIS OUT LOUD, WORD FOR WORD. HONEST LIMIT LINE. NUMBERS. STOP. The redundancy is deliberate. It lets the encoding survive a bad monitor, a colour vision difference, a washed out screen share, and the version of the user who has not opened the file in four days.

---

## Step 6: Build or repair the trigger table

Left column, phrases the user might hear. Right column, which story to lead with. Eight to twelve rows, one screen, no scrolling.

This table exists because of a finding that takes several mock runs to see clearly. The most common failure is not a bad answer, it is a good answer to a slightly different question. The user hears "tell me about a time you influenced without authority," reaches for their best story, and that story is actually about prioritization under load. It lands, and gets marked as not answering the question, which in a real round reads as a candidate who does not listen.

Mid sentence, the user does not have the working memory to classify the question and begin speaking at once, and what gives is the classification. The table pre computes it so the only live work is speaking.

Build rows from three sources, in priority order: every routing gap from Step 2, every question actually asked in the run log, and the probes in the simulator's question bank that no row currently covers.

ONE STORY PER TRIGGER. If two cards could answer a phrase, the table decides which, not the user's instinct in the moment. A row with two answers on it is not a routing table, it is a menu, and reading a menu is the thing that was supposed to be pre computed.

PAUSE HERE. Wait for the user to confirm the routing decisions, because these are judgment calls that belong to them.

---

## Step 7: Version, never edit in place

NEVER edit version one. Copy it forward.

Save the new file as `[Your round folder]/Cheat Sheet v[N+1].html`, leaving the previous version untouched on disk. The point is not backup, it is seeing what changed and which run caused it, the only way to tell whether a change helped or just felt productive.

Then update the artifact versions table in `_STATE.md`:

| Artifact | Version | What changed and why |
|---|---|---|
| Cheat Sheet | v2 | Added closing line box to card 3 and two trigger rows. Run 2 artifact gaps. |

Record the causing run explicitly. "Tidied up" is not a valid entry. Every version exists because a specific run exposed a specific hole, and if you cannot name the run, the change was probably decoration.

**Mark every card as voice tested or untested.** Put it in the card's panel note, something short, "voice tested, run four" or "written, never said out loud."

Writing a card feels like finishing it, and it is not. A card that has never been spoken is an untested hypothesis, usually about thirty percent too long, usually with one beat the user cannot narrate. Under pressure the user reaches for whatever is on the sheet with equal confidence, and nothing about an unspoken card looks different from one delivered five times. So make it look different, then apply the rule: NEVER lead with a card flagged as written but never said out loud.

---

## Step 8: Report what changed and what it still cannot do

Tell the user, in a short block:

- The new version number and the file path.
- Every change, one line each, with the run that caused it.
- Every card still flagged untested, so they know what to drill next.
- Any competency the round tests that still has no card, which is the highest priority gap and the reason to build a new Story Bank card rather than stretch an existing one.
- Anything you refused to add, and why. Usually this is content that was true and useful and not glanceable, and it belongs in the simulator file or the Story Bank instead.

Then update the WHERE THIS IS banner in `_STATE.md` and stop.

---

## Customization: Guard rules (optional)

Guard rules are short standing corrections that this skill applies to every sheet it builds, without being reminded. They exist because sheet errors repeat, and a rule that fires while building is cheaper than a correction after a bad run.

Add yours to the block below. Two illustrative examples:

```
- Never put the Northwind Payments revenue figure on the same card as the earlier role's
  volume figure. Crossing them under pressure has already happened once.
- The certification is past tense. Any card or opening script that mentions it uses
  "was certified, 2022 to 2023" and never the present tense.
```

Keep this block short. It is read on every run, and a long block competes with the anatomy and encoding rules above it, which are the ones that protect the artifact. If it grows past roughly ten lines, promote older entries into the accuracy guards section of `_STATE.md`.

---

## Reference files

- Cheat sheet template, self contained HTML: `templates/Cheat Sheet.html`
- Anchor file: `[Your round folder]/_STATE.md`
- Run log, at the bottom of: `[Your round folder]/Simulator.md`
- Story Bank routing file: `[Your Story Bank folder]/INDEX.md`
- Story card template: `[Your Story Bank folder]/Card Template.md`
- Questions to ask them: `templates/Questions to Ask Them.md`
- Deep Dive on this artifact: `deep dives/07 - The Cheat Sheet.md`
- Deep Dive on the Story Bank: `deep dives/02 - The Story Bank.md`
- The user's Career Brain Trust, if they have one: `[Your Career Brain Trust folder]`

---

## Locked preferences for this skill (default; override during install)

- The sheet is a glance tool. Two second retrieval or it does not go on.
- Sharpen rather than extend. A long card loses a beat before it gains one.
- Never edit a shipped version. Copy it forward and record the causing run.
- One meaning per visual treatment, always, with a word label alongside the colour.
- Never build a card from material the user cannot defend under a follow up.
- Never invent a metric. A missing number is written as a gap, never as a plausible figure.
- No em dashes and no en dashes in any output.
- Define acronyms in full on first use, then use the short form.
