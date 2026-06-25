---
name: research-synthesize
description: Produce the final deliverable from the consolidated draft — synthesis/result.md in the brief's requested form, with a confidence note and a provenance summary — and write run.json (run id, brief digest, sources used and their access tiers, reproducibility verdict).
---

# research-synthesize

One job: turn the consolidated draft into the deliverable the brief asked for, and record the run's machine-readable metadata. You are a leaf. Read `docs/conventions.md` (trace layout, `run.json` fields §5, reproducibility labelling §6). You read the brief and the draft, you write `synthesis/result.md` and `run.json`, and you return a short summary. You do not call other leaves. You synthesize only from the consolidated claims — every statement in the result traces to a CLM.

## Input

The composer gives you the run root. Read `<run-root>/brief.md` (the requested `deliverable` form and any `format_constraints`) and `<run-root>/consolidate/synthesis.draft.md` (the tagged claims).

## Write — the deliverable

Write `<run-root>/synthesis/result.md` in the **form and audience the brief's `deliverable` field requests** (a one-page brief, a comparison table, a memo — match it; honor `format_constraints` if present). Build it from the consolidated claims only. Keep the claim traceability visible: where a statement rests on a claim, reference it by `CLM-NN` so the result stays auditable back to its sources.

End the result with two fixed sections:

```markdown
## Confidence note

<2–4 lines: where the evidence is strong vs thin, any tensions carried from the draft, and what a reader should treat with caution. Honest, not hedged-to-death.>

## Provenance summary

| Source | Access tier | Claims it supports |
|---|---|---|
| <source> | open | CLM-01, CLM-03 |
| <source> | open | CLM-02 |

Reproducibility: <reproducible | checkable> — <one line of why>.
```

Honesty about provenance is absolute: list only sources actually used (trace them through the retrieve files), and never imply a capability ran that did not. This version has no verifier, so do not claim claims were independently contested.

## Write — run.json

Write `<run-root>/run.json`. This is the machine-readable record that makes the run checkable without reading every file. For this happy-path version there is no controller loop and no governor, so cycles is `1` and there is no governor stop reason.

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
  "cycles": 1,
  "version_note": "happy-path v1 — no verifier, no controller loop, no governor"
}
```

Set `reproducibility` per conventions §6: `reproducible` only if every source used was free/keyless (all v1 sources are open, so a clean v1 run is `reproducible`); `checkable` if any paid or gated source was load-bearing — and the v1 catalog has none, so this should be `reproducible` unless something changed. Never label a run `reproducible` when a paid source carried a load-bearing claim.

## Return

A one-line summary: the deliverable path, the reproducibility verdict, and the source count (e.g. "Deliverable at synthesis/result.md; reproducible; 3 sources, all open — run.json written").
