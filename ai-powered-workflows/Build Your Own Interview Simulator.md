>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List

---

# Why I Built This

I wanted to see how far I could push this. Not whether an assistant could write me a cover letter, which is a boring question with an obvious answer. Something harder: could I build myself a real edge in an interview, against a specific company, a specific round, and a specific named person, out of nothing but research, a folder of files, and a model patient enough to run the same drill six times without sighing.

It worked. Well enough that I kept building them, and well enough that I am publishing this.

I was interviewing a lot at the time, and somewhere in there I noticed something that bothered me.

I was good at the job and mediocre at the round. Those are different skills. The round is a performance with a scoring rubric you never see, run by people whose priorities you can usually infer but rarely confirm, about work you did years ago and have not described out loud since. I would leave an interview knowing I had told the right story badly, or the wrong story well, and I would not find out which until the rejection email came with no detail in it.

The standard advice is "practice with a friend." I tried that. My friends are busy, they do not know the company, they do not know what a research director cares about versus what a skip level executive cares about, and they are too kind to tell me my third answer went ninety seconds too long. The other standard advice is to buy a list of "top fifty product manager interview questions," which is fine if you enjoy rehearsing for an interview nobody is actually going to give you.

What I wanted was narrower and harder: practice against **this** round. This company, this stage of the loop, this named person with this career history and this visible worldview. Graded, honestly, by something that would not spare my feelings and would tell me the same thing three times if I kept making the same mistake.

So I built one. Then I built another, because the second round of the same process needed different things. By the time I had built seven of them across several companies, the shape had stopped changing, and I realized I had a system rather than a pile of documents. Then two friends asked me to build one each, and building it for someone else forced me to solve the parts I had been getting away with because they lived in my head.

I am publishing it because of what happened after the last guide. People who used the resume workflow in this repository started telling me they were getting interviews, which was the point. Then the messages changed. Getting the interview turns out to be the easy half, and what people wanted help with next was the round itself: what to say, how to prepare, why the second one went worse than the first. Resume, then interview. This is the next step in the same sequence and it was the obvious thing to write.

This guide is that system, generalized so you can build your own. I built the first version for two friends. It is free and open source, and so is everything it depends on.

A word on what it is not. It is not a way to get an offer you do not deserve. The research makes you fast and difficult to rattle. The judgment still has to be yours, and if you outsource the thinking you will discover that in minute forty of a real interview, in front of people whose entire job is noticing exactly that.

---

# Why This Works

**Rehearsal beats review.** Reading your own notes creates a feeling of readiness that does not survive a real question. Saying an answer out loud, badly, in a low stakes setting, then being told precisely why it was bad, is the only thing I have found that changes what comes out of my mouth under pressure. The system produces reps, not documents.

**Specificity is the whole game.** A generic mock asks "tell me about a time you influenced without authority." A useful mock asks it in the voice of a peer product manager who spent six years at a consultancy, who will interrupt you at the forty second mark, and who is quietly checking whether you will take credit for your team's work. The second one is uncomfortable in the same way the real thing is. That is the point.

**The artifact is what improves, not your memory.** This is the piece almost nobody does, and the reason this system compounds. When a mock goes badly, the fix is not "remember to do better next time." The fix is an edit to a document: a missing card gets added to your cheat sheet, a story gets a closing line it did not have, a trigger phrase gets mapped to the right story. You are running a test suite. Your performance is the instrument reading. The artifact is under test, and it gets a version number.

There is real evidence behind the underlying pattern. Retrieval practice, testing yourself rather than rereading, produces substantially better recall than review, and the effect is strongest when retrieval conditions resemble the real ones. Spacing reps across days beats cramming them into one. And feedback naming one specific correction beats feedback listing everything wrong, because a person under pressure can only hold one repair in working memory at a time. The design choices here, one question at a time, one highest leverage fix per run, and a run log that spaces reps across a week, are all downstream of that.

---

# How This Compares to What You Might Already Use

**Versus a question list.** A list of common questions is a starting input, not a system. It has no model of who is asking, no way to tell you your answer was structurally fine but forty seconds too long, and no memory of what you already drilled. This system consumes question lists as raw material and does the rest.

**Versus a paid interview coach.** A good coach is genuinely better than this at reading you as a person, and if you can afford one for the round that matters most, use one. What a coach will not do is run with you at eleven at night for the fourth time that day, hold a hundred pages of research on one company in working memory, or remember that you have failed the same closing beat five reps running. Use both if you can. If you can only use one, this one is free and infinitely patient.

**Versus a friend running a mock.** Your friend cannot play a research director whose published work you read yesterday. Your friend also cannot grade you against a six dimension rubric without it getting weird. Save them for what they are actually good at, which is telling you whether you sounded like yourself.

**Versus just talking to an Artificial Intelligence (AI) assistant without any of this.** This is the closest substitute and the one most people default to. Opening a chat and typing "interview me for a product manager role" gets you a generic interviewer with no persona, no research, no rubric, no memory between sessions, and a strong bias toward telling you your answer was great. Every piece of scaffolding in this guide exists to defeat one of those five failures.

**A note on tools:** This guide is written for Claude inside the desktop app's Cowork mode, because that is what I use and have tested. The underlying pattern, a research layer feeding a persona driven rehearsal loop that writes its findings back into files, is not locked to Claude. Deep Dive 10 covers running the same system in ChatGPT Projects, and the prompt patterns transfer with minor edits. Adapt as you see fit.

---

# When and How to Use This

**You have an interview booked and more than two days.** This is the main case. Build the full thing. Two to four hours of setup buys you unlimited reps.

**You have an interview tomorrow.** Do not build the full thing. Read the QUICKSTART file, do the ninety minute version, and skip the Story Bank refinement. A rough simulator you actually run twice beats a beautiful one you finish at midnight.

**You are deep in a loop and round two just got scheduled.** This is where the system pays for itself. Round one's transcript is the best intelligence you will ever get about round two, and the debrief step turns it into the next build automatically.

**You are helping someone else prepare.** Read Deep Dive 9 first. Building for another person is a genuinely different problem, mostly because their stories live in their head rather than your files, and because they will not read anything longer than one page before they start.

**You do not have an interview yet.** Build the Story Bank anyway. It is the slowest part, it is reusable across every company you will ever talk to, and everything else sits on it.

---

# What This System Actually Does

![The five layers of the system. Layer one, intelligence: what you know about the company, the round, and the people. Layer two, material: what you can actually say, sourced and defensible. Layer three, rehearsal: the bot that runs the mock and grades it. Layer four, glance: what you look at during the real call. Layer five, loop: what survives the round and seeds the next one.](./img/interview-five-layers.png)

![The full loop. Recruiter intake feeds deep research run twice, which feeds reconciliation, which produces the Company Brief and Interviewer Dossier. A separately built Career Brain Trust feeds the Story Bank. Both feed the simulator, which produces a graded run, which produces a new version of the cheat sheet, which sends you back to run the simulator again. After the real round, debrief and handoff seed the next round.](./img/interview-loop.png)

**Recruiter intake** is the five questions you ask the recruiter that determine what you build. Skipping this is the most common way people prepare beautifully for the wrong interview.

**Deep research, run twice** produces raw intelligence about the company, the role, the round format, and the named humans. Two independent passes, so you can tell a fact from a plausible sentence.

**Reconcile** sorts every claim into agreed, contradicted, and unverified, and the unverified list becomes an explicit "do not assert this out loud" section. That keeps the research from making you confidently wrong in the room.

**The Company Brief and the Interviewer Dossier** are the refined outputs. The brief is about the problem space. The dossier is about a person, and its job is to convert them into a posture.

**The Story Bank** is your material: five to nine stories, sourced from your Career Brain Trust, each with real numbers you can defend under follow up.

**The Simulator** is one markdown file containing the interviewer persona, a tagged question bank, a scoring rubric, the run modes, and an append only run log. It is the bot.

**The graded run** produces six scores, exactly two things that worked, exactly one highest leverage fix, and a note about which artifact failed you.

**The cheat sheet** is the only thing you look at during the real call. It is a glance tool, not a study document, and it gets a new version after every rep that exposes a hole in it.

**Debrief and handoff** capture what was actually asked, what was conspicuously not asked, and what the interviewer accidentally told you about the next round.

---

# What You'll Need

| Thing | Why | Required? |
|---|---|---|
| Claude Pro or Max, with Cowork mode | Runs the simulator, reads and writes the folder | Yes |
| A folder on your computer | Everything lives in files, not in chat history | Yes |
| A deep research tool | Building the intelligence layer | Yes, unless you use the workaround below |
| A second, different research tool | The cross validation pass | Recommended |
| A Career Brain Trust | The source of your stories and numbers | Recommended |
| A recruiter you can email | Five questions that shape the whole build | Recommended |
| A second screen or a phone | Reading the cheat sheet during the call | Optional |
| A way to record and transcribe the real round | The debrief step is far better with a transcript | Optional |

**Total recurring cost beyond your Claude subscription:** $0 to $20 per month. If you have Claude Pro or Max, Claude's own research mode covers the deep research and you can skip a second subscription. If you want the two pass cross validation without a second paid tool, run the second pass in the free tier of a different assistant. It will be shallower, which is fine, because its job is to disagree with the first pass, not replace it.

**No deep research subscription at all? There is a workaround.** You can approximate deep research inside an ordinary chat by following [A Practical RLM-Inspired Workflow for Deep Research with AI](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/A%20Practical%20RLM-Inspired%20Workflow%20for%20Deep%20Research%20with%20AI.md), with the [Quick Reference Guide - 7 Phase Manual Deep Research Workflow](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Quick%20Reference%20Guide%20-%207%20Phase%20Manual%20Deep%20Research%20Workflow.md) as the condensed version. It will not match a dedicated deep research tool one for one, and it burns tokens noticeably faster, but for interview preparation it is good enough.

**Do not have a Career Brain Trust?** Build one. It is [the companion guide in this repository](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md) and the highest leverage two hours in this system, because it is the only artifact reusable across every application and every interview you will ever do. If you cannot spare the time before this interview, the Story Bank template in this kit will work from your resume alone, and it will mark every place where it is missing a real detail and interview you to fill it in.

**Technical comfort level:** If you can create a folder, copy files into it, and paste a block of text into a chat window, you can do this. Nothing here requires code.

**Time investment:** Two to four hours to build the first one. Forty five minutes for every one after that, because the Story Bank and the prompt library carry over. Each mock run is twenty to sixty minutes depending on the mode.

---

# The Steps

## Step 1: Name the round you are actually preparing for

**Why this matters:** "I have an interview at Northwind Payments" is not something you can prepare for. A thirty minute first call with a hiring manager, a sixty minute product sense case with two people, and a forty five minute executive panel with three are completely different events that reward different behaviours, and preparing for the wrong one is worse than preparing lightly for the right one. I have watched it happen. Someone builds a beautiful case interview simulator and walks into a round that turns out to be entirely behavioural.

**What to do:**

1. Write down, in one line each: who is in the room and their function, how long the round is, what the recruiter called it, whether it is live or a take home, and what decision it makes in the funnel.
2. Mark every one you are guessing at. Those are your intake questions for Step 2.
3. Pick your build size. If the round is short and the question set is knowable in advance, you want a **Mock Kit**, which is light. If the round is long, open ended, and your real risk is the interviewer going anywhere, you want a **Super Simulator**, which is heavy. Deep Dive 4 has the full decision table, but the short version is that the failure mode you fear tells you which to build: fear bad delivery, build a Mock Kit; fear a topic you never touched, build a Super Simulator.

![Choosing between the two builds. The question is what failure you are afraid of. If you fear bad delivery and roughly know what will be asked, build a Mock Kit: one interviewer or a short round, a knowable question set, 45 to 60 minutes to build. If you fear a topic you never touched and the round could go anywhere, build a Super Simulator: a panel or a long open ended round, multiple personas and a tagged bank, 2 to 4 hours to build.](./img/interview-build-size.png)

## Step 2: Ask the recruiter the five questions that shape the build

**Why this matters:** Recruiters will tell you an astonishing amount if you ask plainly, and almost nothing if you wait to be told. They are also on your side, structurally, because they do not get credit for candidates who fail. The cost of asking is one short email. The cost of not asking is building the wrong simulator.

**What to do:**

1. Send the five questions. In priority order: who exactly is in this round and what do they do, what is the format and how long, what is being assessed, is there anything I should prepare or bring, and how does this round fit into the rest of the loop.
2. Ask the process questions, not the product questions. A recruiter can tell you the panel is a skip level plus two peers. They usually cannot tell you the team's technical roadmap, and asking makes you look like you are auditioning at the wrong person.
3. Listen past the answers. If they describe the panel as "the leadership team," that is a level signal. If they use the company's internal vocabulary without noticing, that vocabulary is worth mirroring. If they volunteer that the last three candidates struggled with something, that is the whole interview.
4. Write the answers straight into your anchor file, verbatim where possible, including the parts they hedged on.

> **[Deep Dive: Round Types and What Each One Tests](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/08%20-%20Round%20Types%20and%20What%20Each%20One%20Tests.md)**

## Step 3: Set up the folder and the anchor file

**Why this matters:** Chat threads die. They run out of context, you close the window, the tool restarts, and everything the assistant learned about your round evaporates. Every durable version of this system I have built keeps its state in files, so any fresh thread can be brought up to speed with one paste. The anchor file makes that possible, and it is the first file you create and the last one you update.

**What to do:**

1. Create one folder per round. Not per company, per round. Name it `[Company] - [Round Label]`, for example `Northwind Payments - Hiring Manager Round`.
2. Copy the templates from this kit into it.
3. Fill in `_STATE.md` with what you know so far, including the parts you do not know. The unknowns are content, not gaps.
4. Connect the folder to a project in your assistant so it can read and write files there.
5. Get in the habit now: every session ends by telling the assistant to update `_STATE.md`. It takes ten seconds and it is the difference between a system and a pile of chats.

> **[Deep Dive: State, Handoff, and Multi-Round Campaigns](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/05%20-%20State,%20Handoff,%20and%20Multi-Round%20Campaigns.md)**

## Step 4: Run the deep research, twice, in two different tools

**Why this matters:** Research tools are confident. They will hand you a career history for a person with a common name that is actually three people's careers stapled together, and they will do it in clean prose with citations. If you carry that into an interview and refer to something the person never did, you have converted preparation into damage. Running two independent passes and comparing them is the cheapest available protection.

**What to do:**

1. Use the prompt library in this kit. Five prompts: the company and role, the named interviewer, the round format and competency model, the cross validation pass, and the recruiter intake. Run the first three in your primary research tool.
2. Inside the interviewer prompt, state what you believe about the person and ask the tool to confirm or refute it. A research tool asked to verify a stated hypothesis is far more useful than one asked to summarize, because it will tell you when you are wrong.
3. Warn it about name collisions explicitly. If your interviewer shares a name with a public figure, say so, describe the other person, and instruct the tool to keep them separate.
4. Demand the output be split into what is verified with a source link and what is inferred with the reasoning shown. Refuse output that blends them.
5. Run the same three prompts in a second, different tool. You are not looking for a better answer. You are looking for disagreement.
6. Do the thirty minutes of research nobody else does: use the product. Sign up, walk the flow, hit the friction, screenshot it, time yourself. For a case or product round this is the highest value half hour available to you, and the one thing no research tool can do for you.

> **[Deep Dive: The Intelligence Layer](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/01%20-%20The%20Intelligence%20Layer.md)**

## Step 5: Reconcile the two passes and write down what you must not say

**Why this matters:** The output of Step 4 is raw material with an unknown error rate. This step converts it into something you can safely open your mouth about. It takes twenty minutes and it is the step people skip.

**What to do:**

1. Sort every meaningful claim into three buckets. **Agreed** means both passes found it and at least one cited a primary source. **Contradicted** means the passes disagree. **Unverified** means one pass asserted it and nothing backs it up.
2. Promote the agreed claims into your Company Brief and Interviewer Dossier as fact.
3. Assign the contradicted ones to a human. Your recruiter can confirm the panel composition. The interviewer can confirm their own history, gracefully, if you ask lightly rather than asserting.
4. Write the unverified ones into a section called **Do not assert**. For each one, write the safe substitute phrasing. "I read that your team owns the risk platform" becomes "I could not tell from the outside how the ownership splits, is that your team?" That reframe converts a landmine into a good question.
5. Give yourself permission, in writing, to say "I do not know, and I do not think that is public." It is a genuinely strong answer and people are weirdly afraid of it.

## Step 6: Build the Story Bank

**Why this matters:** Everything above is about them. This layer is about you, it is what actually gets scored, and it carries over to every future interview you will ever do. If you build nothing else in this kit, build this.

**What to do:**

1. Start from your Career Brain Trust if you have one. The Story Bank is a new layer on top of it, not a replacement: the Brain Trust holds canonical, verified bullets per role, and the Story Bank re-cuts that material into spoken narratives tagged by what they prove.
2. Aim for five to nine cards. Three of them will do most of the work. Rank them and know which three.
3. Build each card to the ten element checklist: hook, situation and stakes, the ambiguity, your assessment, **the decisions you personally made**, what you built and who did what, how you communicated across functions, the result with real numbers, the reflection, and the competency tags. Element five is the seniority signal and the one most people leave out.
4. Make the assistant interrogate you rather than write for you. Give it the raw story however it comes out, let it name which elements are thin, and answer two to four focused questions at a time. Do not accept a story it wrote from your resume, because you will not be able to defend it.
5. Harden the numbers. Every metric gets checked and, where it was inflated, corrected downward to something you can survive a follow up on. A defensible smaller number beats an impressive one that collapses.
6. Build the coverage map. Each card owns two or three competencies. Between them, the set must cover everything the round will test. If a competency has no card, that is your gap and the first thing to fix.
7. Write one failure card. What you assumed, what happened, what you own, what you changed, and end on the lesson, not the grievance. You will be asked. Everyone is asked.

> **[Deep Dive: The Story Bank](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/02%20-%20The%20Story%20Bank.md)**

## Step 7: Build the simulator

**Why this matters:** This is the file that turns everything above into reps. It is one markdown document, and its structure stops the assistant from drifting into a friendly chat that tells you every answer was strong.

**What to do:**

1. Write the interviewer persona using four fields and no more: who they are, what they test, what wins them, and what loses them. Four fields is enough for the model to hold a distinct voice. A long personality essay is not better, it is just longer.
2. Constrain what the persona knows. Decide whether this interviewer has read your resume. If they have not, forbid the simulator from referencing anything you have not said out loud. Otherwise you rehearse a fantasy in which the interviewer already understands your background, and that fantasy removes the exact skill you need to practise, introducing your background unprompted.
3. Write the scoring rubric before you write the questions. Six dimensions, scored one to five, with the last always communication and presence. The rubric converts vibes into a signal you can act on.
4. Build the question bank with identifiers and tags. Every question gets a short identifier, a topic tag, and a difficulty tier. That sounds fussy and it is what makes run five harder than run two instead of identical to it.
5. Write the run modes. At minimum: a realistic full length run, a coaching run where the bot can break character to teach, and a rapid fire run that trains crispness. Deep Dive 4 has the full mode menu.
6. Add the four rules that do more work than everything else combined:
   - **One question per turn, then stop and wait.** No stacking. A real interviewer does not fire two questions at once, and a stacked question lets you dodge the harder one.
   - **No hints.** The bot must not tell you which story to use or scaffold your answer. Scaffolding hides exactly the defects you are trying to find.
   - **Grade at the end, not after each answer.** Feedback after every answer contaminates the next one and destroys realism.
   - **Ignore transcription artifacts.** If you dictate, tell the bot to grade substance and intent and never flag a garbled word. Otherwise it will spend its feedback budget on your microphone.
7. Add an empty run log section at the bottom. The bot appends to it. You do not.

> **[Deep Dive: Simulator Architecture](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/04%20-%20Simulator%20Architecture.md)**

## Step 8: Run mocks, out loud, and let it grade you

**Why this matters:** Typing your answers feels like practice and is not. The failure modes you need to find are all delivery failures: running long, burying the headline, trailing off without landing, answering the neighbour of the question that was asked. None of them show up when you type, because typing lets you edit.

**What to do:**

1. Use the kickoff prompt. It is a short separate file whose whole job is to be pasted into a fresh thread. It tells the bot what to read, in what order, and what to do before it starts.
2. Say your answers out loud. Use dictation, or talk and transcribe, or record yourself. Whatever it takes, do not type.
3. Let the bot ask its two scoping questions at the start: coaching or realistic, and short or full length. Then let it run.
4. Take the grade seriously and take exactly one thing from it. Six scores, two things that worked, one highest leverage fix. Not a list of fixes. One. A list is a way of ignoring all of them politely.
5. Space your reps. Three runs over three days beats five in one evening, by a wide margin.
6. Watch for overcorrection. If you drill "lead with the number" for four runs, expect a fifth run where you lead with a number on a question that did not want one. The fix is never more drilling, it is a discriminator: a rule that tells you when the move applies and when it does not.

> **[Deep Dive: Scoring and the Feedback Loop](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/06%20-%20Scoring%20and%20the%20Feedback%20Loop.md)**

## Step 9: Build the cheat sheet from whatever the mocks broke

**Why this matters:** Here is the reframe that makes this different from every other preparation method I have tried. The mock is not the product. The mock is a test harness, and the thing being tested is your cheat sheet. Every run should produce at least one note of the form "the sheet did not have what I needed here." That note becomes an edit. The sheet gets a version number. Over five runs it goes from a document you wrote to one that has survived contact.

![What happens to a defect. Run a mock, take one highest leverage fix, name the artifact that failed, edit it and bump the version. The next run re-tests it. If the fix held, mark it closed and locked. If it fired on the wrong trigger, that is overcorrection, and the repair is a discriminator rather than more drilling.](./img/interview-fix-lifecycle.png)

**What to do:**

1. Build it as a single self contained HyperText Markup Language (HTML) file with tabs, not as markdown. You will be reading it on a second screen while talking, and scrolling to find something is a failure. The template in this kit is one file with no dependencies.
2. Put only glanceable things on it. Verbatim opening scripts, the headline line for each story, the numbers, your honest boundary lines, the trigger table, and the landmines. Reasoning, question banks, and rubrics stay in the simulator file where they belong.
3. Use one visual treatment per meaning and stay consistent. A green bordered box always means "say this out loud, word for word." A red band always means "do not do this." Under pressure your eye needs to find the right thing in two seconds, and it can only do that if the encoding never changes.
4. Build the trigger table. Left column: phrases you might hear. Right column: which story to lead with. This exists because the most common mock failure is not a bad answer, it is a good answer to a slightly different question.
5. Add the closing beats. Late in my own runs I discovered three of my five stories had no ending, which is why they kept sprawling. Write the last sentence of every story down. Drill the endings, not the openings.
6. Never edit version one. Copy it to version two. You want to see what changed and why.

> **[Deep Dive: The Cheat Sheet](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/07%20-%20The%20Cheat%20Sheet.md)**

## Step 10: Debrief the real round, then hand off to the next one

**Why this matters:** Most people finish an interview, feel a wash of relief or dread, and let the most valuable intelligence they will ever have decay over the next forty eight hours. The interviewer just told you what the team actually cares about, in their own words, in response to your questions. That is next round's build specification and it has a very short shelf life.

**What to do:**

1. Do it within a few hours. Write down the questions in the order they were actually asked, as close to verbatim as you can manage.
2. Log what was **not** asked. If a whole competency you prepared never came up, that is either a signal it is not weighted, or that it is coming in the next round. Either way it changes what you build next.
3. Mine their answers to your questions. This is the gold. How they described the team, what they said the hardest problem is, which words they used repeatedly, what they seemed tired of. Write it down before it fades.
4. Note what you could not remember. Then have the assistant send you a short recall questionnaire a day later, because roughly a third of the round will come back to you once you stop trying.
5. Promote what worked. Any answer that landed gets marked as locked so no future thread rewrites it.
6. Write the handoff file. It is the seed of the next round's folder: the locked decisions, the accuracy guards, the already drilled list, and the read order for a fresh thread.

> **[Deep Dive: State, Handoff, and Multi-Round Campaigns](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/05%20-%20State,%20Handoff,%20and%20Multi-Round%20Campaigns.md)**

---

# Why This Compounds

Only the research stages, recruiter intake through the company brief and the interviewer dossier, are company specific. The Story Bank, the prompt library, the rubric, the cheat sheet conventions, and your own catalogue of recurring mistakes all survive the round they were built for. By the third company, setup is under an hour, and the fourth simulator you build is better than the first not because you got better at building simulators, but because it inherits four rounds of accumulated corrections about how you specifically fail.

---

# What I Learned

**The mock is a test harness, not a performance.** Once I stopped grading myself and started grading the cheat sheet, everything got faster. Your failures become defects with owners and version numbers instead of things to feel bad about.

**One fix per run. Not a list.** A list of six corrections produces zero corrections. I know this because I generated a lot of lists before I noticed I was implementing none of them.

**One question at a time was the highest leverage rule I ever added.** For four runs my simulator stacked two questions per turn and I quietly answered the easier one every time. Real interviewers do not do this. Neither should your bot.

**Do not let it grade you after each answer.** It feels helpful and it destroys the run. You spend the next answer performing for the grader rather than for the interviewer.

**Endings, not openings.** Almost every delivery problem I had was a landing problem. I could start any story well. I could not stop. Write the last sentence of every story down and drill it.

**The interviewer's answers to your questions are the best intelligence in the entire process.** Better than the job posting, better than the research, better than anything the recruiter said. Ask good questions for that reason alone, and write down the answers within the hour.

**Forbid the bot from knowing things you have not told it.** My early simulators played an interviewer who had memorized my resume. That is a fantasy, and rehearsing inside it removed the actual skill I needed, which is introducing my own background unprompted.

**Two research passes, or none.** A single confident research pass is more dangerous than no research, because it makes you assert things. The reconciliation step is twenty minutes and it is not optional.

**Write down what you are not allowed to say.** The "do not assert" list has saved me from three separate confident errors about people I had never met.

**Give yourself written permission to say "I do not know."** It reads as senior. Bluffing reads as junior and it is detectable within one follow up question.

**Watch for overcorrection.** Coaching creates its own failure modes. Anything you drill four times will start firing on the wrong trigger, and the repair is a discriminator, not more repetition.

**Say it out loud.** Every single time I typed my practice answers I got a false positive. Typing lets you edit. Speech does not.

**Space the reps.** Three sessions over three days beats five in one night. This is not a productivity opinion, it is how memory works.

**Building it for someone else exposed everything I was getting away with.** All the parts that lived in my head and not in the files. If you want to know whether your system is real, hand it to a friend and watch where they get stuck.

**The stories are the asset.** Companies change, rounds change, rubrics change. The seven stories you can tell cold, with real numbers, under follow up, do not. Everything else in this kit is scaffolding around that.

---

# Deep Dives

| Guide | What It Covers |
|---|---|
| [01 - The Intelligence Layer](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/01%20-%20The%20Intelligence%20Layer.md) | The five research prompts, two pass cross validation, the reconciliation buckets, and the "do not assert" list |
| [02 - The Story Bank](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/02%20-%20The%20Story%20Bank.md) | The ten element checklist, the interrogation method, coverage mapping, metric hardening, and how it sits on the Career Brain Trust |
| [03 - The Interviewer Dossier](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/03%20-%20The%20Interviewer%20Dossier.md) | Turning a named person into a posture, fact versus inference, name collisions, and the quiet question in their head |
| [04 - Simulator Architecture](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/04%20-%20Simulator%20Architecture.md) | Mock Kit versus Super Simulator, persona construction, tagged question banks, the mode menu, and the remix engine |
| [05 - State, Handoff, and Multi-Round Campaigns](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/05%20-%20State,%20Handoff,%20and%20Multi-Round%20Campaigns.md) | The anchor file, locked decisions, run logs, debriefs, and how one round seeds the next |
| [06 - Scoring and the Feedback Loop](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/06%20-%20Scoring%20and%20the%20Feedback%20Loop.md) | The six dimension rubric, the one fix rule, fix lifecycle tracking, and detecting overcorrection |
| [07 - The Cheat Sheet](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/07%20-%20The%20Cheat%20Sheet.md) | Why HyperText Markup Language (HTML) and not markdown, the semantic classes, trigger tables, and version discipline |
| [08 - Round Types and What Each One Tests](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/08%20-%20Round%20Types%20and%20What%20Each%20One%20Tests.md) | Hiring manager, behavioural, product sense and case, technical deep dive, executive panel, peer, plus the recruiter screen appendix |
| [09 - Building It for Someone Else](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/09%20-%20Building%20It%20for%20Someone%20Else.md) | The onboarding file, the intake conversation, placeholders as instructions, and the authorship handoff |
| [10 - Running It Outside Claude](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/10%20-%20Running%20It%20Outside%20Claude.md) | ChatGPT Projects, and what changes when the assistant cannot write to your folder |
| [11 - What I Learned, Expanded](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/interview-simulator-deepdives/deep%20dives/11%20-%20What%20I%20Learned,%20Expanded.md) | The lessons above, with the runs that produced them |

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

Based on "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0

## Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- LinkedIn: https://www.linkedin.com/in/malocilja/
- GitHub: https://github.com/VeritasPlaybook/playbook
- Investment Research: https://github.com/Veritas-Research/investment-research

*If you found this valuable, star the repo to help others find it.*
