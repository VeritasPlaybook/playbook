# Evals (optional)

This folder is optional. It exists for readers who want to run benchmark tests on the `update-brain-trust` skill, typically after heavy customization.

If you do not care about evals, ignore this folder. The skill works without anything in here.

---

## What this folder is for

Evals are test cases you run against the skill to verify it still works the way you expect after you change it. Typical reasons to write an eval:

- You added a guard rule and want to confirm the skill respects it across a few realistic test cases.
- You modified the multi-choice question wording in Phase 2 and want to make sure the questions still parse cleanly.
- You changed the canonical facts cheat sheet format and want to confirm the contradiction-check logic still flags correctly.

If you have not modified the skill, you do not need evals. Use the skill as-is.

---

## How to set up evals for this skill

Each eval is a directory under `evals/fixtures/` containing one fixture: a sample `.docx` file representing a tailored application the skill should ingest. You then write an `evals.json` file at the top of the `evals/` folder that defines:

- The test prompt (typically: "update the brain trust with this application")
- The fixture file (the .docx the skill should find in thread context)
- A description of what success looks like

Suggested structure:

```
evals/
|-- README.md (this file)
|-- evals.json
|-- fixtures/
    |-- example-1/
    |   |-- Acme Fintech - Director of Product.docx
    |-- example-2/
    |   |-- Beta Robotics - Senior PM.docx
```

The fixture `.docx` files should mirror the structure of a real combined cover-letter-plus-resume document produced by the `resume-builder` skill (cover letter on page 1, page break, resume on page 2 and beyond).

For the schema of `evals.json` and how to run the resulting evals, see the `skill-creator` skill's documentation if you have it installed. The relevant section is "Running and evaluating test cases."

---

## Generating fixtures from your own past applications

The easiest way to seed fixtures is to copy two or three of your real past applications out of your `Past Resumes/` folder, anonymize them (replace your name, dates, and any sensitive numbers with placeholder values), and drop the anonymized copies into `evals/fixtures/`.

This keeps your evals realistic without leaking personal data.

---

## License

This evals scaffold is published under Creative Commons Attribution 4.0 International (CC BY 4.0). Attribution: "Tailored, Not Templated" by VeritasPlaybook. Original repository: https://github.com/VeritasPlaybook/playbook.
