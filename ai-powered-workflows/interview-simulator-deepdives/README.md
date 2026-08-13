>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this material for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Interview Simulator Kit

Everything that supports [Build Your Own Interview Simulator](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md): the templates you copy, the research prompts you run, the question banks you pull from, the four skills, the deep dives, and two fully worked examples.

Read the main guide first. This folder makes little sense on its own.

---

# Where to start

**In a hurry, interview in the next day or two:** read `QUICKSTART.md`, copy `templates/` into a new folder, and build the ninety minute version.

**Building it properly:** read the main guide, then copy `templates/` and work through Steps 1 through 10.

**Want to see it finished before you build one:** open `Examples/`. Two complete builds, one for a product manager in a hiring manager round, one for a backend engineer in a technical panel. Both are fictional, and both include a run log excerpt showing real weakness found and fixed rather than a flattering demo.

**Building one for a friend:** read Deep Dive 9 first.

---

# What is in here

| Folder | What it holds |
|---|---|
| `QUICKSTART.md` | The ninety minute version, for when the interview is tomorrow |
| `templates/` | Blank files you copy into your own round folder. Start here |
| `templates/00_START_HERE.md` | The onboarding file for a finished round folder. Rewrite it if you are building this for someone else |
| `Prompt Library/` | Four deep research prompts and one recruiter intake email, plus a routing file saying which ones you need to run |
| `Question Banks/` | Tagged probes for six round types plus a recruiter screen appendix |
| `skills/` | Four Claude skills that automate the research, the mock, the cheat sheet, and the debrief. Install all four with `skills/INSTALL-ALL.md` |
| `deep dives/` | Eleven chapters on why the system is shaped the way it is |
| `Examples/` | Two complete worked builds |

---

# Downloads

GitHub has no button for downloading a single folder, which makes the instructions above more annoying than they should be. So the pieces you copy are also packaged on the [latest release](https://github.com/VeritasPlaybook/playbook/releases/latest).

**The four skills**, as `.skill` files. Download one and open it to install into Claude, instead of copying a folder by hand: `interview-research.skill`, `interview-simulator.skill`, `cheat-sheet-builder.skill`, `round-debrief.skill`.

**Three starter packs**, as zip files. `starter-blank-templates.zip` is the empty `templates/` folder, pre-wired, and is where most people should start. `starter-pm-jordan.zip` and `starter-engineer-alex.zip` are the two worked examples, ready to unzip and run.

The folders in this repository are the source of truth. The packaged files are built from them, so read the folders if you want to see exactly what a skill does before you install it.

---

# The deep dives

| Guide | What It Covers |
|---|---|
| 01 - The Intelligence Layer | The five research prompts, two pass cross validation, the reconciliation buckets, and the "do not assert" list |
| 02 - The Story Bank | The ten element checklist, the interrogation method, coverage mapping, metric hardening, and how it sits on the Career Brain Trust |
| 03 - The Interviewer Dossier | Turning a named person into a posture, fact versus inference, name collisions, and the quiet question in their head |
| 04 - Simulator Architecture | Mock Kit versus Super Simulator, persona construction, tagged question banks, the mode menu, and the remix engine |
| 05 - State, Handoff, and Multi-Round Campaigns | The anchor file, locked decisions, run logs, debriefs, and how one round seeds the next |
| 06 - Scoring and the Feedback Loop | The six dimension rubric, the one fix rule, fix lifecycle tracking, and detecting overcorrection |
| 07 - The Cheat Sheet | Why HyperText Markup Language (HTML) and not markdown, the semantic classes, trigger tables, and version discipline |
| 08 - Round Types and What Each One Tests | Hiring manager, behavioural, product sense and case, technical deep dive, executive panel, peer, plus the recruiter screen appendix |
| 09 - Building It for Someone Else | The onboarding file, the intake conversation, placeholders as instructions, and the authorship handoff |
| 10 - Running It Outside Claude | ChatGPT Projects, and what changes when the assistant cannot write to your folder |
| 11 - What I Learned, Expanded | The lessons from the main guide, with the runs that produced them |

---

# A note on the examples

Every person, company, interviewer, and number in `Examples/` is invented. Northwind Payments does not exist. PM Jordan and Engineer Alex are the same two fictional people used in the resume workflow guide in this repository, carried forward so you can see one system end to end: a Career Brain Trust becomes a tailored resume, and the same material then becomes a Story Bank and a simulator.

The numbers in the examples are deliberately modest. Heroic numbers make a nice demo and terrible practice material, because the point of the Story Bank is that every figure survives a follow up question.

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

Based on "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
