>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# 02: Interviewer Deep Research

This is the highest-value prompt in the library and the most dangerous. A good interviewer dossier tells you what this person tends to probe, in what order, and what evidence satisfies them. A bad one invents a personality from a job title, and you walk in and confidently misremember a stranger's career back at them.

The prompt is built to prevent that. It asks the research tool to verify your assumptions rather than generate a profile from nothing, forbids fabricated quotes and invented titles, and forces every finding into a confidence tier so you can see how much of the dossier is real.

Run it in a deep research tool with web access. Ten to twenty minutes per interviewer. The output becomes one `Interviewer Dossier` file per person.

---

# When to run this

Run it once you know who is in the room, which usually means after the recruiter replies to the intake email in prompt 05. Run it separately for each interviewer rather than batching, because batching produces blended profiles where one person's career quietly absorbs another's. If you only have a first name or a job title, skip this prompt and spend the time on prompt 03: research on a person you cannot identify is fabrication with extra steps.

---

# The prompt

Fill in the belief block honestly, including the parts you are unsure about. The tool is more useful as a fact checker than as a biographer.

```
You are a research analyst. I am interviewing with the person below and I need a verified profile, not a generated one. Your default posture is skeptical. Correcting me is more useful than agreeing with me.

WHO
Full name: [FULL NAME]
Company: [COMPANY]
Title as I understand it: [THEIR TITLE]
Public profile links I already have: [LINKEDIN URL, ANY OTHER LINKS]
The round they are running: [ROUND TYPE AND LENGTH]
Role I am interviewing for: [ROLE TITLE]
My background in three sentences: [YOUR BACKGROUND]

NAME COLLISION WARNING
[FULL NAME] is a common name. There is also a [OTHER PERSON DESCRIPTION: for example, an academic at a university, an executive at a different company, an author]. Do not merge them. Before you report any fact, confirm it belongs to the person at [COMPANY] holding the title above. If you cannot tell which person a source refers to, report the source and say which person it might belong to, and do not use it to support any conclusion. If you find three or more distinct people with this name, list them and their distinguishing details before continuing.

WHAT I ALREADY BELIEVE (verify or correct each line)
1. [BELIEF ONE] Source I am relying on: [LINK OR "assumption, no source"]
2. [BELIEF TWO] Source: [LINK OR "assumption, no source"]
3. [BELIEF THREE] Source: [LINK OR "assumption, no source"]
4. [BELIEF FOUR] Source: [LINK OR "assumption, no source"]

For each numbered belief return one of exactly four verdicts: CONFIRMED with a source link, CORRECTED with the accurate version and a source link, CONTRADICTED with the conflicting sources shown side by side, or NOT FOUND with a note on what you searched. Do not restate a belief back to me as fact simply because I wrote it down.

HARD RULES
1. Never fabricate a quote. Only quote text you can link to. If you are paraphrasing, label it as a paraphrase.
2. Never invent a job title, an employer, a date range, a school, or a publication. If a date is uncertain, write the range you can support and say the source is unclear.
3. A negative finding is a real finding. Report it as "searched, not found: [what you searched]". Never write that something does not exist, and never fill a blank with a plausible-sounding placeholder.
4. Where two sources conflict, show both and say which you find more reliable and why. Do not silently pick one.
5. Nothing about their personal life, family, health, politics, or anything outside their public professional footprint. If you encounter it, skip it.

DELIVER THESE SEVEN SECTIONS

1. IDENTITY CONFIRMATION
State plainly whether you are confident you found the right person, and on what basis. List the identifiers you matched (employer, title, tenure, location, distinctive project). If confidence is low, stop here and tell me what additional detail I need to supply.

2. VERIFIED CAREER HISTORY
Reverse chronological: employer, title, approximate dates, and one line on scope. Source-link each entry. Flag every place where sources disagree about dates or titles. Note career shape explicitly: how long they stay, whether they moved through operating roles or specialist roles, whether they have been at [COMPANY] long enough to have hired for this role before.

3. PUBLIC FOOTPRINT
Conference talks, podcast appearances, published writing, engineering or product blog posts, open-source contributions, patents, panel appearances, and public posts of substance. For each: title, date, link, and the two or three ideas they actually argued. If you find nothing in a category, write "searched, not found" and name the sources you checked. A thin footprint is useful information, so do not pad it.

4. HOW THIS ARCHETYPE RUNS A ROUND
Ground this in their training lineage, not in personality invention. Look at the interview philosophy of the companies where they spent formative years, the norms of their function, and any public statement they have made about hiring. Then tell me: how a person trained in those environments typically opens, how deep they push on a single example before moving on, whether they favour structured frameworks or unstructured probing, how they handle a candidate who does not know something, and what they write down. Label the whole section INFERRED and show which lineage evidence each inference rests on. Do not describe their temperament as if you have met them.

5. RANKED LIKELY QUESTIONS
Ten to fifteen questions, ranked most likely first, each phrased the way this person would plausibly say it given their function and the round type. For each: what it is really testing, what a strong answer shows, and the failure mode that gets a candidate marked down. Mark any question that follows directly from something in their public footprint, and say which item it follows from.

6. WHAT WINS THEM AND WHAT LOSES THEM
Two short lists. Wins: the kinds of evidence, structure, and behaviour this archetype rewards. Loses: what makes them disengage, what reads as hand-waving to someone with their background, and any specific topic where a shallow answer would be obvious to them. Tie each item to evidence where you can and label the rest INFERRED.

7. CONFIDENCE TIERS
Close with three lists covering every claim in the dossier.
HIGH: multiple independent sources, or one primary source.
MODERATE: single secondary source, or reasonable inference from strong evidence.
NOT FOUND: what I asked about that you could not verify, with the searches you ran.
Then give me the three things I should treat as unverified and never assert out loud, with a safe way to raise each one as a question instead.
```

---

# What good output looks like

Reject and re-ask if the tool returns a fluent biography with no confidence tiers, quotes without links, or a "how they run a round" section that reads like an astrology profile. Reject if your four beliefs come back confirmed with no sources, which usually means it agreed with you rather than checked. Reject if there is no NOT FOUND list: a genuine search on a real person always fails at something. Reject if it merged two people with the same name after you warned it.

Good output feels thinner than you wanted and more trustworthy than you expected. Two verified employers and an honest empty footprint beats a rich profile you cannot source.

---

# What to do with the output

Save it as `Interviewer Dossier - [FULL NAME].md` in your round folder. One file per person.

Then extract three things. The wins and loses lists become the four-line persona in your simulator template, which makes the mock feel like this person rather than a generic interviewer. The ranked questions seed the question bank. The NOT FOUND list and the never-assert items go into the **Do not assert** section of your cheat sheet with the substitute phrasing attached, so under pressure you ask "how has the team's approach to X changed since you joined?" instead of asserting a career fact you half-remember from a research output.

The identity confirmation and any contradicted claim get carried into `04 - Cross-Validation and Reconciliation`.

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

Based on "02: Interviewer Deep Research," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
