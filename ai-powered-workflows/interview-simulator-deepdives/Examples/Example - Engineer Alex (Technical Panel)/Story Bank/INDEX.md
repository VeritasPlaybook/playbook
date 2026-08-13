>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this example for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Story Bank INDEX: Alex Rivera, Northwind Payments technical panel

**Purpose:** Routing file. The assistant reads this in full, then loads only the cards the run needs.
**Folder root:** `Story Bank/`
**Last updated:** 27 June 2026, after mock run two. Card 4 marked as the top gap and still not written.

> **Worked illustration.** Alex Rivera is fictional. Beacon Pay, Lumen Streams, and Hearthstone Labs are invented employers. Every number is illustrative. Each card traces to a bullet in the fictional Career Brain Trust published with the resume guide in this repository. The Story Bank sits on top of the Brain Trust and does not replace it: the Brain Trust holds written material, these cards hold spoken narratives, which is why the same work appears in both.

---

# Card library

| Card | Short name | Owns (competencies) | Tags | Source | Status |
|---|---|---|---|---|---|
| 1 | Idempotency primitives | correctness under distributed failure, interface design, blast radius | `#correctness` `#api` `#distributed` `#payments` | Brain Trust `Experience/3.1 Beacon Pay.md` | drilled 2 times |
| 2 | Sharded migration | migrating a live financial store, verification, staged rollout | `#migration` `#data` `#verification` `#risk` | Brain Trust `Experience/3.1 Beacon Pay.md` | drilled 2 times, v2 after run one |
| 3 | Service mesh cutover | operability, choosing the right measure, cross-team change | `#operability` `#latency` `#crossteam` `#toil` | Brain Trust `Experience/3.2 Lumen Streams.md` | drilled 1 time |
| 4 | Incident card | detection, mitigation versus durable fix, customer-visible symptom | `#incident` `#oncall` `#failure` | Brain Trust `Experience/3.1 Beacon Pay.md`, on-call material | **NEEDS REAL DETAIL.** Does not exist. See coverage gap. |

Cards 1 and 2 do most of the work and map cleanly onto the two interviewers: Card 2 is Ines's territory, Card 1 is where the payments credibility lives. Card 3 answers exactly two question types. Card 4 is the hole, and there is a former site reliability engineer on the panel.

---

# Coverage map

| Competency the round tests | Card that owns it | Confident? |
|---|---|---|
| Correctness under partial failure | Card 1 | yes |
| Migrating a live system that holds money | Card 2 | yes, after the verification detail was added in v2 |
| Data modelling defended under pushback | Card 2 | thin. The shard key rationale was improvised in run one and it showed |
| Choosing what to measure, and defending the choice | Card 3 | yes |
| A production incident, told from the customer inward | **none** | none |
| Being wrong about something technical and finding out | Card 1 partially, the first version of the key scheme | thin |
| Explaining something complicated to a non-specialist | spread across all three, owned by none | thin. This became the run two problem |

**Gaps to close first:**

1. **No incident card.** The largest gap in the folder. Marcus Dube spent six years in site reliability and still carries a pager. The raw material exists and is uncomfortable, which is why it has not been written: the duplicate-charge incident at Beacon Pay in early 2024 that motivated the idempotency work was found by a platform customer, not us, and ran about six hours. That is the card. Written properly it is a strong answer, because the honest version of "a customer told us first" disarms the doubt a polished version would leave standing.
2. **Shard key rationale.** Not a new card. One block on Card 2 with the key chosen, the two rejected candidates, and the reason. Added in version two.
3. **The customer-visible symptom line.** One line on every card, not just the incident one. Cheap, and it forces the answer to exist.

---

# Rules for this folder

1. Nothing is invented. Anything unverified says `NEEDS REAL DETAIL` with a specific question beside it.
2. Numbers get hardened once and corrected downward where they were generous. Each card carries the date the numbers were last checked.
3. Append, do not rewrite. New framings go in the variant block at the bottom of a card.
4. One story per question. The Triggers table on the cheat sheet decides which.
5. Every card gets a written ending. Trailing off is the most common delivery failure and the most fixable.
6. **Local rule for a technical round:** every card carries a verification line. Not what the result was, how I knew the result was real. Both interviewers screen for this and it is the highest-value line on the card.

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
