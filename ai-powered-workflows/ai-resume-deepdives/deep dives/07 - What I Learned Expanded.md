>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# What I Learned (Expanded)

This deep dive expands the ["What I Learned"](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md#what-i-learned) section of the main guide. The main guide listed thirteen lessons as bolded one-liners with two or three sentences of expansion each. This is the longer version: each lesson with a story from a real application I sent, lightly anonymized, plus a short note on what to do differently if you are starting from scratch. After the thirteen lessons, a closing reflection covers three things the outline of this guide flagged: the patterns that almost broke the system and how they got fixed, what I would build into a version two if I were starting from scratch today, and the mistakes other people are most likely to make when adapting this system.

If you have not read [the main guide](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md) yet, the lessons will still make sense, but their full meaning is anchored in the workflow the main guide describes. The companies in the stories are disguised. The lessons are not. Each one cost me something real to learn, and they are the deposit I am leaving for the reader who is one step behind me on the same path.

---

## 1. Pushback is a feature, not friction.

The AI that always agrees with you produces the most boring possible output. It will draft what looks like a credible application, you will ship it, and you will wonder why nothing is landing. The first draft is a proposal. It is not a result. The strongest applications I have ever sent were the ones where I argued the most with Claude.

A real example. The first draft of a cover letter for an early-stage payments startup came back too corporate. The voice was hedged. The opener read like a banking application even though I had told the skill the archetype was startup. I pushed back: "a founder reading this would screen me out as too big-company." I asked for three punchier framings of the opener. The version that ended up in the final draft was almost the opposite tone of the first one. Much shorter. Much more direct about what I had actually shipped. The opening line earned its place by being the line a founder would read and want to keep reading.

The mechanic that makes pushback work is straightforward. Tell Claude what is wrong, why it is wrong, and what kind of alternative you want. "Too corporate, give me three punchier versions for a founder reader" is a complete instruction. The skill will produce three credible variants and you pick the strongest. Or merge two. Or rewrite the survivor yourself in your own voice. Either way you have moved off the first draft toward the version that is actually sharp.

**If you are starting from scratch:** treat the first draft as a starting point you are obligated to push back on at least three times before the application is done. Build the habit before you build the rest.

---

## 2. Lock decisions explicitly.

When something works, say "lock that in." When something fails, say "never do that again." Memory turns one-time corrections into permanent rules. Without that step, you will re-learn the same lessons every other week and wonder why the system feels like it is treading water.

A real example. Mid-way through tailoring an application to a major North American bank, I told Claude: for banking applications, always lead the cover letter with regulatory and compliance credentials, not product velocity. Claude saved the rule as a memory and asked me to confirm the lock. I confirmed. Three applications later, on a different banking application, the skill led the cover letter with credentials automatically. I never repeated the instruction. The one-time correction had become a permanent default for that archetype.

This pattern played out a dozen times over the year. Each lock took me five seconds to say and saved me five minutes on every future application of the same type. The compound effect is enormous. By the time I had been at it for two months the system was making the right choice by default on most of the small decisions I used to have to make manually every time.

The verbal cue matters. Saying "lock that in" or "save this as a rule" tells Claude that this is not a one-off preference, it is something that should affect future runs. The skill will confirm and save the rule. If the rule is wrong later (and some of mine were), you remove it the same way: "remove the rule about X." Memory is editable. Use it.

**If you are starting from scratch:** every time you correct Claude on something that you suspect will come up again, name the lock out loud. The five seconds of explicit saving pays back compound interest for the rest of your search.

---

## 3. Build skills, not prompts.

A prompt is a one-shot you have to remember to use. A skill is a reusable workflow that triggers itself when you say the right phrase. Anything you do more than twice should become a skill. The leverage compounds.

A real example. For the first ten or twelve applications, I ran each one with a long custom prompt at the top of every thread. The prompt described who I was, my preferred resume structure, what to exclude, what voice to default to, what the guard rules were. By application ten the prompt was eight hundred words, and I was noticing that I retyped it (with subtle drift) every single time. Slightly different phrasing on Monday than Tuesday. A guard rule I forgot to include on Friday's application. A clarification I had added in one thread that did not propagate to the next.

I wrapped the whole prompt into a single skill called [`resume-builder`](https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/ai-resume-deepdives/skills/resume-builder/). The trigger phrase became one short sentence: "let us apply to Acme Fintech for the Director of Product Payments role." The skill anchors the workflow on one canonical version of every rule and triggers itself. Setup time per application dropped from ten minutes of pasting and re-explaining to thirty seconds. The drift stopped. The workflow became reliable in a way the prompt-based version never was.

The other benefit is iteration. Once a workflow lives inside a skill file, you can improve the workflow by editing the file in one place. Fix the bug once and every future application benefits. With prompts, you fix the bug at the top of one thread and the next thread starts from the old version.

**If you are starting from scratch:** notice when you have copy-pasted the same prompt block three times. That is the signal. Wrap it into a skill that afternoon. The skill creates leverage you do not get from any number of prompts.

---

## 4. Close the loop or you start from zero every time.

The [`update-brain-trust`](https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/ai-resume-deepdives/skills/update-brain-trust/) skill is what separates this workflow from "I used an AI chatbot to write a resume." A new framing you discovered for last week's application is no good to you if it does not get folded back into the source of truth. The loop is the system.

A real example. For the first fifteen applications or so I forgot to run the update step at the end of each thread. The thread closed, the new framings stayed in the thread, and the brain trust stayed where it had started. Application twenty-something to a regulated fintech reused a cover letter hook that had landed brilliantly in an earlier application to a similar company. I could not remember the exact phrasing. I had to recreate it from rough memory, and I lost some of the original sharpness in the recreation. I shipped a weaker version of work I had already done once.

After that miss, every application thread ended with the update step before I closed it. The skill ingests the resume, cover letter, and Job Description (JD) from the thread, asks me a structured block of multi-choice questions about what new variants to fold back in, applies the additive changes I approved, and logs the application. Three minutes at the end of each thread. By the time I had sent fifty applications, the brain trust had something like three times the canonical phrasings it had started with. The system was pulling from a much richer library than the one in my head.

The compounding works because every application teaches the system something. Not every application teaches the system something big, but every application teaches the system something. Without the loop, none of those small lessons accumulate.

**If you are starting from scratch:** make the update step the last thing you do every application, no exceptions, before you close the thread. Treat it like saving a file. Lose the habit and you lose the compounding.

---

## 5. Hard guard rules prevent the same mistake twice.

Some lessons are so important they belong as explicit rules the AI must follow on every run. Encode them once. Stop relearning them.

A real example, two patterns. The first was a chronology rule. On an early application, Claude pulled in some of my older career history that predated my pivot into Product. The bullet was technically accurate, but it diluted the seniority story by anchoring the reader on a different career track. I encoded a chronology guard: never include any role that predates my current career pivot. The rule got saved once. The same mistake stopped happening immediately and never came back.

The second pattern was a conditional advisory-engagement exclusion. I had done some advisory work earlier in my career that fit well into the story for most company archetypes but absolutely did not fit one specific banking archetype I applied to often. The first time the skill included the advisory engagement on a banking application, I cut it manually and encoded a conditional rule: for applications to that specific archetype, never mention that specific advisory engagement. Different archetypes, different rules. The guard got saved once and the skill respected it on every future banking application.

The pattern beneath both rules is the same. A guard is a one-time correction promoted to a permanent constraint. The first time you notice a bullet, a role, a phrasing, or a section that should not have made it into the draft, ask yourself: will this come up again? If the answer is "yes, in this same category of application," that is a guard rule. Name it. Save it. Move on.

**If you are starting from scratch:** when you correct Claude on something that feels like it could happen again, take the extra five seconds to name the rule explicitly and ask Claude to save it. Future you will thank present you for the discipline.

---

## 6. Validate in human-readable form before shipping.

Never send the AI's first draft. The Google Docs polish step is non-negotiable. Reading a document in a document editor (not in a chat window) catches a different category of issue than anything you can catch any other way. The format is the readership.

A real example, and a painful one. Early on I shipped an application where Claude had introduced a phrase like "leveraged synergies across stakeholders" buried in a bullet on page two of the resume. I had skimmed the draft inside the Cowork chat. It read fine in the chat window. I had not yet built the habit of opening the Word document in Google Docs at the end. The phrase landed on the recruiter, and the moment I saw the exported Portable Document Format (PDF) on my own screen I cringed. There was nothing I could do; the application was already sent.

Since then, every application gets the Google Docs polish step before export. Open the file in a document editor. Read it as a recruiter would, not as a drafter would. Look for stilted phrasing, awkward line breaks, words you would never say out loud. Spot-check every metric against the canonical version in your brain trust. Read the cover letter opener three times before approving it. Check the page break between cover letter and resume; if the cover spills onto page two by a single line, tighten the cover letter, do not let it spill.

The chat window is the workshop. The document editor is the showroom. Anything that survives the workshop but fails in the showroom is a defect you can still fix. Anything that ships in the PDF you sent cannot be fixed.

**If you are starting from scratch:** never ship from chat. Always go through the document editor. Every time. It will save you the cringe at least once a month for the rest of your search.

---

## 7. External research belongs outside the main session.

A different job needs a different tool. Perplexity is built for live research with citations. Keeping it out of the main Cowork thread keeps the main thread focused on tailoring and lets the research tool do what it is best at.

A real example. Early in the system's life I tried to do company research inside the main Cowork thread by asking Claude to web-search the company, the team, and recent news. The thread context bloated with company facts the tailoring step did not need. The resume draft started leaking irrelevant company-specific phrasing into bullets. Quality dropped. I switched to running the research step in a separate Perplexity Pro tab. The main thread stayed focused on tailoring, Perplexity did the live research with citations, and I brought back only the findings that mattered as a research notes file inside the project folder. The tailoring quality recovered immediately.

The unexpected bonus showed up a few weeks later. The external research step started catching company red flags before I invested an hour on the application. A round of layoffs six months ago. A founder who had been publicly quoted in a way I would not want to work for. A product line that had been quietly killed and the role was likely a backfill of someone burned out. Half the time, the most valuable output of Step 8 was a "do not apply" decision that saved me an hour I redirected to a better opportunity.

The principle generalizes. Any time a workflow has a sub-step that benefits from a specialized tool, run that sub-step in the specialized tool, then bring the output back into the main workflow. Tools are best used for what they were built for.

**If you are starting from scratch:** start the research habit on application one. The hour you save by not applying to one wrong job in your first month pays for a year of Perplexity Pro twice over.

---

## 8. Memory is the moat.

Without persistent memory, every conversation starts at zero and every conversation ends at zero. With memory configured, every conversation starts where the last one ended. This is the difference between a tool and a collaborator.

A real example. One Saturday morning I opened a fresh Cowork thread for a banking application and found I was re-explaining everything from scratch: that my older certifications were past tense, that I follow a strict chronology rule on what roles appear, that I prefer multi-choice clarifying questions, that I never use em dashes. After about the fifth thread that month where I re-onboarded Claude on the same defaults, I realized I had not turned on persistent memory yet. I was paying the same setup tax every single time.

I turned on auto-memory in the desktop app and saved a handful of seed memories explicitly: target roles, style locks, hard rules, the resume chronology rule, the cover letter archetypes I work in. The very next thread loaded with the right defaults. The thread after that, too. From that point on, every new application thread started where the last one had ended. The setup cost flipped from "per thread" to "once."

The compound value is harder to see in any single application but obvious across a search. Multiply the per-thread re-onboarding cost by fifty applications and you get hours of repetitive typing. Memory eliminates the entire category. It also lets you save things you discover over time (a new framing, a new guard rule) and have them propagate to every future thread automatically.

**If you are starting from scratch:** turn on persistent memory before you send your first application. Save five or six seed memories the first afternoon. Every thread after that will start sharper than the one before, which is the entire point of building the system in the first place.

---

## 9. Boring and reliable beats fancy and fragile.

A simple Word template that ports cleanly to PDF beats a beautiful template that breaks on every export. A flat folder structure beats a deeply nested one. The workflow you can run while tired beats the workflow you have to think about.

A real example. Early on I tried a more elaborate Word template: a colored sidebar on page one, a two-column resume layout on page two, and a custom font that I had downloaded for the headline. It looked great inside Microsoft Word. The first PDF export broke the sidebar alignment by half an inch on page two. The next export opened cleanly on my laptop but on a colleague's mobile preview the sidebar overlapped the body text. The third export, after I had "fixed" the layout twice, parsed badly in a public Applicant Tracking System (ATS) checker because the two-column resume interleaved left-column and right-column content into a single long string.

I cut everything fancy in one sitting. Dropped to a plain header table at the top of every page, a single column body, a neutral sans-serif font at body weight, page number footer, nothing else. The plain template ports cleanly across every device and every ATS I have tested it on. The fancy template was a vanity tax I paid for two weeks before I admitted it.

The principle goes beyond templates. The Career Brain Trust folder structure I use is flat by design. The skill files are short and read like instructions, not like clever engineering. The trigger phrases are normal English. The workflow has nothing in it I cannot remember the first time I am tired on a Sunday night. Fancy systems break. Boring systems run.

**If you are starting from scratch:** pick the plainest template that does the job, the flattest folder structure that holds the content, and the simplest skill workflow that gets the result. You can always add complexity later if you genuinely need it. You almost never genuinely need it.

---

## 10. The structured-question pattern compounds.

Multi-choice clarifying questions with a copy-paste answer sheet are the most leveraged single pattern in this entire system. Once you bake the pattern into your global instructions, every project benefits, not just job applications.

A real example. The pattern started inside the job application workflow because that was the workflow where I needed it most. The skill would ask me five questions before drafting, I would copy the answer sheet, fill in single letters, paste back, and the skill would draft with my full context. After a few weeks I noticed the same pattern was making other AI-assisted work faster: research drafts where Claude was about to make wrong assumptions on something I cared about, strategy planning sessions where I wanted a structured option set instead of free-form prose, even routine writing tasks where I wanted to lock format choices before drafting started.

I added the pattern to my global instructions so every Claude thread defaults to it on any project. The leverage of that one habit, applied across every AI-assisted thing I do, is bigger than any single application I have ever tailored. It pays compound interest in every domain it touches.

The reason it works is that ambiguity is expensive. A free-form clarifying question lets the model and the human both drift toward whatever feels easiest to answer. A multi-choice question forces both sides to land on a specific commitment before drafting starts. Drafts built on locked commitments are sharper than drafts built on vague intent. The pattern is described in detail in the companion guide called ["The Context Prompt That Will Revolutionize Your Workflow,"](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md) linked from the main guide.

**If you are starting from scratch:** put the structured-question pattern in your global instructions on day one. Use it for your job applications, your research, your strategy work, and your random Sunday brainstorming. The habit pays everywhere.

---

## 11. Different tones for different companies.

Banking applications are formal and credentialed. Startup applications are direct and punchy. Big-tech applications are crisp and metrics-heavy. Same me, different framing. Telling Claude the archetype explicitly produces dramatically different drafts because the skill is anchoring on a known pattern.

A real example. I applied to a major North American bank and an early-stage payments startup in the same week. Same me. Same brain trust. Two completely different cover letters. The banking cover led with regulatory and compliance credentials in a measured tone with longer sentences and named programs and frameworks. The startup cover opened with a short, direct, builder-voice line about shipping zero to one in a regulated market and skipped the formal framing entirely. Both came from the same source of truth. The only thing that changed was the archetype I named when I triggered the skill ("banking-style cover" versus "startup-style cover"). Both applications got real engagement. Neither would have worked if I had used the other archetype's voice.

The principle is small but important. Tone is part of tailoring. Skipping the archetype step and letting the skill default to a neutral voice produces drafts that read competent but generic. The bank reader thinks you are not serious about the regulatory side. The startup founder thinks you are too corporate to ship fast. Same writer, same content, wrong voice register. Naming the archetype solves the problem.

Building archetype files inside the Cover Letters section of the brain trust over time is what makes the voice library work. By the time you have applied to a handful of companies in each archetype, your brain trust has reusable hooks and structures for each one.

**If you are starting from scratch:** name the archetype explicitly on every application from the first one. Even if your archetype library is empty, the act of naming the archetype tells the skill what voice to draft in, and the resulting variants build your library faster than you expect.

---

## 12. The structure is the product.

The Career Brain Trust folder structure, the INDEX with tags, the per-role and per-archetype child files: this is the actual product. Without the structure, the AI is guessing. With it, the AI is curating. Spend time on the structure upfront; the dividend pays every application after.

A real example. For roughly the first dozen applications, my Career Brain Trust was a single monolithic Markdown file. One big document with every role, every cover letter, every metric, and every framing in it. Claude could read the file, and the skill mostly worked. Then I hit a wall: past somewhere around twenty-five thousand tokens, the tool that read the file started truncating. The skill was loading the file but missing the back half. The cover letter archetypes lived in the back half. Drafts came out flat because the relevant archetype section was never reaching the working context.

I split the monolith into a folder structure: an INDEX at the top, per-role child files numbered 3.1, 3.2, 3.3, per-archetype cover letter child files numbered 4.1, 4.2, 4.20, plus supporting files for Identity, Chronology, Skills, Achievements, and Education. The skill now reads INDEX first and selectively loads only the matching child files for the application at hand. The truncation problem vanished overnight. Drafts got sharper because the right context was finally reaching the model. The system became faster and more reliable.

The deeper lesson sits underneath the truncation story. The folder structure is what makes the rest of the system work. The AI prompt is just the part on top. If the structure is wrong, no prompt fixes it. If the structure is right, even a mediocre prompt can produce strong drafts. Spend the time on structure first.

**If you are starting from scratch:** build the brain trust as a folder from the very first application, not as a single file you split later. [Deep Dive 1](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/ai-resume-deepdives/deep%20dives/01%20-%20The%20Career%20Brain%20Trust%20Structure.md) walks the exact structure step by step. Save yourself the migration.

---

## 13. Collaboration beats automation.

The point of this system is not to automate your job search away. It is to amplify your judgment with a tireless partner. The strongest applications come from a back-and-forth conversation, not a one-shot prompt. The system is the scaffolding. You are still the writer.

A real example. My first attempt at the workflow was closer to "one-shot prompt." I gave Claude the brain trust and the Job Description, asked the skill to draft the whole application end to end, ran a light proofread, and shipped the draft. The output was technically tailored. It was also flat. Generic. It did not sound like me; it sounded like an AI pretending to be me, which is the worst of both worlds.

I changed the workflow to be explicitly iterative. Claude drafts, I push back with specifics, Claude offers three alternatives, I pick one or merge two, Claude refines, I refine further, we go around the same bullet until it sounds like me amplified rather than like a robot wearing my name. The final drafts now sound like the strongest version of my own writing because I am still the writer; Claude is the tireless partner who never gets bored of the eleventh revision and never gets defensive about a phrasing I want to cut.

The framing matters. Automation means you are out of the loop. Collaboration means you are still inside it, sharper than you would be alone. The system gives you scaffolding, persistent memory, structured context, and a partner who never tires. You give the judgment, the voice, the editorial taste, and the willingness to argue until the bullet earns its place.

**If you are starting from scratch:** expect to argue with Claude on every single application. The argument is the workflow. Treat the first draft as a proposal, push back at least three times, and stop when both of you agree the application is sharp. That is the system working.

---

# Closing Reflection

Three things the outline of this guide flagged for the closing of this deep dive: the patterns that almost broke the system and how they got fixed, what I would build into a version two if I were starting over, and the mistakes other people are most likely to make when adapting this system. Each one is its own short section below.

## Patterns That Almost Broke the System

Three failure modes nearly broke the workflow at different points.

The first was the monolithic brain trust file (covered in lesson twelve). Past twenty-five thousand tokens the read got truncated and the back half of the file effectively did not exist for the skill. The fix was the folder split. If you start from a folder structure today you will skip this entire failure mode.

The second was a quiet drift in canonical bullets. Each application slightly rephrased a bullet, the rephrased version got folded back into the brain trust as a variant, and after thirty applications I had four or five competing variants of the same bullet with no clear canonical anymore. The fix was a weekly review: ten minutes once a week to scan the brain trust, pick the strongest canonical, and demote the rest to variants-of-canonical.

The third was a conflict between two guard rules. One rule said never include a specific advisory engagement on a specific banking archetype. Another rule said always include the most recent advisory work for senior individual-contributor applications. The two collided on one application where both rules wanted to fire. The fix was an explicit precedence rule: archetype-specific guards always win over default behavior. Document the precedence; do not leave it implicit.

## What I Would Build Into Version Two

If I were starting from scratch today with everything I now know, I would change five things on day one.

I would build the brain trust as a folder from application one, not as a single file I split later. The migration was painful and avoidable.

I would turn on persistent memory before sending the first application and save six or seven seed memories that afternoon: target roles, hard rules, style preferences, cover letter archetypes I work in.

I would put the multi-choice structured-question pattern into my global instructions on day one rather than building it in over the first month. The leverage compounds from the first thread you use it in.

I would build the application log file from day one as a searchable record. Mine started a few weeks in and the early applications are not in there. I cannot search what I cannot find.

I would write the first two cover letter archetypes from scratch as starter templates before applying to any company in those archetypes. Cold-drafting the archetype on a real application costs more than building the template the day before.

## Mistakes Other People Are Most Likely to Make

The most predictable mistake is skipping the brain trust setup and trying to use the skill on a thinly populated source of truth. The system needs material to curate. If the brain trust is empty, the skill is just a one-shot prompt with extra steps.

The second predictable mistake is skipping the update step at the end of the application thread. You will tell yourself you will do it later. You will not. Make the update step the last thing in every thread, no exceptions.

The third is treating the first draft as a final draft. The first draft is a proposal. Push back at least three times. Ask for alternatives. Argue until the bullet earns its place.

The fourth is trying to use the system to apply faster instead of better. The point of cutting tailoring time from four hours to twenty minutes is not to send sixty mediocre applications a week. It is to send fifteen genuinely sharp ones with the time you got back. Quality compounds; quantity does not.

The fifth is forgetting that you are still the writer. The system gives you scaffolding and a tireless partner. The judgment is yours. The voice is yours. The taste is yours. The system is only as good as the writer using it.

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

If you use or adapt this deep dive, please include:

Based on "What I Learned (Expanded)," part of "Tailored, Not Templated: An AI Workflow for Resumes That Actually Land in a Brutal Job Market" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/AI%20Workflow%20for%20Resumes%20That%20Actually%20Land.md
License: CC BY 4.0
