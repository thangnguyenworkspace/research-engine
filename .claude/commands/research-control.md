---
name: research-control
description: The deterministic controller leaf: compute the four signals (coverage, confidence, gap, contradiction), check the governor, apply the fixed priority ladder, emit ONE decision, and append it to controller/loop-log.md.
---

# research-control

One job: read the run's current state, compute four explicit signals, and emit one decision by a fixed, readable policy, never "the model decides." The intelligence is in *computing* the signals (logged with their reasoning); the routing is a deterministic ladder anyone can read. You are a leaf. Read `docs/conventions.md` (trace layout, identifiers) and `docs/architecture.md` §3 (the four signals + the priority ladder) and §5 (the governor). You read the trace artifacts, you append to `controller/loop-log.md`, and you return the decision. You do not call other leaves; the composer acts on your decision and re-runs whatever leaves the decision targets.

## Input

The composer gives you: the run root, the current cycle number (1-based), and the depth (from `brief.md`). Read:
- `<run-root>/decompose/sub-questions.md`: the full set of SQ-NN (the denominator for coverage and gap).
- `<run-root>/select/` and `<run-root>/retrieve/`: which sub-questions actually got a source retrieved.
- `<run-root>/consolidate/synthesis.draft.md`: the CLM-NN claims and which SQ each answers; the **Tensions** section, if any.
- `<run-root>/verify/contestation.md`: per-claim verdicts (supported / partial / unsupported-refuse) and the refusal count.

## Compute the four signals

Each is a concrete computation, not a feel. State the numbers.

- **coverage** = (number of sub-questions that have at least one retrieved source yielding a non-refused claim) / (total sub-questions). A sub-question counts as covered only if it has a CLM that a source answered and the verifier did not refuse.
- **confidence** = (number of load-bearing claims with verdict `supported` in contestation.md) / (total load-bearing claims). Partial and refused do not count toward confidence.
- **gap** = the list of sub-questions with no supported claim (no CLM, or all its CLMs partial/refused), plus any unanswered need surfaced in the draft. Name them by SQ-NN.
- **contradiction** = (count of `unsupported / refuse` verdicts in contestation.md) + (count of unresolved source tensions in the draft's **Tensions** section).

## Decide

Check in this exact order. First match wins.

1. **MEASURABLE STOP (success).** If `coverage ≥ 0.8` AND `confidence ≥ 0.7` AND `contradiction = 0`, emit `STOP` with stop-reason `criterion-met`. This is the success stop, checked first so that a run which both meets the criterion AND sits at the governor ceiling reports the meaningful reason, that it succeeded, not merely that it ran out of budget.
2. **GOVERNOR (hard backstop).** The v1 cycle ceiling by depth: `quick = 1`, `standard = 2`, `deep = 3`. If the criterion is not met and the current cycle number has reached the ceiling, force `STOP` with stop-reason `governor`: the run is out of budget; it synthesizes from what it has, carrying any standing refusals or gaps honestly into the result. This guarantees termination.
3. **PRIORITY LADDER** (architecture §3; first match wins):
   1. refusal or contradiction pending (`contradiction > 0`) → `re-research`: target the sub-questions / claims behind the refusals and tensions. Never synthesize over a refuted load-bearing claim.
   2. gap present (`gap` non-empty) → `supplement-gap`: target the gap sub-questions.
   3. `coverage < 0.8` → `go-deeper`: target the uncovered sub-questions.
   4. `confidence < 0.7` → `re-retrieve`: target the weak (partial/unsupported) claims.
   5. otherwise → `STOP` with stop-reason `criterion-met`.

(The optional `branch` action is not in v1; omit it.)

## Write

Append one block per cycle to `<run-root>/controller/loop-log.md` (create the file on cycle 1). Never overwrite a prior cycle's block; the loop log is the history.

```markdown
## Cycle <N>

- **Coverage:** <fraction> (<covered>/<total> sub-questions): <one line of how it was read>
- **Confidence:** <fraction> (<supported>/<total> claims): <one line>
- **Gap:** <SQ-NN, SQ-NN | none>
- **Contradiction:** <count> (<refusals> refusals + <tensions> tensions)
- **Governor:** cycle <N> of <ceiling> (depth: <quick|standard|deep>)
- **Decision:** <re-research | supplement-gap | go-deeper | re-retrieve | STOP>
- **Targets:** <SQ-NN / CLM-NN this action re-runs, or "none" for STOP>
- **Stop-reason:** <governor | criterion-met | none>
- **Why:** <one line: which rule fired and the values that triggered it>
```

## Return

Return the decision to the composer:
- The **action** (`re-research` | `supplement-gap` | `go-deeper` | `re-retrieve` | `STOP`).
- If `STOP`, the **stop-reason** (`governor` | `criterion-met`).
- If a remediation, the **targets**: the exact SQ-NN sub-questions or CLM-NN claims it re-runs, so the composer knows what to feed back into the pipeline.

(e.g. "Decision: re-research; targets SQ-03, CLM-07 (refused). Cycle 1 of 2. Written to controller/loop-log.md." or "Decision: STOP; criterion-met (coverage 1.0, confidence 0.83, contradiction 0). Cycle 2 of 2.")
