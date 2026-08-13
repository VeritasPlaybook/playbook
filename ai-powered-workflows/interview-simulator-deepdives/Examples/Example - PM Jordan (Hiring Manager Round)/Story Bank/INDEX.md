>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Story Bank INDEX: Jordan Chen, Northwind Payments hiring manager round

**Purpose:** Routing file. The assistant reads this in full, then loads only the cards the round needs.
**Folder root:** `Story Bank/`
**Last updated:** 25 June 2026, after mock run two. Added the coverage gap on failure and marked Card F as the next thing to build.

> **Worked illustration.** Jordan Chen is fictional. Tessera, Brightline Health Systems, and Quantile Insights are invented employers. Every number below is illustrative. Each card traces to a bullet in the fictional Career Brain Trust published with the resume guide in this repository, which is the point: the Story Bank sits on top of the Brain Trust and does not replace it.

---

# Card library

| Card | Short name | Owns (competencies) | Tags | Source | Status |
|---|---|---|---|---|---|
| 1 | Automation engine | taking manual work out of a workflow, adoption under distrust, trade-off ownership | `#build` `#adoption` `#workflow` `#tradeoffs` | Brain Trust `Experience/3.1 Tessera.md` | drilled 2 times |
| 2 | Messaging clearance | shipping inside a non-negotiable constraint, cross-functional sequencing, regulated domain credibility | `#compliance` `#crossfunctional` `#sequencing` `#regulated` | Brain Trust `Experience/3.2 Brightline Health Systems.md` | drilled 2 times |
| 3 | Connector roadmap | prioritising against teams you do not control, saying no, expansion mechanics | `#prioritisation` `#influence` `#roadmap` `#integrations` | Brain Trust `Experience/3.1 Tessera.md` | drilled 1 time |
| F | Failure card | learning, ownership, a decision that did not work | `#failure` | Brain Trust `Experience/3.1 Tessera.md`, artificial intelligence task assistant bullet | **NEEDS REAL DETAIL.** Does not exist yet. See coverage gap below. |

Cards 1 and 2 do most of the work. Card 3 is reinforcement, the right answer for exactly one question type. Card F is the hole.

---

# Coverage map

| Competency the round tests | Card that owns it | Confident? |
|---|---|---|
| Taking manual handling out of a queue without losing the cases humans catch | Card 1 | yes |
| Shipping under a constraint that cannot be argued with | Card 2 | yes |
| Owning a surface that depends on teams you do not control | Card 3 | yes |
| Describing the system underneath a product decision | Card 1, second half | thin. The system description was improvised in run one and it showed |
| A decision that did not work, owned without deflection | **none** | none |
| Level and scope at Senior in a bigger surface | Card 3 partially | thin |

**Gaps to close first:**

1. **No failure card.** Run two asked for a miss and Card 1 got stretched into one, producing a success story with a caveat bolted on. This is a material gap, not a delivery gap, and no amount of drilling fixes it. The raw material exists: the artificial intelligence (AI) task assistant at Tessera shipped a first version that had to be pulled back and rescoped. That is the card. It has not been written.
2. **Level and scope.** No card answers "what was the scope of your last role" with numbers on team size and decision rights. Card 3 is closest. Needs a scope block rather than a fourth card.

---

# Rules for this folder

1. Nothing is invented. Anything unverified says `NEEDS REAL DETAIL` with a specific question beside it.
2. Numbers get hardened once and corrected downward where they were generous. Every card carries the date its numbers were last checked.
3. Append, do not rewrite. New framings go in the variant block at the bottom of a card.
4. One story per question. The Triggers table on the cheat sheet decides which, not instinct in the moment.
5. Every card gets a written ending. Trailing off is the most common delivery failure and the most fixable.

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

Based on "Story Bank INDEX," part of "Build Your Own Interview Simulator: Practice Against the Actual Round, Not a Generic Question List" by VeritasPlaybook
Original: https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Build%20Your%20Own%20Interview%20Simulator.md
License: CC BY 4.0
