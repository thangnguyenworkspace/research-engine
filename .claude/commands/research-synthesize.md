---
name: research-synthesize
description: Produce the final deliverable from the consolidated draft — synthesis/result.md in the brief's requested form, with a confidence note and a provenance summary — and write run.json (run id, brief digest, sources used and their access tiers, reproducibility verdict).
---

# research-synthesize

One job: turn the consolidated draft into the deliverable the brief asked for, and record the run's machine-readable metadata. You are a leaf. Read `docs/conventions.md` (trace layout, `run.json` fields §5, reproducibility labelling §6). You read the brief and the draft, you write `synthesis/result.md` and `run.json`, and you return a short summary. You do not call other leaves. You synthesize only from the consolidated claims — every statement in the result traces to a CLM.

## Input

The composer gives you the run root, the cycles run, and the final stop-reason. Read `<run-root>/brief.md` (the requested `deliverable` form and any `format_constraints`), `<run-root>/consolidate/synthesis.draft.md` (the tagged claims), and `<run-root>/verify/contestation.md` (the per-claim verdicts). The contestation is authoritative: a claim's verdict governs whether and how it may appear in the result.

## Write — the deliverable

Write `<run-root>/synthesis/result.md` in the **form and audience the brief's `deliverable` field requests** (a one-page brief, a comparison table, a memo — match it; honor `format_constraints` if present). Build it from the consolidated claims, filtered by each claim's contestation verdict:

- `supported` — use freely.
- `partial` — use only with the caveat the verifier named; never state it more strongly than the evidence allows.
- `unsupported / refuse` — do NOT present it as established. Drop it, or — if it is material to the objective — surface it explicitly as a claim the engine could not substantiate. A refused claim never reads as fact.

Keep the claim traceability visible: where a statement rests on a claim, reference it by `CLM-NN` so the result stays auditable back to its sources.

End the result with two fixed sections:

```markdown
## Confidence note

<2–4 lines: the grounding score from contestation.md (claims supported vs checked), any claims refused or carried only as partial, and what a reader should treat with caution. Honest, not hedged-to-death.>

## Provenance summary

| Source | Access tier | Claims it supports |
|---|---|---|
| <source> | open | CLM-01, CLM-03 |
| <source> | open | CLM-02 |

Grounding: <supported>/<checked> claims supported by the verifier; <N> refused.
Reproducibility: <reproducible | checkable> — <one line of why>.
```

Honesty about provenance is absolute: list only sources actually used (trace them through the retrieve files), and never imply a capability ran that did not. The verifier ran — reflect its verdicts faithfully: never report a refused claim as supported, and never inflate the grounding score.

## Write — run.json

Write `<run-root>/run.json`. This is the machine-readable record that makes the run checkable without reading every file. Record the real `cycles` the controller ran and the final `stop_reason` (both passed by the composer), and the contestation outcome from `verify/contestation.md`.

```json
{
  "run_id": "<the run id>",
  "brief_digest": "<one-line restatement of the objective + deliverable>",
  "sources_used": [
    { "source": "World Bank", "access_tier": "open" },
    { "source": "OpenAlex", "access_tier": "open" },
    { "source": "Web", "access_tier": "open" }
  ],
  "reproducibility": "reproducible",
  "cycles": "<number of controller cycles run>",
  "stop_reason": "<criterion-met | governor>",
  "grounding": { "supported": "<N>", "checked": "<N>", "refused": "<N>" }
}
```

Set `reproducibility` per conventions §6: `reproducible` only if every source used was free/keyless (all v1 sources are open, so a clean v1 run is `reproducible`); `checkable` if any paid or gated source was load-bearing — the v1 catalog has none, so this should be `reproducible` unless something changed. Never label a run `reproducible` when a paid source carried a load-bearing claim.

## Return

A one-line summary: the deliverable path, the reproducibility verdict, and the source count (e.g. "Deliverable at synthesis/result.md; reproducible; 3 sources, all open — run.json written").
