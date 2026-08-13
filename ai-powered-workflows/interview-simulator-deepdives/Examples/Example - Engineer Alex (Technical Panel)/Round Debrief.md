>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Round Debrief: Northwind Payments, technical panel, 2 July 2026

> **Worked illustration.** Alex Rivera, Ines Kowalczyk, Marcus Dube, and Northwind Payments are fictional. Every detail below is invented for teaching.

**Interviewers:** Ines Kowalczyk, Staff Engineer, Money Movement. Marcus Dube, Engineering Manager, Authorization and Risk Platform.
**Format and length:** Video panel, 60 minutes, ran the full hour and finished on time
**Filled in at:** 2 July 2026, 6:15 in the evening, about three and a half hours after the call

---

## How it actually went

**Tone read:**

- **Their energy:** Ines neutral and unhurried throughout. Marcus warm at the start, noticeably sharper for the middle twenty minutes, warm again at the end.
- **Where the energy changed, and on what:** two moments. Marcus sharpened when I said a customer found our incident before we did, and stayed sharp until I finished the story, then relaxed more than he had been at the start. And Ines leaned in on the shard key answer, specifically the rejected candidates, and asked three follow-ups in a row, the longest single thread of the hour.
- **Did it feel like a screen or a conversation:** a screen for the first ten minutes, a conversation after that.
- **Anything about the setup worth recording:** both on camera, both in the same room at one point, which meant cross-talk I could not hear. They swapped who was leading twice, cleanly, without stepping on each other. Marcus took notes visibly, Ines did not.

**Their question list, in the order asked:**

1. Marcus: "Tell me about the last time something you owned broke."
2. Marcus: "Who found it?"
3. Marcus: "What did the merchant see?"
4. Ines: "Take me through a schema change you made on something live."
5. Ines: "Why that shard key and not the transaction identifier?"
6. Ines: "What did you reject and why?"
7. Ines: "How did you know it worked?"
8. Ines: "Where is that design ugly now?"
9. Marcus: "Our authorization path went slow in February, not down. What is the first thing you would have looked at?"
10. Ines: "If our ledger and a bank record disagree about one movement, where do you start?"
11. Marcus: "What is the last thing you learned that changed how you build?"
12. Both: questions for us.

The ordering is the finding. Marcus opened with an incident, went straight to detection, and had asked what a customer saw by minute six. The dossier predicted all three and the mock never produced them in that sequence, because it kept treating the incident question as a mid-round probe rather than the opener.

---

## What landed

- I said: *"a platform customer found it before our monitoring did, and it ran about six hours"* and Marcus said "thank you for saying that" and his posture changed. This is the half-built card. The one field I had, detection and who found it, was the field that mattered.
- I said: *"the seven times is the headline and the 31 rows is the actual result"* and Ines wrote nothing but said "that is the right way round" and then asked three follow-ups, the most engaged she was all hour.
- I said: *"transaction identifier gives perfect distribution and scatters our dominant read pattern, and date range gives clean archival and a permanently hot last shard"* and Ines said "and you have two hot merchants now, do you not," which she had worked out from the answer before I got to it. Saying yes and describing the manual isolation was the best exchange of the round.
- I said: *"I would want to know what your ordering and delivery guarantees actually are before I answer that"* and Ines answered the question, in detail, for about two minutes. Asking instead of assuming bought more information than any question I had prepared.

---

## What was shaky

- **Question 3, what did the merchant see.** I had the sub-merchant side, on the card as of version 2.1. I did not have the cardholder side and said so. Marcus accepted it and moved on, but I could hear it being a smaller answer than it should have been. The v2.1 line worked as intended, covering for a fact I did not have rather than a skill I did not have.
- **Question 11, the last thing I learned.** I gave the timestamp precision story, a good story and also the answer I gave to a different question in run two. It came out slightly rehearsed because it is rehearsed. Better to have given something from the last month.
- **Question 10, the ledger and bank disagreement.** Fine, not strong. I asked good clarifying questions and then, once Ines answered them, my proposal was thinner than the questions had promised. I set up a frame I could not fill. Note for the next round: do not ask three clarifying questions unless the answer uses all three.
- **Anything I said that I am not sure I can defend:** I said the comparison ran "about six weeks." My notes say six weeks. I am not certain whether that was six weeks of comparison or six weeks from the start of dual write. Check.

---

## What was NOT asked, and what that signals

| Prepared area that never came up | What I think the absence means | Confidence |
| --- | --- | --- |
| The Senior versus Staff question | Not their decision, and neither of them raised it. Almost certainly saved for the hiring manager conversation. One full drilled probe went unused, correctly. | High |
| Story 3, the service mesh | Not a priority. Nobody asked about latency, service topology, or cross-team migration. This round was about data and failure, not platform work. | High |
| Idempotency, Story 1, as a story | Interesting absence. The idempotency work is on my resume and the most obviously relevant thing I have done. It came up only as context inside the incident answer. My guess is the coding exercise already covered interface design, so they spent the hour on what they could not otherwise see. | Medium |
| Anything about mentoring or design documents | Saved for the hiring manager. Both are in the job description and neither person asked. | Medium |
| Live system design on a whiteboard | The recruiter said no coding and it turned out to also mean no drawing. Everything was verbal and grounded in things I had actually built. Worth knowing for anyone else preparing for this panel. | High |

The absence pattern says this panel was calibrated to test what a coding exercise cannot: judgment under a real system's history. Every question was about something I had done rather than something hypothetical, except question nine.

---

## Intel they gave away when answering your questions

- **How they described the team:** Ines said Money Movement is "six engineers and a very long queue of things that only one person understands." Said without drama, which made it more convincing.
- **The hardest problem they named:** Ines, immediately: the second ledger. Her words: "We have two sets of cutoffs and one matching engine that was designed when there was one, and every edge case now has a mirror image we did not think about." That is the most useful sentence of the hour, a much sharper version of the guess in my Company and Role Brief.
- **Words or phrases they repeated:** "agreement" from Ines, six or seven times, always about records rather than people, which confirms the vocabulary note. Marcus used "detection" four times and "mitigation" twice, and never "root cause."
- **What they seemed tired of:** Marcus, unprompted: "people tell me about incidents where they were the hero of the incident." He said it lightly and it was clearly a real complaint.
- **What they lit up about:** Ines on the rejected shard key candidates. Marcus on the fact that a customer found our incident first.
- **Anything they said about the next round:** yes. Hiring manager conversation, one person, name not given, "probably a couple of weeks." Ines said it would be "less technical than this and more about what you want."
- **Any name they dropped:** one, an engineer on Money Movement described as "the person who understands the United Kingdom cutoffs." No name given, just the description, which is itself a fact about the team.
- **Anything that contradicted my Company and Role Brief:** two things. The move off the batch window is not finished. Ines said "the main path is off it and the exception path is not," more precise than my do-not-assert phrasing and it should replace it. And Money Movement is six engineers, smaller than I assumed, which changes what "own the matching engine" means.

---

## What I could not remember

- The exact wording of question eleven. I have the substance.
- What Ines said in the two minutes about their event log guarantees. I remember being satisfied by it and did not write it down while she was speaking, which was a mistake.
- Whether Marcus asked about the February incident before or after Ines's shard key thread.

*Note to self: ask for a recall questionnaire tomorrow. The event log answer is the one worth recovering, because it directly closes a do-not-assert item.*

---

## Answers to promote to locked

| Question it answers | Locked wording | Why it is locked |
| --- | --- | --- |
| Any migration or verification question | "The seven times is the headline and the 31 rows is the actual result." | Ines said "that is the right way round" and the round opened up from there. |
| Any incident question | "A platform customer found it before our monitoring did, and it ran about six hours." | Changed Marcus's posture in one sentence. The honest version outperformed anything polished. |
| Any question resting on an assumption about their systems | "I would want to know what your ordering and delivery guarantees actually are before I answer that." | Bought two minutes of detailed information I could not have researched. |
| Shard key or data modelling | The three-candidate structure: chosen, rejected, rejected, then the cost that is still ugly. | Longest and best thread of the hour. |

---

## Accuracy guards to carry forward

1. **Guard:** do not say the batch window migration is finished, and do not say it has barely started. **Correct version:** "the main path is off it and the exception path is not," which is Ines's own phrasing. **Learned from:** Ines, directly, on 2 July.
2. **Guard:** do not describe the Money Movement team as large or well staffed. **Correct version:** six engineers. **Learned from:** Ines.
3. **Guard:** stop saying the comparison ran "about six weeks" until it is checked. **Correct version:** unknown, verify against project notes before the next round. **Learned from:** noticing mid-answer that I was not certain.
4. **Guard:** do not tell an incident story where I am the hero of the incident. **Correct version:** detection, who found it, what I personally did, what was still broken afterward. **Learned from:** Marcus saying it out loud.
5. **Guard:** do not use the timestamp precision story twice in one loop. **Correct version:** find something from the last month for "what have you learned recently." **Learned from:** hearing myself reuse it.

---

## Proposed shape of the next round's build

> **DRAFT ONLY. DO NOT BUILD THIS YET.** Written while the round was fresh so the thinking is not lost. Nothing here is approved.

- **Next round is:** hiring manager conversation, one person, date unconfirmed, "probably a couple of weeks."
- **Interviewer:** unknown. Ask the recruiter for a name today, not next week.
- **What today suggests they will test:** what I want, and whether the Senior title will be a problem in six months. Ines said explicitly it would be "less technical and more about what you want," close to being told the agenda.
- **New dossier needed:** yes. Nobody researched.
- **Build type:** Mock Kit, not Super Simulator. One person, forty five minutes probably, and the risk is delivery rather than coverage. The heavy build would be two wasted hours.
- **Cheat sheet changes proposed:** new build for the round type. Carry forward the Numbers tab and the Landmines tab unchanged. The Triggers table needs rewriting entirely, because none of the current rows fit a fit-and-motivation round.
- **Stories to add:** finish Card 4. The half-built version was enough today and will not be enough if the hiring manager asks a version of the same question, because they will want the part after the incident rather than the detection.
- **Stories to retire:** none, but Story 3 was not used today and is unlikely to be used next round either. Keep it, do not drill it.
- **Question areas to drill:** the Senior versus Staff answer, which is now the live question rather than a hypothetical. And a genuine "what do you want in three years" answer, which I do not have in any artifact.
- **What I do not yet know and need before building:** who the hiring manager is, whether they are the Money Movement manager or a level up, and whether the level decision is made in that conversation or after it.

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

Based on "Round Debrief," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
