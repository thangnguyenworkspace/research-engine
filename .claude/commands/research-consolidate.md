---
name: research-consolidate
description: Merge the retrieved material across sub-questions into a working synthesis (every claim tagged CLM-NN with its supporting SRC references) and write consolidate/synthesis.draft.md.
---

# research-consolidate

One job: turn raw retrieved material into a set of atomic, traceable claims. You are a leaf. Read `docs/conventions.md` (trace layout, the CLM/SRC identifier scheme). You read the retrieval files, you write `consolidate/synthesis.draft.md`, and you return a short summary. You do not call other leaves. You make claims only from what was retrieved: no outside knowledge, no filling gaps from memory.

## Input

The composer gives you the run root. Read `<run-root>/decompose/sub-questions.md` for the sub-questions, and every `<run-root>/retrieve/SQ-NN/SRC-NN.md` for the material.

## Do

1. Group the material by sub-question (the natural finding clusters).
2. Extract **atomic claims**: one assertion per claim, the smallest standalone statement that is either true or false. Split compound statements; a claim that bundles two facts cannot be cleanly contested or cited later. (This draft is what the verifier contests in a later version, so atomicity and traceability are the point.)
3. Tag each claim `CLM-01` onward (two-digit zero-padded, engine-wide across all sub-questions). After each claim, cite the source(s) that support it by their trace ids, `SQ-NN/SRC-NN`. Every claim must carry at least one SRC reference; if material does not support a claim, do not make it.
4. If two sources disagree, do not silently pick one. Record both as separate claims with their references, and note the tension in one line. (Resolving contradictions is the verifier's job in a later version; here, surface them.)
5. If a sub-question's retrieval came back empty, say so under that cluster rather than inventing a claim.

## Write

Write `<run-root>/consolidate/synthesis.draft.md`:

```markdown
# Synthesis draft

## SQ-NN: <sub-question text>

- **CLM-01**: <one atomic claim>. [SQ-NN/SRC-NN]
- **CLM-02**: <one atomic claim>. [SQ-NN/SRC-NN, SQ-NN/SRC-NN]

## SQ-NN: <sub-question text>

- **CLM-03**: <one atomic claim>. [SQ-NN/SRC-NN]

## Tensions

- **CLM-02 vs CLM-04**: <one line: what the two sources disagree on>.
```

(Omit the **Tensions** section if there are none.)

## Return

A one-line summary: how many claims, across how many sub-questions, and whether any tensions or empty clusters were noted (e.g. "9 claims across 5 sub-questions; 1 tension noted, written to consolidate/synthesis.draft.md").
