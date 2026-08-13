>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# The Cheat Sheet

This deep dive expands Step 9 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which gave you six lines about building the sheet. The longer version: why it is a web page with tabs rather than a document, the golden rule governing every card, the semantic classes and why consistent encoding beats the encoding itself, card anatomy, provenance flags, the trigger table, the discovery that most delivery problems are landing problems, the split between the sheet and the simulator file and the Story Bank, version discipline, the separate opening sheet, and what to cut.

Read the main guide first, at minimum Steps 6 through 8. Everything here assumes a Story Bank and at least two mocks run out loud. A sheet written before any reps is a document about what you imagine you will need. The value comes from rebuilding it around what you reached for and missed.

---

# Why It Is a Web Page and Not a Document

The sheet is not something you read. It is something you look at, once or twice, for about two seconds each time, while a person on the other screen watches your face.

That settles the format. A markdown document renders as one long column. To find anything you scroll, and scrolling usefully means already knowing where it is, which means reading to navigate. Four or five seconds, and the person you are talking to watches you leave.

Tabs remove navigation from the problem. Eight named regions, one click each, no scroll. You are not searching, you are pointing. When PM Jordan hears a question about a metric, the move is one click on Numbers, not a scan down a page hoping the numbers are above the fold. The cost drops from remembering where something is to remembering its name.

The rest is practical. A single self contained HyperText Markup Language (HTML) file has no dependencies, no internet requirement, and nothing that updates itself twenty minutes before your call. And a screen beside the camera beats paper, which makes you look down and away.

There is a test. Cold, ask out loud what your headline number on story two is, and time it. Longer than about two seconds and the sheet is wrong, almost never because the information is missing. It is buried inside a sentence.

---

# The Golden Rule: Sharpen, Do Not Extend

This is a glance tool, not a study document. Every other rule here follows from that one.

The practical form is a rule about direction. When a card fails, sharpen it, never extend it. If it has grown past what you can take in at a glance, the card is wrong, and the clarifying clause that would complete it makes it more wrong.

The drift toward extension is structural rather than a discipline failure. Every mock produces a note of the form "the sheet did not have what I needed here." Notes become additions. Additions are individually reasonable and collectively fatal. Each costs a fraction of a second on every future lookup, and you never feel that cost while editing. You feel it in the room, looking at a card and unable to find the line.

So run a hard budget. A card fits on one screen, and when something new goes on, either something comes off or the new thing replaces words rather than joining them.

The sharpening move is usually the same: find the clause that supplies context and delete it. In the room you are standing inside the context, so what you need is the trigger. "I took a chargeback queue that was three days behind and got it to same day without adding headcount" is a card line. The version that also gives the year, the volume spike, and the hiring freeze is a paragraph reminding you of something you have never once forgotten.

Cut until the point survives on its own. A long card is worse than no card, because a missing card leaves you improvising and a long card leaves you reading.

---

# Semantic Classes, and Why the Encoding Matters More Than the Colours

Every visual treatment on the sheet means exactly one thing, and it means that thing everywhere.

A green bordered box always means say this out loud, word for word. An amber bordered box always means the honest limit line, the thing you admit rather than dodge. A blue bordered box always means numbers. A purple pill always means the competencies this card owns. A red band always means do not do this. A red bordered block always means a landmine, which is a thing that ends rounds.

The specific colours are arbitrary. What is not arbitrary is that the mapping never varies. You are training a lookup reflex, and reflexes train on visual form, not meaning. Under pressure your eye matches shape and colour rather than reading, which is the whole mechanism behind two second retrieval.

The failure mode is precise. The first time you use green for something that is not verbatim, every green box becomes something you have to read to classify. You have not degraded one card, you have converted the sheet back into a document, and you will not notice, because you know what you meant.

Two rules protect the encoding. **No decorative styling:** if you want to emphasize something and no existing class fits, it goes inside an existing class or off the sheet, because a tenth treatment invented for one special case is followed by an eleventh, then by colours you no longer recognize. **Label every block in words as well as colour:** SAY THIS OUT LOUD, WORD FOR WORD. HONEST LIMIT LINE. NUMBERS. STOP. The redundancy is deliberate. It lets the encoding survive a bad monitor, a colour vision difference, a washed out screen share, and the version of you who has not opened the file in four days.

---

# Card Anatomy

Every story card has the same six elements in the same order, and the order is not decorative.

**The competency pill.** What this card owns, two or three competencies, at the top, so scanning tabs means scanning for what a story proves rather than its subject.

**The headline box, labelled say this first, then stop.** One sentence with the outcome in it, verbatim, first thing out of your mouth. The instruction to stop lives in the label, not a note underneath, because stopping is the part people fail.

**Five short beats.** The spine: situation, what was actually broken, the call you made and the option you rejected, what you shipped and who you had to move, the result and what you would do differently. Fewer and you have a summary, more and you are reading rather than glancing. The beats must not be prose, because prose gets read aloud, and reading aloud sounds like reading aloud.

**The closing line box.** Verbatim, the last sentence, then silence. It gets its own chapter below, because it is the element most people leave out and the one that fixes the most.

**The numbers box.** The metrics on their own, separate from the narrative, because sometimes you need only the number, and reading a story to extract one is the failure this sheet prevents.

**The boundary box.** The honest limit line for this story, pre written. For PM Jordan's chargeback card: "I did not own the model itself, I owned the decision thresholds and the appeal path." When the follow up lands you are not deciding whether to admit a limit, you are reading a line you chose while calm, and it comes out level instead of defensive.

Only the headline and the closing line are verbatim, so everything between is improvised over a fixed skeleton. The anatomy is identical on every card, because one that adds a section for its own good reasons breaks the scan pattern for the rest.

## Provenance flags

Mark every card with whether it has been said out loud or only written. Something short, in the panel note: "voice tested, run four" or "written, never said."

Writing a card feels like finishing it, and it is not. A card that has never been spoken is an untested hypothesis, usually thirty percent too long, usually with one beat you cannot narrate. Under pressure you reach for whatever is on the sheet with equal confidence, and an unspoken card looks no different from one you have delivered five times. So make it look different, then apply the rule: never lead with a card flagged as written but never said out loud.

---

# The Trigger Table

Left column: phrases you might hear. Right column: which story to lead with. Eight to twelve rows, one screen, no scroll.

It exists because of a finding that takes several runs to see. The most common mock failure is not a bad answer. It is a good answer to a slightly different question. You hear "tell me about a time you influenced without authority," you reach for your best story, and your best story is about prioritization under load. It lands, and the grader marks it as not answering the question, which in a real round reads as a candidate who does not listen.

That is a routing failure, and routing is a separate skill from having stories. Mid sentence you do not have the working memory to classify the question and begin speaking at once, and what gives is the classification. The table pre computes it so the only live work is speaking.

Build it from transcripts rather than imagination. The left column holds phrasings you have encountered: from mock runs, from the question bank for your round type, from the recruiter's own wording. "Tell me about a time you influenced without authority" is a textbook phrase. "How did you get the risk team to move when they did not report to you" is what a hiring manager at Northwind Payments would say, and that is the version your ear needs to recognize.

Put the tie break rule on the sheet, in a red band, under the table: if two stories fit, take the one you have said out loud more recently. A well rehearsed near fit beats a perfect fit you have never spoken. That rule lives on the sheet because the moment it applies is the moment you start deliberating, and deliberating is what you cannot afford.

---

# Endings, Because Most Delivery Problems Are Landing Problems

Late in a run of mocks PM Jordan notices that three of five stories have no ending. Not a weak ending. No ending. The story reaches the result and keeps producing sentences until an interviewer interrupts or the energy runs out.

That explains most of the delivery feedback. Openings get rehearsed obsessively, because the opening is the anxious part you think about in the eleven minutes before the call. Endings never get rehearsed, because by the time you reach one you are relieved, and relief does not produce editing.

Look at what the delivery failures actually are. Running long is a landing problem. Trailing off is a landing problem. The interviewer having to interrupt is a landing problem. Adding a second, weaker example is a landing problem. "Does that answer your question" is a landing problem. Almost nothing on the list is about how the answer started.

So write the last sentence of every story down, verbatim, in a green box, and drill it. A closing line hands the conversation back, so the interviewer need not guess whether you are pausing or finished, and it puts the point where people remember it. One sentence, containing the point rather than a summary of it, ending downward in tone.

A missing closing line produces three anti patterns. The trailing recap, "so yeah, that was basically the chargeback thing," ends a good answer on your own dismissal of it. The upward hedge, "does that make sense," invites reassurance instead of the next question. The bonus story, "and actually, a similar thing happened later," spends your best material to weaken your best answer.

To drill it, run rapid fire and ask the simulator to grade only the last fifteen seconds of each answer.

---

# What Belongs on the Sheet, and What Does Not

Three artifacts, three jobs, and most cheat sheet bloat is content that wandered in from one of the other two.

**The sheet holds things you look at while talking.** Verbatim opening scripts, story headlines, five beat spines, closing lines, numbers, boundary lines, the trigger table, landmines, and the questions you will ask them.

**The simulator file holds things the bot needs and you never read during a call.** The persona, the tagged question bank, the rubric, the run modes, and the run log.

**The Story Bank holds the full narrative.** The ten element cards, the raw detail, the answers you gave during the interrogation. This is the source, and the sheet is a compression of it.

The test for anything you add: would you read this while someone was looking at you. If understanding it takes more than a glance, it is reference material and belongs elsewhere.

Reasoning never goes on the sheet. It produced the line, and once the line exists it is finished work. The commonest version of this leak is a note explaining why a headline is phrased that way. You wrote the headline. You know why.

The do not assert list belongs on the sheet only in compressed form, each item a landmine with its substitute phrasing, never the reconciliation record, which lives in the Company and Role Brief.

Duplication between the sheet and the Story Bank is expected: the headline exists in both. Divergence is not. When you sharpen a headline during run four, push it back into the Story Bank so the next round inherits the better line, or the improvement dies with the round.

---

# Version Discipline, and the Separate Opening Sheet

## Never edit version one

Copy it forward. Version one, version two, version three, as separate files sitting next to each other.

You will occasionally sharpen a line past where it works and need the earlier one back, and reconstructing it from memory produces a third version worse than both. The change history is also the only durable record of how you specifically fail, which is what makes your fourth simulator better than your first.

Attribute every version bump to the run that caused it. One line at the top is enough:

`v3, after run 5. Added a closing line to the chargeback card. Run log flagged sprawl on that card three runs running.`

That forces you to name which run exposed the hole, and it makes speculative editing visible: if you cannot name the run behind a change, you are not fixing the sheet, you are decorating it. Decoration is the most comfortable avoidance available to someone who does not want another rep. The mock is a test harness, the artifact under test is the cheat sheet, and a run that produces six scores and no edit is a run you have not finished.

## The opening sheet

Build a second, much shorter artifact for the first five minutes. One screen, no tabs. The twenty five second opener, the why them line, the one sentence answer to why you are looking, the single landmine most likely to fire early, and the name and role of everyone in the room spelled correctly. Nothing else.

It is separate because the opening is the only fully scripted part of the round, so the only part you can re read cold ten minutes out and still have in your head when it starts. Paging through eight tabs at that point is how you notice four things you meant to sharpen and arrive rattled. Second reason: during those five minutes you will not be clicking tabs, so whatever you need has to be visible without one.

The division of labour is clean. The opening sheet is what you read. The full sheet is what you refer to.

---

# What to Cut, and How to Tell It Has Become a Study Document

The failure mode of this artifact is not that it goes wrong. It slowly turns into a study document, which is a perfectly good thing that is useless during a call.

**You read it the night before for reassurance rather than to check something.** The clearest signal available. A glance tool is consulted, a study document is absorbed, and if you are reading the sheet end to end you are managing anxiety, which more content will not fix.

**Any card that requires scrolling,** measured against the smallest screen you might use. No exceptions.

**Any tab you have never opened during a mock.** Tabs cost nothing in file size and a lot in scan time, because the tab bar is the first thing your eye hits. A tab that survived five runs unopened is not being saved for the real thing, it is being avoided.

**Prose paragraphs anywhere,** especially ones explaining why a line works. That is the reasoning leak.

**More than three story tabs for a thirty to forty five minute round.** You will use two. Five story tabs is not extra coverage, it is a routing problem you created for yourself at the worst possible moment.

**Anything appearing twice** because you were not sure where it belonged. Duplication doubles the surface your eye has to eliminate.

**Anything you know cold.** The counterintuitive one, and the highest yield cut. The sheet is for things you might lose under pressure, not for things you have. A card you have drilled ten times should get shorter: once the story is in you it needs the headline, the landing, and the numbers, and the beats can go. Most people never cut a card because cutting feels like removing preparation. A card that has shrunk is a card that has been learned.

One last thing. On the day, the best outcome is that you glance at the sheet twice and never open the tab you spent longest on. That is not wasted work. The sheet's function is to remove one fear from the room, of losing a number or a name mid sentence, so your attention is free for the person in front of you and the question they just asked. A sheet that does that and goes unused has done its entire job.

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

Based on "The Cheat Sheet," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
