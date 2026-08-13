>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# 04: Cross-Validation and Reconciliation

This prompt is different in kind from the first three. Those generate. This one disagrees.

Run it in a second research tool from a different vendor than pass one, and give it a list of claims rather than a subject. Its only job is to independently confirm, refute, or fail to find each claim. Using the same tool twice reproduces the same errors with more confidence, which is worse than not checking at all.

Ten to twenty minutes. The output is not a new document. It edits the documents you already have and produces the **Do not assert** list that keeps you from being confidently wrong about a stranger in a room where you cannot check.

---

# When to run this

Run it after prompts 01, 02, and 03, once you have a brief and at least one dossier. Run it on load-bearing claims only, the ones you would say out loud or build an answer around, usually eight to fifteen of them rather than everything you found. If you have less than forty eight hours and must cut something, cut a mock run rather than this: a weaker rehearsal costs you polish, an unchecked claim costs you credibility.

---

# The prompt

Paste this into a fresh thread in a different research tool. Fill the claim list with your own claims, one per line, each tagged with where it came from.

```
You are an independent fact checker. Another research tool produced the claims below about a company, a role, and an interviewer. I am about to rely on these in a job interview. Your job is to check them, not to improve them or fill them out.

Assume the claims may be wrong. You have not seen the original research and you should not try to reconstruct it. Do not add new claims of your own, do not expand on any claim, and do not tell me anything I did not ask about. If a claim is partly right, split it into the part that holds and the part that does not.

CONTEXT (for search only, not to be verified)
Company: [COMPANY]
Role: [ROLE TITLE]
Interviewer: [FULL NAME], [THEIR TITLE] at [COMPANY]
Name collision note: [FULL NAME] may be confused with [OTHER PERSON DESCRIPTION]. Do not use sources about the other person.

CLAIMS TO CHECK
C1. [CLAIM] (source given in pass one: [LINK OR "none"])
C2. [CLAIM] (source: [LINK OR "none"])
C3. [CLAIM] (source: [LINK OR "none"])
C4. [CLAIM] (source: [LINK OR "none"])
C5. [CLAIM] (source: [LINK OR "none"])
C6. [CLAIM] (source: [LINK OR "none"])
C7. [CLAIM] (source: [LINK OR "none"])
C8. [CLAIM] (source: [LINK OR "none"])

METHOD
1. Search independently for each claim. Where pass one supplied a source link, do not treat it as evidence until you have opened it and confirmed it actually says what the claim says. Report separately if a cited source does not support the claim it was attached to, because that is the most common failure and the easiest to miss.
2. Prefer primary sources: company sites, filings, documentation, official profiles, conference programmes, publication records.
3. Do not resolve disagreement by averaging. If two sources conflict, show both.
4. Never fabricate a quote or a date. If a date is approximate, say what range the evidence supports.
5. Ignore anything about the person's private life.

OUTPUT: THREE BUCKETS, NOTHING ELSE

AGREED
Claims you independently confirmed. For each: the claim identifier, the confirming source link, the date of that source, and whether confirmation came from one source or more than one.

CONTRADICTED
Claims where you found evidence pointing the other way. For each: the claim identifier, what the evidence actually says, the source link, and your assessment of which version is more reliable and why. Include partial contradictions, for example a right employer with wrong dates or a right person with a wrong title.

UNVERIFIED
Claims you could not confirm or refute. For each: the claim identifier, exactly what you searched (terms, sites, and databases), and whether the absence of evidence is meaningful. Absence is meaningful when you would expect a public record and there is none. Absence is not meaningful when the claim concerns something that is rarely public, such as internal team structure or an individual's role on a project.

Close with one line: which single claim, if wrong, would do the most damage to me in the interview.
```

---

# What good output looks like

Reject and re-ask if everything lands in AGREED, which almost never happens honestly and usually means the tool restated your claims back at you. Reject if the UNVERIFIED bucket does not say what was searched: "could not confirm" without a search trail is not a finding. Reject if it opened no source links. Reject if it volunteered new facts about the company, which means it drifted from checking into generating.

A healthy result on a real person is roughly half agreed, one or two contradicted, and the rest unverified.

---

# What to do with the output

Handle each bucket differently, and do it as a file edit rather than a mental note.

**AGREED becomes fact.** Leave it in the brief or the dossier and mark it as double-sourced. You can say these things out loud without hedging.

**CONTRADICTED gets assigned to a human.** Do not pick a side and do not average the versions. Strike the claim from your documents, then either ask the recruiter (see prompt 05) or turn it into a question you can safely ask in the room. A contradiction in a career history is often just a stale profile, and asking about it is normal conversation.

**UNVERIFIED goes into the "do not assert" list** at the bottom of the relevant file, with substitute phrasing written beside it before you close the file. The substitute is the whole point. If you only strike the claim, you will still reach for it under pressure.

Here is the conversion worked through. Pass one claimed your interviewer "led the fraud platform rebuild at Northwind Payments." Pass two put it in UNVERIFIED: the person is confirmed at Northwind Payments with a confirmed title, but no public source ties them to that programme. Asserting it is a bad trade: if you are wrong you have told a stranger a fabricated fact about their own job, and there is no recovery from that inside a thirty minute call.

So write the row as: **Do not assert:** they led the fraud platform rebuild. **Say instead:** "I have been reading about how payments teams are rethinking fraud tooling. How much of that work sits with your team?" You get the same information, you get it from the only person who knows, and you sound curious instead of wrong. Every unverified claim converts the same way: a statement you cannot support becomes a question only they can answer.

Finally, update `_STATE.md` with one line recording that pass two ran, the date, and how many claims were struck. Later rounds inherit these documents, and the next version of you needs to know which parts were checked.

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

Based on "04: Cross-Validation and Reconciliation," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
