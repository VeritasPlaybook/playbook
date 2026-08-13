>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Example: Engineer Alex, Technical Panel at Northwind Payments

**Everything in this folder is fictional.** Alex Rivera is not a real person. Northwind Payments is not a real company. Ines Kowalczyk and Marcus Dube are not real interviewers. Beacon Pay, Lumen Streams, and Hearthstone Labs are invented employers. Every number is illustrative, written to be modest and defensible rather than impressive. Open source technologies are named where the persona's history requires them, and those references make no claim about any real product or vendor.

**One naming note.** Alex Rivera is the candidate everywhere in this kit and never anybody at Northwind Payments. The template files illustrate interviewer disambiguation with a separate fictional person, Priya Raghunathan, named differently so the two are never confused. The dossier here still carries a wrong person exclusion, because a common name really does contaminate a research pass and that section is where you record it.

---

## Who this person is

Alex Rivera is a Senior Backend Engineer, roughly six years in. Go primary, Python secondary. Currently at Beacon Pay on the transaction processing service. Before that: real-time streaming infrastructure at Lumen Streams, and a first engineering role at Hearthstone Labs, an early-stage Python startup that went from four people to fourteen.

Alex already exists elsewhere in this repository. The resume guide, [Tailored, Not Templated](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md), ships an example Career Brain Trust for the same person, with the same employers, dates, and numbers. This folder is the next chapter: Alex applied to Northwind Payments, cleared a recruiter screen and a coding exercise, and now has a technical panel on the calendar. Every story card traces to a bullet in that Brain Trust.

The earlier chapter is at [ai-powered-workflows/ai-resume-deepdives/templates/Example Career Brain Trust - Engineer Alex/](https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/ai-resume-deepdives/templates/Example%20Career%20Brain%20Trust%20-%20Engineer%20Alex).

## What this round is

A 60-minute technical panel for a Senior Backend Engineer role on the Money Movement group at Northwind Payments, a fictional payments infrastructure company. Two interviewers in the same call: Ines Kowalczyk, a Staff Engineer who owns the settlement data model, and Marcus Dube, an Engineering Manager, six years in site reliability before management.

The wrinkle worth noticing: Alex's public positioning says "targeting Staff Individual Contributor roles," and this posting is Senior. The recruiter said Northwind levels Senior broadly and a Staff outcome from this loop is possible but not the default. Alex ran the loop anyway, so one probe in the simulator is about saying why, plainly, without sulking about the title or pretending the question does not exist.

## What to look at, and in what order

1. **`Run Log Excerpt.md`** first. It is the point of the system. Two graded runs, four days apart, verbatim. Run one finds a specific hole: Alex describes a database migration as a throughput win, and the Staff Engineer asks twice how Alex knew the shard key was right. The cheat sheet gets a version bump. Run two is markedly better on technical depth and risk awareness, and worse on a dimension nobody was working on, because the fix escaped its context. That is the most instructive thing in the folder.
2. **`Cheat Sheet.html`** next, in a browser. This is the only artifact that exists during the real call.
3. **`_STATE.md`**, to see a maintained anchor file rather than a filled-in-once one.
4. **`Company and Role Brief.md`**, particularly the **Do not assert** section with three worked entries.
5. **`Interviewer Dossier.md`**, covering both people in one file, with a headline correction that reverses which of them you would assume is the hard one.
6. **`Story Bank/INDEX.md`** and the three cards.
7. **`Simulator.md`**, the Super Simulator build, and **`Kickoff Prompt.md`**.
8. **`Round Debrief.md`** last, written the evening of the real round.

## Why this one is a Super Simulator and Jordan's is a Mock Kit

The other example, the hiring manager round in the folder beside this one, uses the light build. Sixty minutes with two people asking technical questions is a coverage problem: the realistic fear is a topic that never got drilled coming up cold, which is what the heavy build is for. Forty five minutes with one manager is a delivery problem, and a Super Simulator for it would have cost two hours and taught nothing extra. The two folders sit side by side so you can see where the line is.

## What is deliberately imperfect here

There is no incident card in the Story Bank, and there is an ex-site-reliability engineer on the panel. Run one finds the gap, logs it, and it is only half closed before the round. Run two exposes a fresh problem created by the fix from run one. A worked example where everything gets closed would be a nicer story and a less useful one.

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

Based on "Example: Engineer Alex, Technical Panel," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
