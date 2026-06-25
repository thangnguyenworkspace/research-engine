---
name: research
description: Run the research engine end to end — intake a brief, scaffold a run trace tree, then drive the leaf pipeline (decompose → select → retrieve → consolidate → synthesize) to a cited, reproducible deliverable with a full inspectable trace.
---

# research — the composer

You are the composer. You own intake and orchestration; the leaves do the work. Read `docs/conventions.md` before you start — every path and identifier below comes from it. Read `schema/research-brief.md` — it is the intake contract.

You orchestrate the leaves in sequence. You never do their jobs yourself: you do not decompose, select, retrieve, consolidate, or synthesize inline. You scaffold the tree, invoke each leaf, confirm it wrote its artifact, and pass control to the next.

## How a run loops

A run is a bounded loop, not a straight line. After the first pass the controller decides whether to stop or run one more remediation cycle, and the adversarial verifier can refuse a claim — which forces the loop to re-research rather than synthesize over it. The loop is governed: it runs at most `quick = 1`, `standard = 2`, `deep = 3` cycles (by the brief's `depth`), then force-stops, so it always terminates. The full multi-round adaptive controller is designed but not shipped — see `docs/architecture.md` §6; v1 ships this bounded loop with a real, refuse-capable verifier.

## 1. Intake

Compare the user's request against `schema/research-brief.md`. The three required fields are `objective`, `deliverable`, `output_path`. The recommended fields carry defaults; the optional fields are used only if the user volunteered them.

Run a guided interview of **at most five questions** to lock the brief:
- `output_path` is mandatory — always ask it if the user did not give a directory.
- For each missing recommended field, propose the schema default and ask the user to accept or adjust (`scope` inferred from the objective, `depth: standard`, `recency` none-unless-implied, `claim_types` inferred, `reproducibility: reproducible`, `budget` from depth). Note: this version has no governor, so `depth` and `budget` are recorded in the brief but do not bound execution yet.
- Recommend a value for everything; do not interrogate. If the objective makes a field obvious, state your inferred value and let the user correct it rather than asking blind.
- Stop at five questions. Fill anything still open with the schema default and note it in the locked brief.

Present the assembled brief and get the user's confirmation. Once confirmed, the brief is **locked** — do not change it after this point.

## 2. Scaffold the run

Compute the run id: `{YYYYMMDD}-{HHMMSS}-{slug}`, where `slug` is a short kebab form of the objective (a few words, lowercased, hyphen-separated). Use the current date and time.

Create the run trace tree at `<output_path>/<run-id>/` with these directories: `decompose/`, `select/`, `retrieve/`, `consolidate/`, `verify/`, `controller/`, `synthesis/`. Write the locked brief verbatim to `<run-id>/brief.md`.

If the brief's `depth` is not one of `quick` / `standard` / `deep`, treat it as `standard` (a 2-cycle ceiling) when you pass it to the controller.

Hold the run root path (`<output_path>/<run-id>/`) — every leaf needs it.

## 3. Drive the pipeline

Invoke the leaves via the Skill tool. Prefer to run each in its own sub-agent so its working context stays out of yours; pass the sub-agent the run root path and tell it which leaf to invoke and that the leaf reads and writes only inside the trace tree. After each leaf, confirm the named artifact exists before moving on. If a leaf reports it could not write its artifact, stop and tell the user — do not fabricate downstream work.

### First pass

1. **`/research-decompose`** — input: the run root. Output: `decompose/sub-questions.md` (SQ-01..SQ-NN with claim types).
2. **`/research-select`** — input: the run root. Output: `select/SQ-NN.selection.md`, one per sub-question. This is the differentiator artifact; do not skip or summarise it.
3. **`/research-retrieve`** — input: the run root. Output: `retrieve/SQ-NN/SRC-NN.md`, one per selected source.
4. **`/research-consolidate`** — input: the run root. Output: `consolidate/synthesis.draft.md` (claims tagged CLM-NN → SRC references).
5. **`/research-verify`** — input: the run root. Dispatch under the `research-verifier` agent; independence is required, so this leaf must run in its own sub-agent that did not produce the claims. Output: `verify/contestation.md` (per-claim, refuse-capable verdicts).

### The control loop

6. **`/research-control`** — input: the run root, the current cycle number (start at 1), and the brief's `depth`. It computes the four signals, applies the governor + priority ladder, appends to `controller/loop-log.md`, and returns a decision.
   - **`STOP`** (criterion-met or governor) → leave the loop, go to synthesize.
   - A **remediation** (`re-research` / `supplement-gap` / `go-deeper` / `re-retrieve`) → re-run only the targeted sub-questions/claims back through select → retrieve → consolidate, then `/research-verify` again, then call `/research-control` with the cycle number incremented. Never synthesize while a refusal stands and cycles remain.
   - The governor guarantees termination: `research-control` force-stops at the depth ceiling, so the loop cannot run forever. Track the cycle count and the final stop-reason to pass to synthesize.

### Synthesize

7. **`/research-synthesize`** — input: the run root, the cycles run, and the final stop-reason. Output: `synthesis/result.md` and `run.json`. It honors the contestation: a refused claim is never presented as established.

Each leaf returns a short summary. Carry only the summary forward; the artifacts on disk are the source of truth, not your memory of them.

## 4. Return

Tell the user:
- The final deliverable path: `<run-id>/synthesis/result.md`.
- The run root, so they can read the full trace.
- The contestation outcome from `verify/contestation.md`: the grounding score and how many claims were refused.
- The reproducibility verdict and the cycles run, from `run.json`.
- One line that v1 ships a bounded loop, not the full multi-round adaptive controller (see `docs/architecture.md` §6), so the user knows what ran.
