# AGENTS.md

Entry point for an agent operating or ingesting this repository. This is the single canonical agent-instruction file; [CLAUDE.md](CLAUDE.md) imports it, so the two cannot drift. Edit this file, never CLAUDE.md.

## What this is

`research-engine` is a research engine packaged as a Claude Code skill bundle: a `research` composer skill orchestrates primitive `research-{verb}` leaf skills and an independent verifier sub-agent. It produces a defensible research deliverable plus a fully traceable record of how it was produced. The differentiator is contestation made inspectable: a refuse-capable adversarial verifier and a per-source selection-and-trust log. See [README.md](README.md) for the human framing.

## Architecture

A single human gate (the locked brief) is followed by an autonomous pipeline: `decompose → select → retrieve → consolidate → [controller loop ↔ verify] → synthesize`, bounded by a depth/cycle governor. The controller is deterministic: it computes four signals (coverage, confidence, gap, contradiction) and routes by a fixed priority ladder, never "the model decides." The full design is in [docs/architecture.md](docs/architecture.md); its §6 is the canonical split of what ships in v1 versus what is designed-not-shipped.

## How to navigate

| Path | Role |
|---|---|
| `.claude/commands/research.md` | The composer: start here; it owns intake and orchestration. |
| `.claude/commands/research-{verb}.md` | The leaf skills: one verb, one job, writes one artifact. |
| `.claude/agents/research-verifier.md` | The independent verifier persona. |
| `schema/research-brief.md` | The intake contract: the brief every run is built from. |
| `docs/architecture.md` | The settled design; read §6 for what ships vs designed-not-shipped. |
| `docs/conventions.md` | Naming, trace-tree, and identifier rules. Read before producing any artifact. |
| `docs/source-catalog.md` | The v1 selection knowledge base. |
| `examples/` | A complete, real sample run: read it in trace order to see the output. |

## Run it

This is a Claude Code skill bundle, not a buildable program; there is no compile or test step. To run it: open the repo in Claude Code and invoke the composer skill `/research`; answer the ≤5-question intake (at minimum an `objective` and an `output_path`); the run is autonomous from the locked brief. The deliverable lands at `<output_path>/<run-id>/synthesis/result.md`, with the full trace beside it. To verify without running, read the committed run under `examples/` in trace order, or feed its `brief.md` back through `/research` and compare against its `synthesis/result.md` (the OpenAlex/World Bank spine is exact; open web pages may have drifted).

## Conventions

- Honesty about provenance is absolute: never imply a source was consulted that was not, or a capability shipped that was only designed.
- One artifact, one job, one documented location: nothing lands outside the run's trace tree.
- The controller is deterministic: read the signals, apply the documented ladder, log the decision; never substitute your own judgement for the routing policy.
- The verifier is independent by construction: a separate agent that re-fetches the cited sources itself (not the author's `retrieve/` files) and may run one corroboration query, with a mandate to refuse. The author of a claim never verifies it.
- Identifiers are zero-padded from `01`: `SQ-NN` sub-questions, `SRC-NN` sources (numbered within a sub-question), `CLM-NN` claims, `CHL-NN` challenges. No `00`.

## Status & provenance

Stable snapshot, v1, built with Claude Code; issues and PRs are not actively watched. The full pipeline (refuse-capable verifier + bounded control loop) runs end to end; the full adaptive controller, the multi-round verifier, a hard spend cap, and the ~95-source catalog are designed-not-shipped (see [docs/architecture.md](docs/architecture.md) §6). The build's raw decision log is kept private (gitignored); the settled decisions live in `docs/architecture.md` and `docs/conventions.md`.
