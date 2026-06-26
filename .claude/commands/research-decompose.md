---
name: research-decompose
description: Break a locked research objective into typed sub-questions (SQ-01..SQ-NN, each carrying a claim type) and write them to the run's decompose/sub-questions.md.
---

# research-decompose

One job: turn the objective into a set of answerable, typed sub-questions. You are a leaf. Read `docs/conventions.md` for the trace layout and identifier scheme. You read only `brief.md`, you write only `decompose/sub-questions.md`, and you return a short summary. You do not call other leaves.

## Input

The composer gives you the run root path. Read `<run-root>/brief.md`. The objective, scope, and any `claim_types` hint live there.

## Do

1. Decompose the objective into the smallest set of sub-questions that, answered together, fully cover it. Stay inside the brief's `scope`; do not add sub-questions for things ruled out of bounds. Aim for genuinely distinct questions; do not pad the count.
2. Give each sub-question a stable id, `SQ-01` onward, two-digit zero-padded, starting at `01`.
3. Tag each with exactly one **claim type**, the dominant kind of evidence it needs:
   - `factual`: a stated fact or definition (what is X, who makes Y).
   - `quantitative`: a number, statistic, or measured value.
   - `regulatory`: a rule, law, filing, or compliance fact.
   - `competitive`: a market, vendor, or comparison claim.
   - `technical`: how something works, a mechanism, an implementation detail.
   If a sub-question genuinely spans two types, split it so each piece carries one type; the claim type routes source selection downstream, so keep it clean.

## Write

Write `<run-root>/decompose/sub-questions.md` in this shape:

```markdown
# Sub-questions

Objective: <restate the objective in one line>

| ID | Sub-question | Claim type |
|---|---|---|
| SQ-01 | <one clear question> | competitive |
| SQ-02 | <one clear question> | quantitative |
| SQ-03 | <one clear question> | technical |
```

## Return

A one-line summary to the composer: how many sub-questions, and the claim-type spread (e.g. "5 sub-questions: 2 competitive, 2 quantitative, 1 technical, written to decompose/sub-questions.md").
