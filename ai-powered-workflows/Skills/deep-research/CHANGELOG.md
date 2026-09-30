# Changelog

## v2 (September 2026)

### Why v2

v1 was built from a literature review of how deep research agents fail. In September 2026 it went head to head with [Hyperresearch](https://github.com/jordan-gibbs/hyperresearch) by Jordan Gibbs, an open source harness that turns Claude Code into a 16 step research pipeline with 16 specialised agents, 55 to 130 sources per run, and run times of 30 minutes to several hours.

Hyperresearch is powerful, and for most everyday questions it is far more than you need. It is built for report quality first, with spend handled by a budget cap you set rather than by the design. What it does have is a few cheap checks that catch errors v1 could not see. v2 takes those checks and leaves the weight behind.

### Added

- **Scan-first ladder.** When you do not name a depth, the skill runs a cheap Scan, then tells you what the answer looks like, what is contested, whether you asked the right question, and whether a deeper tier is worth it. Original to this skill.
- **Coverage matrix** (adapted from Hyperresearch). Before any searching, every phrase in your question is mapped to a sub-question. Catches the plan quietly narrowing "supplements" to "creatine" or dropping a date range. Verification cannot catch this later, because it checks whether claims are true, not whether they answer what you asked.
- **Adversarial search minimums** (adapted from Hyperresearch's "what source would overturn this?" critic). Scan 1, Standard 3, Deep 5 searches that must hunt for the case against. A count is visible when skipped; an intention is not.
- **Independent source count** (adapted from Hyperresearch's independence audit). For each key claim, the number of truly independent sources after collapsing reprints, rewrites and wire copies, with the collapsed clusters named.
- **Retraction check** (adapted from Hyperresearch's retraction sweep). Every cited DOI or arXiv paper is checked against OpenAlex or Semantic Scholar. A retracted paper passes every other check, because it still says what the report claims it says.
- **Customizing section** so the skill is easy to fork.

### Fixed

Running the skill's own verification pass on this public version caught three citation problems in the private draft:

- **Wrong paper for the self-review finding.** The GPT-4 GSM8K drop from 95.5% to 91.5% was cited to a 2024 survey (arXiv:2406.01297). It comes from Huang et al., arXiv:2310.01798 (ICLR 2024). The "self-correction blind spot" is a separate paper, arXiv:2507.02778.
- **Unverifiable sycophancy figures.** The ELEPHANT figures (72% versus 22%, a 28 point gap) could not be found in the paper. Replaced with the published figures: models accept the user's framing 90% of the time against 60% for humans.
- **Orphan citation.** The evidence list cited Anthropic's 4x, 15x and 90.2% figures, but they appeared nowhere in the body. They are now in the opening section, verified against Anthropic's June 2025 engineering post.

Also removed: two unsourced figures (a 6 point gain from a web fallback, and dollar costs per tier) and one approximate figure quoted from memory, now replaced with the sourced Nature figure on 2023 retractions.

### Removed

Everything specific to the original author's setup: personal note-app filing, browser routing, local file links, and house style rules. See the Customizing section of `SKILL.md` to add your own.

## v1 (August 2026)

First version. Four core rules (plan once, isolate raw text in sub-agents, better retrieval over more searching, verify against sources rather than self-review), three tiers, domain source routing, and a source quality checklist.
