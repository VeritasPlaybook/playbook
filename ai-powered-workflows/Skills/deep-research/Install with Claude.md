# Install with Claude: Deep Research skill

Paste the prompt below into a new chat and Claude will install the skill, check it works, and help you tailor it.

If you prefer to install it yourself, see `INSTALL.md` in this same folder.

---

## Before pasting

1. Download `deep-research.skill` (or the whole `deep-research` folder) from this repository.
2. Attach the file to a new chat, or point Claude at the folder if you are using Claude Code or have a folder connected.
3. Paste the prompt below.

---

## The prompt

```
I want to install the Deep Research skill I attached (or the deep-research folder I pointed you at).

1. Read SKILL.md in full and tell me in five bullet points what it does and when it will trigger.

2. Install it for me:
   - If you can install skills directly in this environment, do it.
   - If you cannot, give me exact steps for my setup. Ask me first whether I use Claude desktop, claude.ai in a browser, or Claude Code, and on which operating system.

3. Check the prerequisites: web search on, web fetch on, and whether this environment supports sub-agents. Tell me which are missing and what that costs me.

4. Ask me whether I want to customize anything now, using the CUSTOMIZING section of SKILL.md:
   a. Save Deep tier reports to a notes app or folder I use (ask which, and add one line to Phase 4)
   b. Add source routing rows for my field (ask my field and the sources I trust)
   c. Add my house writing style (ask for my rules)
   d. Skip for now
   Give each option a recommended default so I can reply "defaults".

5. Make only the edits I approve. Keep the name: field in SKILL.md matching the folder name.

6. Verify the install by telling me a test phrase to type in a new chat and what I should see if it worked (a neutral restatement of the question and a request for my go-ahead, not an answer from memory).

Do not run any research during install.
```

---

## What happens after install

Say "deep research", "/deep-research", "do a deep dive on", or "what does the literature say about" followed by your question. Claude restates it neutrally, picks or recommends a tier, shows you the plan on Standard and Deep, and waits for your yes before spending anything.

---

## License

This skill is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Deep Research skill" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
