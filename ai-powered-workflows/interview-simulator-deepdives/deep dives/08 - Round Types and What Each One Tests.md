>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Round Types and What Each One Tests

This deep dive expands Steps 1 and 2 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which told you to name the round you are preparing for and ask the recruiter five questions, then moved on. The longer version: one chapter per round type, each covering the decision that round makes, who runs it, what it is really testing underneath the stated topic, its specific failure modes, and how to tune the six dimension rubric for it. Then an appendix on the recruiter screen, a chapter on working out which round you are in when nobody tells you, and what to do when you find out in the first two minutes that you prepared for the wrong one.

Read the main guide first. This chapter assumes you know the rubric has six dimensions, that dimension one is always structure and six is always communication and presence, and that two through five are the tuneable ones. Deep Dive 6 covers the scoring machinery. This chapter tells you what goes in the middle four slots and why.

---

# Hiring Manager and Fit

**The decision it makes.** Whether this person wants you on their team, and whether the problem they are hiring against is one you have solved. It is the likeliest real gate: a hiring manager who wants you will carry you through a mediocre panel, and one who does not will find a reason.

**Who runs it.** The person you would report to, occasionally their manager.

**What it is really testing.** Not your background, which they have on paper. Whether you understand what is hard about their job. A hiring manager has one or two problems they think about at night, and the round checks whether you have met those. Underneath sits a quieter question: what would you be like to manage. Do you bring decisions or problems, do you tell them bad news early, will they have to check your work.

**Failure modes.** Reciting the resume chronologically, answering a question they did not ask. Describing what your team did without ever saying what you decided, the seniority signal most candidates leave out. Answering "why us" in their own marketing language. And vagueness about why you are looking, which reads as something hidden even when nothing is.

**Rubric tuning.** Dimensions two through five: problem fit, ownership, how you operate day to day, and motivation. The two this round cannot forgive are ownership and problem fit. A hiring manager can work with a candidate who is a little unpolished. They cannot work with one whose contributions dissolve into the team's when you press.

---

# Behavioural

**The decision it makes.** Whether your track record survives structured probing, and whether you behave the way the company says it wants people to behave. In organizations with named values or leadership principles, this is where those get scored.

**Who runs it.** Anyone. A trained interviewer from another team, a peer, the hiring manager. Their function matters less here than in any other round, because they are working from a script.

**What it is really testing.** Whether your stories are load bearing. Everyone arrives with three polished stories, and the round is built to go one or two follow ups past where the polish ends. Underneath is the measurement: the numbers you can defend, the alternative you rejected and why, the part you got wrong, the person who disagreed and what happened. A story that collapses at follow up two is worse than a smaller story told completely.

**Failure modes.** The plural we, where nobody can tell what you did. The heroic story with no cost, which reads as untrue or unreflective. Reusing one story for three questions, scored as narrow experience. Failure stories that are disguised successes, or end in grievance rather than a lesson. And length, because these rounds have a fixed number of probes and a six minute answer has eaten someone else's question.

**Rubric tuning.** Dimensions two through five: depth, judgment, ownership, and fit. The unforgiving pair is depth and ownership. Depth is what the follow ups hunt for, and ownership is what the format is built to isolate.

---

# Product Sense and Case

**The decision it makes.** Whether you can think in front of people. Everything else in the loop evaluates work you already did under conditions nobody can reconstruct. This round watches you reason live, which is why it is weighted heavily even though the specific answer rarely matters.

**Who runs it.** Usually a product manager one or two levels above the role, sometimes with a designer or analyst observing.

**What it is really testing.** Not the answer. The framing, the tradeoffs, and whether you notice the constraint nobody mentioned. A strong case answer usually starts by narrowing: who exactly, in what situation, against what alternative today. The most predictive behaviour is clarifying before solving, and the second is naming what you would need to know to be wrong. Underneath, they are checking whether you have opinions about users or only about features.

**Failure modes.** Solving immediately, the most common and most damaging. Reciting a memorized framework as though it were the answer. Generating twelve ideas and prioritizing none. Missing the business model, which produces confident recommendations that would bankrupt the company. And one specific to people who prepared well: over structuring, where the framework is so visible the thinking disappears behind it.

**Rubric tuning.** Dimensions two through five: problem framing, user insight, tradeoffs, and metrics. The unforgiving pair is problem framing and tradeoffs. Metrics is where prepared candidates score well and it is rarely what separates them.

This is also where the thirty minutes of using the product, described in Deep Dive 1, pays back most directly. PM Jordan walking through Northwind Payments' merchant onboarding, timing it, and noticing that step four asks for the same information twice arrives with a first hand observation nobody else in the loop has.

---

# Technical Deep Dive

**The decision it makes.** Whether your technical claims are real, and at what depth you can hold a conversation without a document in front of you.

**Who runs it.** A senior engineer, an architect, or a research lead. For technical product roles it is often someone who has been burned by a product manager who could not tell a hard problem from an expensive one.

**What it is really testing.** Two things at once, and candidates usually optimize for the wrong one. The first is depth, checked by following one thread down until you stop, and where you stop is the measurement. The second, often weighted higher, is whether you can explain something complicated to someone outside your background. Engineer Alex, interviewing for a role spanning two teams, gets scored less on the architecture answer and more on whether it would have made sense to the product manager sitting in.

**Failure modes.** Claiming a layer you did not own. Fatal here and only here, because the person across from you can tell inside two follow ups, and once they can tell they discount everything technical you said earlier. Then defensiveness at the edge of your knowledge, when the correct move is to name the edge and say how you would find out. Then explaining upward, using vocabulary to signal seniority rather than transmit meaning. And oversimplifying until the interviewer cannot tell whether you understand it.

**Rubric tuning.** Dimensions two through five: technical depth, system thinking, risk awareness, and explaining complexity to a non specialist. The unforgiving pair is technical depth and risk awareness, the second because someone who cannot name the failure mode of their own design is the specific person this round is built to find.

Tell your simulator to run the honesty probe deliberately: pick one thing you claimed, follow it down four levels, and score how you handled the level where you ran out. The highest value drill for this round type.

---

# Executive and Panel

**The decision it makes.** Whether to make the offer, and at what level. By the time you are here the functional questions are mostly settled, and the round is about scope, judgment, and whether the room believes you can operate at the altitude the title implies.

**Who runs it.** A skip level, a peer director, a functional leader from an adjacent organization. Three on the invite is the usual shape, frequently comparing notes against criteria they never agreed on.

**What it is really testing.** Whether you can compress. Executives ask questions that could take twenty minutes and want ninety seconds with the conclusion first. Underneath that they are testing decisiveness under incomplete information, the actual job, and whether you can be disagreed with in front of other people without folding or escalating. The panel format is part of the instrument: three people means interruption, competing agendas, and redirecting an answer mid sentence when a second person takes it somewhere else.

**Failure modes.** Answering an executive question at operational depth, which reads as level mismatch rather than thoroughness. Talking to only one person on the panel, usually the friendliest. Losing the thread when interrupted. Hedging on a direct question, because "it depends" with no follow through is scored as an inability to decide. And going long, which in a panel costs you two questions rather than one.

**Rubric tuning.** Dimensions two through five: scope, strategic framing, stakeholder handling, and decisiveness under incomplete information. The unforgiving pair is scope and decisiveness. A two on scope is a level downgrade, and a two on decisiveness is usually a no.

Build the persona as three separate voices with different priorities and let them interrupt each other. A panel simulated as one polite interviewer trains you for a round that will not happen.

---

# Peer and Cross Functional

**The decision it makes.** Whether the people who will work with you every week want to. It is often described as informal and it quietly kills candidates, because a peer's objection is hard to overturn and rarely written down in a way you could argue with.

**Who runs it.** Someone at your level in a function that is not yours: an engineer, a designer, a data scientist, an operations lead.

**What it is really testing.** What you are like when you are the obstacle. Peers are not evaluating whether you are impressive. They are simulating the worst Tuesday they will have with you: the week the deadline moves, the week your priorities and theirs disagree, the week their work slips and you decide what to tell your stakeholders. They are also listening to how you describe engineers, designers, and analysts you have worked with, because how you talk about the last one predicts the next.

**Failure modes.** Credit drift, where the story slowly becomes yours as you tell it. Peers detect this best and forgive it least. Describing another function's work as an input rather than as work, a small phrasing habit with a large signal attached. Talking about conflict as something you resolved by being right. And overclaiming technical depth to an engineer, which converts a friendly round into an interrogation.

**Rubric tuning.** Dimensions two through five: collaboration under friction, credit and attribution, handling disagreement, and clarity across functions. The unforgiving pair is credit and attribution and handling disagreement. Note that metrics barely matters here, the trap for a candidate who has drilled the case round and arrives quantifying everything at a person who wanted to know what you are like to be blocked by.

---

# Appendix: The Recruiter Screen

**The decision it makes.** Whether you move forward at all, plus two logistics facts the recruiter needs before they can advocate for you. It is a filter, not an evaluation, and the difference matters.

**Who runs it.** A recruiter or a talent partner, usually twenty five to thirty minutes, usually the first conversation.

**What it is really testing.** Coherence and level. Can you say what you do, why you are looking, and why this role, in a way a non specialist can repeat accurately to a hiring manager two hours later. That last clause is the whole round. The recruiter is a relay, not the audience.

**The depth ceiling.** This makes the recruiter screen different from every other round here, and it is the one constraint your simulator has to enforce against you rather than for you. Over rotating into deep technical or strategic answers is not neutral, it is negative: it signals someone who cannot read a room, burns twenty five minutes on material the recruiter cannot evaluate, and stops them getting the facts they need. The rule is one level of depth, then stop and check. Asked what they did at their last company, PM Jordan answers for about ninety seconds and ends with an offer rather than a second paragraph: "I can go deeper on the fraud side if that is useful."

Write it into the simulator explicitly: this persona is a recruiter, not a technical evaluator, and any answer over ninety seconds or any technical detail beyond one level gets penalized and named as over rotation. Without that instruction the model rewards depth, because depth is what it rewards everywhere else.

**The logistics questions, which are scored.** Compensation expectations, notice period, location and any in office expectation, work authorization, and whether you are in other processes. Nobody calls these scored and they are. A wandering or evasive compensation answer costs you standing at the start of the loop, where you have no other evidence in the bank. Prepare them as verbatim lines on the opening cheat sheet, and practise saying the number without qualifying it into a paragraph.

**Rubric tuning.** Dimensions two through five: narrative coherence, level and depth control, motivation, and logistics handling. The unforgiving pair is depth control and coherence, and this is the only round where a dimension exists to stop you doing something rather than to measure you doing it.

---

# Working Out Which Round You Are Actually In

Half the time the invitation does not say. Here is how to read the signals, in rough order of reliability.

**Who is on the invite, and what they do.** The strongest signal available, at one search each. Three people including someone two levels above the role is an executive panel whatever the calendar entry says. One senior engineer and nobody else is a technical deep dive. A product manager at your level from a team you would not report to is a peer round.

**The length.** Twenty five to thirty minutes cannot be a case. Sixty minutes with one person is either a deep dive or a hiring manager round that expects real material. Ninety minutes is usually two rounds stitched together, so ask which halves.

**How the recruiter described it, including the parts they hedged on.** "Just a chat" almost never means an unstructured chat, but it does reliably mean the round is not a case. "They will want to go deep on your background" means behavioural. "Bring an example of something you shipped" means portfolio or case, and any request to bring or submit anything converts the round into a case whatever else it is called. Listen for the level word too: if they call the panel "the leadership team," you are being evaluated on scope.

**Where you are in the loop.** Round one is a filter, the last round is a decision, and the middle rounds collect the functional evidence.

Two things worth stating plainly, because they cause more misbuilt simulators than anything else.

**The same person can run different rounds.** The hiring manager who ran your first call as an open conversation may run the third as a structured behavioural interview against a scorecard, with a different posture entirely, because the loop assigns them a different job. Do not build round three's simulator from round one's experience of the person. Build it from the job the round is doing.

**The round type matters more than the person's title.** A director running a technical deep dive is running a technical deep dive. An engineer running a values interview is running a behavioural round. Tune the persona to the human and the rubric to the round, and when the two conflict, the round wins. The persona controls how the questions sound. The round controls what is being scored.

When you genuinely cannot tell, prepare one level harder than you expect. Preparing for an executive panel and walking into a friendly manager chat costs nothing except some tightness in the first answer. The reverse costs you the loop.

---

# When You Prepared for the Wrong Round

You will get it wrong eventually, and you will find out in the first two minutes. Early enough to recover if you move quickly, catastrophic if you spend the round grieving the preparation you did.

**Notice it, and let yourself notice it.** The tell is usually the first question. If you built for a case and the opening is "walk me through a time you disagreed with a stakeholder," that is the round. The failure here is denial: candidates spend three more questions waiting for the interview they prepared for, and answer three badly instead of one.

**Do not announce it.** Nothing good comes from saying you were told this would be a case. It sounds like a complaint, it makes the interviewer responsible for your preparation, and you may have misread an accurate description anyway.

**Fall back to the Story Bank, which is round agnostic.** This is the argument for building it first that you only appreciate once. Your stories work in every round here, and what changes is which part you lead with. In a behavioural round, lead with the decision you personally made. In a case, lead with how you framed the problem. In a peer round, lead with who you had to move. Same material, different entry point, and you can switch entry points live in a way you cannot invent material live.

**Reset your length calibration in the first answer.** Rounds have different natural answer lengths, and that mismatch is more visible than the content one. If you built for a technical deep dive and landed in an executive panel, your first answer will be three times too long. Cut it, mid answer if you have to, land it, and stop.

**Then debrief it as a build defect, not as bad luck.** Write down which signal you misread, or never went looking for. Almost every wrong round traces back to a question that was never asked, and the intake email is four minutes of work.

One last thing, worth knowing because the panic in minute two does the real damage. Preparing for the wrong round is survivable. The research still applies, you still know who is in the room and what they care about, and your stories are still true. What you lost was rehearsal, and rehearsal buys fluency rather than substance. Slow the first answer down, land it, and run the round you are actually in.

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

Based on "Round Types and What Each One Tests," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
