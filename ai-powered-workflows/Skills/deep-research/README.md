# Deep Research skill (v2)

>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this skill for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

A research method you install into Claude. It gets sourced, checked answers for a fraction of the tokens a naive multi-agent run burns.

## Why

Anthropic's own numbers: agents use about 4x the tokens of a chat, and multi-agent research about 15x. That spend buys real quality, but most of it is waste: re-planning after every search, dumping whole web pages into the main context, reading more sources instead of better ones, and a final report nobody checked against the sources it cites. In one 2026 study, deep research citations were factually accurate to their source only 39% to 77% of the time, even when the links worked.

This skill keeps the part that works and cuts the waste.

## How it works

| Step | What happens |
|---|---|
| 0. Confirm | Restates your question neutrally. If you did not pick a depth, runs a cheap Scan first and tells you whether going deeper is worth it |
| 1. Plan once | Writes the whole plan up front, including searches that hunt for the case *against* the expected answer, and checks every phrase of your question is covered |
| 2. Fan out | Sub-agents read sources in their own context and hand back short briefs. Raw pages never reach the main thread |
| 3. Verify | A separate agent re-opens the sources behind every number and load-bearing claim, checks for retracted papers, and counts how many sources are truly independent |
| 4. Synthesize | Findings graded by confidence, disagreements, what nobody has studied, and what it means for your decision. Ends with a cost note |

Three tiers so effort matches the question:

| | Scan | Standard | Deep |
|---|---|---|---|
| Sub-agents | 0 to 1 | 3 to 4 | 5 to 8 |
| Sources read fully | 3 to 5 | 8 to 12 | 15 to 20 |
| Verification pass | No | Yes | Yes |
| Output | Chat answer | Markdown file | Markdown file |

Every rule in `SKILL.md` names the study behind it and says how strong that evidence is.

## Install

- **Easiest:** download `deep-research.skill` from this folder and upload it in Claude's skill settings. See `INSTALL.md`.
- **Let Claude do it:** paste the prompt in `Install with Claude.md`.
- **Claude Code:** copy this folder to `~/.claude/skills/deep-research/`.

Then ask: *"Do a deep research run on [your question]."*

## Files

| File | What it is |
|---|---|
| `SKILL.md` | The skill itself. The only file Claude needs |
| `deep-research.skill` | One-file package for upload |
| `INSTALL.md` | Manual install steps |
| `Install with Claude.md` | Paste-in prompt for a guided install |
| `CHANGELOG.md` | What changed from v1, and why |

## Credits

Four of the v2 checks were adapted from [Hyperresearch](https://github.com/jordan-gibbs/hyperresearch) by Jordan Gibbs, a heavier open source research harness for Claude Code. See `CHANGELOG.md`.

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

If you use or adapt this skill, please include:

Based on "Deep Research skill" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/tree/main/ai-powered-workflows/Skills/deep-research
License: CC BY 4.0

## Questions or Feedback?

Found this helpful or have suggestions? Connect with me:
- LinkedIn: https://www.linkedin.com/in/malocilja/
- GitHub: https://github.com/VeritasPlaybook/playbook

*If you found this valuable, star the repo to help others find it.*
