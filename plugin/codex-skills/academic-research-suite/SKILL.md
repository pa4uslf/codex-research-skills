---
name: academic-research-suite
description: >-
  Umbrella router for Academic Research Skills in Codex. Use when the user asks
  for academic research help, literature review, paper writing, manuscript
  review, revision, citation checking, or a complete research-to-publication
  workflow and the best ARS sub-skill is not yet clear.
---

# Academic Research Suite For Codex

Use this Codex wrapper as the router for the Academic Research Skills package.
Keep routing explicit and then load the canonical workflow file for the chosen
sub-skill.

## Route

- Research, literature review, PRISMA, systematic review, fact-checking,
  evidence synthesis, or guided research scoping: use `../../../deep-research/SKILL.md`.
- Paper writing, outlining, revision, reviewer-comment parsing, citation
  checking, format conversion, abstracts, or AI disclosure: use
  `../../../academic-paper/SKILL.md`.
- Manuscript review, peer-review simulation, methodology-only review,
  re-review, quick assessment, or reviewer calibration: use
  `../../../academic-paper-reviewer/SKILL.md`.
- End-to-end research-to-publication workflow, stage tracking, integrity gates,
  review/revision loops, or process summary: use `../../../academic-pipeline/SKILL.md`.

## Codex Execution Rules

1. Read the selected canonical `SKILL.md` before doing substantive work.
2. Resolve relative files from the canonical skill directory, not from this
   wrapper directory.
3. Prefer evidence-first academic outputs: separate verified facts, assumptions,
   limitations, and next actions.
4. Do not claim paper completion, review completion, or citation verification
   without the corresponding artifacts or checks described by the selected
   canonical workflow.

## Codex Entrypoints

Users can invoke this router with `$academic-research-suite`, or invoke the
specialized wrappers directly:

- `$ars-deep-research`
- `$ars-academic-paper`
- `$ars-paper-reviewer`
- `$ars-academic-pipeline`
