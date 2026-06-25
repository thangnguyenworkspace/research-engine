# research-engine

A research engine that contests its own findings and shows its work.

Most deep-research tools cite their sources but never argue with them, and none show why they trusted one source over another. `research-engine` makes two things into first-class, inspectable artifacts: a refuse-capable adversarial verification pass that can return *the evidence does not support this*, and a per-source selection-and-trust log that records why each source was chosen, why others were rejected, and how far each was trusted. Every run is open and reproducible over a stack of real, mostly free public sources.

> **Status: scaffolding.** The architecture and conventions are settled; the pipeline is being built in stages. See [docs/architecture.md](docs/architecture.md) for the design and [docs/decisions/](docs/decisions/) for the decision record. Run instructions land once the first end-to-end path is in.

## What it does

You give it a research objective and an output location. It then:

1. **Decomposes** the objective into typed sub-questions.
2. **Selects** sources per sub-question and logs why each was chosen and why others were not.
3. **Retrieves** from a stack of real sources — web, academic, structured and government data.
4. **Consolidates** findings into a working synthesis with every claim tagged to its sources.
5. **Contests** load-bearing claims with an independent verifier that can refuse the unsupported ones.
6. **Synthesizes** a final, defensible result with its full provenance and a confidence record.

A deterministic controller decides what to do after each cycle from explicit signals — coverage, confidence, gaps, contradictions — rather than an opaque "the model decides," and a budget-and-depth governor bounds every run so a stranger can re-run it without unbounded spend.

## What makes it different

- **Contestation, not just citation.** A separate verifier with its own sources attacks each load-bearing claim and can refuse it. Citation-checkers confirm a quote exists; this asks whether the evidence actually supports the claim.
- **Inspectable selection and trust.** For every source: why this one, why not the others, how fresh, how primary, how far trusted — written down, not hidden inside a tool call.
- **Open and reproducible.** The default source set is free and keyless. When a paid source is unavoidable, the run is labelled *checkable*, not *reproducible* — honestly, per source.
- **Bounded by design.** A measurable stopping rule and a hard budget make every run terminate and stay affordable to repeat.

## How a run is laid out

Each run scaffolds a complete, traceable folder at the path you give it — the brief, the decomposition, the per-source selection logs, the raw retrieval, the contestation record, the controller's loop log, and the final result. The layout and naming are fixed and documented in [docs/conventions.md](docs/conventions.md), so any reader (human or agent) can navigate a run they have never seen.

## Reproducing a run

_Coming with the first end-to-end build stage._

## License

[MIT](LICENSE).
