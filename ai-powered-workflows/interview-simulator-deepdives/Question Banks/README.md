>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Question Banks: Which One to Load and How to Drill It

Seven files. Six round types plus an appendix for the recruiter screen. Each is a drop in question bank for the simulator you build in the main guide, carrying its own scoring dimensions and landmines, because a good answer in a peer round is a mediocre answer in an executive round.

You do not load all seven. You load the one that matches the round on your calendar. Loading more than one at a time produces a simulator that drifts between personas and grades you against the wrong rubric.

# Which file for which round

| The invite says | Load | Also worth loading |
|---|---|---|
| Screen, intro call, chat with talent | Appendix: Recruiter Screen | Nothing. Keep it short. |
| Call with the hiring manager, or with the person you would report to | 01: Hiring Manager and Fit | 02, if the manager is known to run structured behavioural questions |
| Values interview, competency interview, or a named leadership principle | 02: Behavioural | Nothing |
| Case, product exercise, take home review, portfolio review, analytics case | 03: Product Sense and Case | 04, if the case has a technical core |
| Technical interview, architecture review, deep dive, system design | 04: Technical Deep Dive | 03, for technical product roles |
| Final round, executive chat, skip level, panel, three people on the invite | 05: Executive and Panel | 02, since panels usually include behavioural probes |
| Team interview, peer interview, cross functional partner, "meet the team" | 06: Peer and Cross-Functional | 02 |
| Unlabelled invite, one hour, one name you do not recognize | 01 | Ask the recruiter. The intake prompt in the Prompt Library is four minutes of work. |

When the invite is ambiguous, prepare the round one level harder than you expect. Preparing for an executive panel and getting a friendly manager chat costs nothing. The reverse costs the loop.

# How the identifiers work

Every probe is a single block with three parts.

The bold line is the machine readable header: a round prefix and number, a topic tag, and a difficulty tier. `HM-14 · track-record · T2` is probe fourteen in the hiring manager bank, tagged track record, at core difficulty. Prefixes are `HM`, `BEH`, `CASE`, `TECH`, `EXEC`, `PEER`, and `REC`.

The quoted line is the question, written the way an interviewer would say it. That is the only line the simulator reads aloud.

The italic `*Strong answer contains:*` line is the grading note. It is written for the grader, not the candidate, and it must never be spoken during a mock. A simulator that recites it has handed you the answer key and the session is worthless. If your tool keeps leaking it, move the grading notes into a separate section of the prompt and tell the simulator to consult them only when producing a score.

Keep the identifiers unchanged when you copy probes into your prompt. They are what make your run log readable across weeks: "weak on TECH-26 twice" points at a specific gap, "weak on failure modes" points at nothing you can act on.

# Difficulty tiers

**T1 is warm up.** Broad, expected, and answerable by anyone who prepared for an hour. Use these in the first session of a new round type and to check length control.

**T2 is the core of the round.** Most of what you will actually be asked sits here. Spend most of your practice time in T2.

**T3 is the edge.** Probes that are uncomfortable, that ask you to argue against yourself, or that go one rung past where you are confident. Save these for the final two sessions before the round, when a bad session is still useful and no longer demoralizing.

A session that is all T1 feels good and teaches nothing. A session that is all T3 teaches you that you are unprepared and little else. Six to eight probes weighted toward T2, with one or two T3 at the end, is a working session.

# How to steer coverage

Each bank ends its usage section with a coverage tracker: a two column table of that file's tags with a count. Paste it into your simulator's state file or into the top of your run log and increment it after every session.

**Drill the lowest count, not the favourite.** Preparation fails predictably: people rehearse the three stories they enjoy and walk into the round on a tag they have never said out loud. The tracker exists to override that instinct, and it only works if you let the numbers pick the session.

**Tell the simulator to select for you.** A line like "choose six probes from the tags with the lowest counts in the tracker, weighted two thirds T2 and one third T3, and do not repeat a probe from the last two sessions" removes the choice from you entirely, which is the point.

**Stop at even coverage, not at total coverage.** You do not need every probe in a file. You need no tag sitting at zero and no tag more than about three ahead of the rest. In practice that is four to six sessions for one round type.

**Cross load one tag when the round is mixed.** Real rounds are rarely pure. A hiring manager will ask two behavioural probes, a panel will ask a case, a peer will ask about failure. Add one tag from a neighbouring bank rather than loading the whole file, so the persona stays intact.

# Two rules that apply to all seven

**The bank is not the point.** Running probes is a test harness, and the thing under test is your Story Bank and your cheat sheet. Every weak answer should produce a defect note against an artifact, not just a note that you were weak. A session that ends with no artifact changed was entertainment.

**Adapt the wording to your function.** These banks are written to work for product managers, engineers, designers, marketers, and analysts, and where a probe is function specific it says so in the grading note. Everything else is portable: swap the domain nouns and the probe still tests the same thing. Rewrite the question in the vocabulary your interviewer would use, because a probe that sounds foreign gets answered as a puzzle rather than as an interview question.

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

Based on "Question Banks: Which One to Load and How to Drill It," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
