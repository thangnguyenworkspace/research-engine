# AGENTS.md

Entry point for an agent operating or ingesting this repository.

## What this repo is

`research-engine` is a research engine packaged as a Claude Code skill bundle. The top-level composer skill orchestrates a pipeline of primitive leaf skills and sub-agents; the result is a defensible research deliverable plus a fully traceable record of how it was produced. The differentiator is contestation made inspectable: a refuse-capable adversarial verifier and a per-source selection-and-trust log. See [README.md](README.md) for the human framing and [docs/architecture.md](docs/architecture.md) for the design.

## How it is organized

| Path | What lives there |
|---|---|
| `.claude/commands/` | The skills — `research` (composer) plus `research-{verb}` leaves. |
| `.claude/agents/` | Agent definitions, including the independent verifier. |
| `schema/research-brief.md` | The intake contract: the brief every run is built from. |
| `docs/architecture.md` | The settled architecture — pipeline, controller, governor, reproducibility. |
| `docs/conventions.md` | Naming, folder, and trace conventions. Read before producing any artifact. |
| `docs/decisions/` | Decision records (curated, public). |
| `scripts/` | Deterministic helpers — source adapters, governor accounting, grounding scorer. |
| `examples/` | A committed sample run — a complete trace tree to read. |

## How to operate it

1. Read [docs/conventions.md](docs/conventions.md) first. Every artifact you emit follows the naming and trace layout defined there.
2. A run starts from a locked brief (`schema/research-brief.md`). Do not begin retrieval until the brief is complete — the intake interview backfills missing fields.
3. Write every intermediate artifact to the run's trace folder at the brief's `output_path`. Nothing about a run should be untraceable.
4. The controller is deterministic. Read the signals, apply the documented policy, log the decision. Never substitute your own judgement for the routing policy.
5. The verifier is independent by construction: a separate agent, a separate source set, a mandate to refuse. Do not let the author of a claim also verify it.

## Conventions that bind you

- Honesty about provenance: never imply a source was consulted that was not, or a run was reproducible when a paid source was used.
- One artifact, one job, one documented location. No artifact lands outside the trace tree.
- Anti-over-engineering: the shipped version is a scoped v1. Designed-but-not-shipped capability is documented as such, not faked.
