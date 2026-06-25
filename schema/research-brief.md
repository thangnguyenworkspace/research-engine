# Research Brief

The intake contract. Every run is built from a completed brief, and the brief is the single input a stranger needs to reproduce a run. The composer compares an incoming request against these fields, then runs a short interview (at most five questions) to backfill what is missing, recommending sensible defaults for anything the user does not care to specify. Once locked, the brief is copied verbatim into the run trace as `brief.md`.

The design tension this guards against: too thin a brief and the pipeline guesses; too heavy and intake becomes a chore. So only three fields are genuinely required; the rest carry defaults and are confirmed, not interrogated.

## Required

The run will not start without these.

| Field | What it is |
|---|---|
| `objective` | The research question or goal, stated in one clear sentence. |
| `deliverable` | The form and audience of the final output — e.g. "a one-page competitive brief for a GTM lead". |
| `output_path` | Where the run scaffolds its trace tree and writes the deliverable. The user points to a directory. |

## Recommended (defaulted, confirmed in the interview)

The engine proposes a value for each; the user adjusts or accepts.

| Field | What it is | Default |
|---|---|---|
| `scope` | What is explicitly in and out of bounds. | Inferred from the objective; confirmed. |
| `depth` | Quick scan, standard, or deep. Maps to the governor's cycle and budget ceiling. | `standard` |
| `recency` | How fresh the evidence must be. | No constraint unless the objective implies one. |
| `claim_types` | The kinds of claims expected — factual, quantitative, regulatory, competitive, technical. Routes source selection. | Inferred from the objective. |
| `reproducibility` | `reproducible` (free sources only) or `checkable-ok` (paid sources allowed when load-bearing). | `reproducible` |
| `budget` | Hard ceiling on spend and depth for this run. | Set from `depth`. |

## Optional

Used when present, never asked for.

| Field | What it is |
|---|---|
| `known_sources` | Seed URLs or sources the user already trusts. |
| `prior_context` | Anything already known that the engine should not re-derive. |
| `avoid_sources` | Sources or domains to exclude. |
| `format_constraints` | Length, structure, or style requirements for the deliverable. |

## Example

```yaml
objective: "Which vendors lead the AI meeting-notes market for sales teams, and on what basis?"
deliverable: "A one-page competitive brief for a founding GTM lead, with a comparison table."
output_path: "~/research/ai-notetakers"
scope:
  in: ["sales-team use cases", "vendors with public pricing"]
  out: ["general-purpose transcription", "consumer apps"]
depth: standard
recency: "last 12 months"
claim_types: [competitive, quantitative]
reproducibility: reproducible
budget: { cycles: 3, usd: 2.00 }
known_sources: []
```
