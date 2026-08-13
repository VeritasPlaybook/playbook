>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# The Intelligence Layer

This deep dive expands Steps 4 and 5 of the [main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md), which covered running deep research twice and reconciling the results in about a dozen lines each. This is the longer version: why one confident research pass is more dangerous than none, what each of the five Prompt Library prompts is for, how to make a research tool verify rather than generate, name collision disambiguation, the hard split between verified and inferred claims, negative findings as real findings, two pass cross validation and why the second tool's job is to disagree, the three reconciliation buckets, the do not assert list and its substitute phrasings, harvesting the company's own vocabulary, and the thirty minutes of research no tool can do for you.

Read the main guide first, at minimum Steps 1 through 3. Everything here assumes you have named the round you are preparing for and have some idea who is in the room. Research run before those two answers exist produces a beautifully written brief about an interview nobody is going to give you.

---

# Why One Confident Pass Is More Dangerous Than None

If you do no research at all, you walk in curious. You ask what the team owns. You ask what the hardest problem is right now. You are underinformed, which costs you, but you are not wrong out loud.

If you do one pass and believe it, you walk in asserting. That state damages you, and the cause is the tool rather than you. A research tool writes at constant fluency regardless of the evidence underneath. A claim with three primary sources and a claim assembled from a similar name on a conference roster come back in the same clean sentences, the same measured tone, sometimes the same citation formatting. Nothing visibly separates them, so your confidence tracks writing quality instead of evidence.

The damage arrives at a predictable moment. Suppose PM Jordan, preparing for a round at Northwind Payments, opens by referencing the interviewer's work on a payouts rewrite. The interviewer did not work on that. Someone with the same name, at a different company, did. Three things happen at once. You get corrected, which costs a little standing. You lose your footing, because the opening you rehearsed has just been publicly voided. And for the rest of the hour they discount everything you say about their world, because they have one confirmed data point that your information is unreliable.

The asymmetry is what matters. A question you did not ask costs you a little texture. A false assertion costs the interviewer's trust in your whole model of them, and you cannot repair it inside the hour. Reconciliation in Step 5 is not optional housekeeping. It converts research into something you are allowed to open your mouth about.

---

# The Five Prompts and What Each One Is For

The Prompt Library has five prompts. Four are for a deep research tool, one is an email to a human.

**01, Company and Role.** The problem space. What the company sells, who pays them, how the business model creates the constraints the team lives inside, what changed recently, where the role sits. Run it once per company and reuse it across the loop; company facts do not change between Tuesday and Thursday.

**02, Interviewer Deep Research.** One named human at a time. This prompt most needs a confirmed identity and is the most capable of confident fiction without one. Never batch two people into a single run. Its output feeds the Interviewer Dossier (more on that in Deep Dive 3).

**03, Round Format and Competency Model.** Reconstructs the scorecard: what a company of this shape, at this level, in this function is likely scoring, and what a strong answer looks like on each dimension. It converts preparation from answering questions into covering competencies, a meaningfully different activity.

**04, Cross Validation and Reconciliation.** Run in a different tool, on your load bearing claims only. Its job is described in a later chapter.

**05, Recruiter Intake.** Not a research prompt. Five question email, four minutes of work, and it returns the input everything else depends on: who is in the room. Sending it late is the most common sequencing mistake in this kit.

The honest ranking by value per minute is 05, then 02, then 01, then 03, then 04. Most people running a normal round need three of the five. If your interview is tomorrow, run 05 and 02 and nothing else.

---

# Prompting for Verification Rather Than Generation

## State the belief you are testing

Most people use a research tool to summarize. Summarization is generation, and generation is where fabrication lives, because a model asked to produce a career history will produce one whether or not the evidence supports it.

What changes output quality most is stating your belief in the prompt and asking the tool to confirm or refute it. Instead of "tell me about the director of risk platform at Northwind Payments," write: "I believe this person spent most of their career in fraud operations before moving into product, and joined Northwind Payments within the last two years. Confirm or refute each claim separately, with sources. If you cannot confirm a claim, say so and tell me what you found instead."

Three things change. The tool has a falsifiable target rather than an open ended writing task. It will tell you when you are wrong, the most valuable output available, and it cannot do that if you never said what you thought. And you get a structured answer per claim instead of a narrative where every sentence carries the same implied confidence.

You are not fishing for agreement. You want the run that comes back saying your second claim is unsupported and here is why. That run just saved you an opening line.

## Name the people who are not your interviewer

If your interviewer has a common name, say so explicitly and describe the other people. Something like: "There is a well known academic with this name in a different field, and at least one person with this name in logistics. My interviewer is neither. Mine is at Northwind Payments in a payments risk function. Do not merge biographies. If a source is ambiguous about which person it refers to, mark it ambiguous rather than assigning it."

Do this even when you think the name is unusual, because you will discover it is not. Carry the exclusions forward into the dossier as an explicit do not merge list, so a fresh thread three days from now does not quietly reintroduce the person you ruled out.

---

# The Split, and What Counts as a Finding

## Verified and inferred, never blended

Every research output must come back in two clearly separated sections. VERIFIED means there is a source and it is linked. INFERRED means the tool reasoned its way to the claim, with the reasoning shown so you can judge it.

The instruction has to be in the prompt, and enforced. If the output arrives as a smooth narrative with citations sprinkled through, do not untangle it yourself. Ask again, bluntly: split this into VERIFIED with links and INFERRED with your reasoning, and move anything you cannot link into INFERRED. A blended narrative is the most common way an unsourced guess ends up in your dossier wearing the clothes of a fact.

Inference is not the enemy. "This team is probably measured on approval rate rather than raw fraud loss, because the public job posting emphasizes merchant experience" is worth writing down. It is useful because it is labelled, so you treat it as a hypothesis to test in the room rather than a fact to assert in it.

## Searched, not found

Instruct the tool to report negative findings, phrased as "searched, not found" rather than "does not exist." The distinction is not pedantry. "Does not exist" is a claim about the world the tool has no standing to make. "Searched, not found" is a claim about the search, which is exactly what it can know.

A tool that never returns an empty result is not searching, it is composing. Once you start demanding negative findings you will notice which tools produce them and which never do, and that alone will change which one you trust.

Negative findings are also directly actionable. An interviewer with almost no public footprint is telling you something real: they do not expect you to have read their work, and referencing a half matched item you dug up is a larger risk than saying nothing. Record the empty searches in the Sources section so nobody, including future you, redoes them next week.

---

# The Second Pass, Whose Job Is to Disagree

Run the same core prompts in a second tool. Different vendor, not a second thread in the same tool. Running the same model twice reproduces the same errors with more confidence, which is worse than not checking, because now you feel checked.

Say this out loud when you set it up, because it changes how you read the second output: the second tool's job is not to be better. It is to disagree. You want the places where two independent processes reached different conclusions, because that is where at least one is wrong, and you now know where to spend attention.

This is why the second pass can be shallower than the first and still work. A free tier assistant with weaker search is a fine disagreement engine. It will miss things the primary pass found, and missing is not contradicting. You care about the subset where it asserts something incompatible.

Scope it deliberately. Do not re-run everything. Run it on the claims you plan to say out loud: the interviewer's role and tenure, the team's ownership, the product change you were going to open with, and any number you intend to quote. Ten load bearing claims is a normal list. Everything else stays unverified, because you were never going to assert it.

---

# Reconciliation, and the Three Buckets

Sort every meaningful claim from both outputs into exactly one of three buckets. Twenty minutes, and it is the step people skip.

**AGREED.** Both passes found it, and at least one pointed at a primary source. Promote these into the Company Brief and the Interviewer Dossier as fact. You may say them out loud without hedging. This bucket is usually smaller than people expect, which is the useful part.

**CONTRADICTED.** The two passes disagree. Do not average them, do not pick the more confident one, do not pick the one you prefer. Assign each contradiction to a human who can settle it. Panel composition, round length, and format go to the recruiter, who answers in one line. Facts about a person's own history go to that person, asked lightly in the room, phrased so a wrong guess costs nothing. Anything you cannot assign to a human gets demoted to unverified.

**UNVERIFIED.** One pass asserted it and nothing corroborates it. This bucket is not a list of things that are false. It is a list of things you do not get to assert. Most of it is probably true, which is exactly why it is dangerous: plausibility is what makes you say it.

Write the buckets down in the file. Not in your head. In minute twelve of the real round, under pressure, your memory will happily promote an unverified claim to a fact, and the only defence is having written it in the other column while you were calm.

---

# The Do Not Assert List

Striking a claim is not enough. Delete an unverified fact and you have removed it from the document but left it in your head, and under pressure you will reach for it. The repair is a section called **Do not assert**, where every entry gets a safe substitute phrasing you have rehearsed.

The substitution follows one pattern: convert the claim into a question. "I read that your team owns the risk platform" becomes "I could not tell from the outside how ownership splits between risk and payments engineering. Is that on your side of the line?" The first is a landmine. The second costs nothing if you are wrong, sounds like someone who reads carefully and knows the limits of outside information, and often produces a better answer than the fact you meant to assert, because they explain the real structure.

One more worth having ready: "since you led the migration" becomes "I may have this out of date, was the migration your team's or a partner team's?"

Then give yourself written permission to say "I do not know, and I do not think that is public." Write it on the cheat sheet as a verbatim line. It reads as senior, it is true, and people are strangely afraid of it. Bluffing reads as junior and is detectable inside one follow up question.

---

# The Research No Tool Can Do for You

**Harvest their vocabulary.** As you read the company's own material, keep a running list of the exact words they use: merchants or sellers, disputes or chargebacks, partners or clients, incidents or events, guardrails or controls. The list takes five minutes and is worth more than most of the analysis around it, because mirroring an organization's internal vocabulary makes you sound like someone already in the building. Using the wrong term for their core object is a small, constant signal that you are outside.

**Notice the contradictions inside their own material.** The careers page, the documentation, the engineering blog, and the most recent announcement were written by different people at different times and often do not agree. A real one is worth raising out loud, carefully and with no implication of a gotcha. Saying "the documentation describes settlement as next day, and the newer announcement implies same day for some flows, I could not work out whether that is a rollout or two products" proves what no amount of preparation language can prove: you read the actual thing, not a summary of it.

**Do the thirty minutes nobody else does.** Sign up for the product. Walk the flow end to end. Time yourself. Screenshot the friction. Get to the point where you had to guess what a button did, and write down your guess and what it did. If the product is not self serve, get as close as you can: the sandbox, the public documentation, the pricing page, the support forum.

No research tool can do this, and that is the point. A tool can tell you the company has a merchant onboarding flow. Only you can tell them onboarding asked for the same information twice, that step four took six minutes, and that you assumed the verification email had failed when it had not. That is a first hand observation about their product the person across from you has probably heard from customers and certainly never from a candidate. For a product sense or case round it is the highest value half hour available.

---

# Knowing When the Research Is Done

Research is the most comfortable part of preparation, and comfort is why it expands. Reading is calm, ordered, and produces the reliable feeling of progress. Saying an answer out loud and being told it was ninety seconds too long is none of those things. So people research until the interview arrives and call it preparing.

The stopping rule is simple. The intelligence layer is done when it can answer four questions: what problem does this company have that this role exists to solve, what is this round scoring, who is in the room and what does each of them care about, and what am I not allowed to assert. When those four are answered, stop. Everything past that is decoration.

Three signals that you have crossed from research into procrastination. The first is that new sources stop changing anything and you are reading a fourth article confirming what you already wrote down. The second is that your notes have grown past what you could act on. If the brief is fifteen pages and the cheat sheet is empty, you have been collecting rather than preparing. The third and most reliable is that you have not said a single answer out loud. Any hour on the eighth source before the first spoken rep is an hour in the wrong place, because the failure modes that lose rounds are delivery failures and none show up in a document.

There is a floor here too. If you cannot identify who is in the room, skip the interviewer research rather than running it on a guess, and spend the time on the competency model, which does not require a name.

One last thing. Research makes you fast and difficult to rattle. It does not make you qualified. If you are researching to feel ready rather than to answer one of those four questions, close the tab, open the simulator, and take the first rep badly. The rep will tell you what the research was missing, a better brief than any you could write from the outside.

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

Based on "The Intelligence Layer," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
