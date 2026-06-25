# Conventions

The naming, folder, and trace rules every part of the engine follows. The point is that any run — and any artifact inside it — is predictable, navigable, and traceable by a reader who has never seen it before. These conventions are product surface: a reviewing agent ingests the trace tree to report what the engine is, so the structure has to be legible on its own.

## 1. Repository layout

```
research-engine/
├── README.md              human entry: what it is, what it proves
├── AGENTS.md              agent entry: how to operate / ingest the repo
├── LICENSE                MIT
├── .claude/
│   ├── commands/          the skills (composer + leaves)
│   └── agents/            agent definitions (incl. the independent verifier)
├── schema/
│   └── research-brief.md  the intake contract
├── docs/
│   ├── architecture.md    the settled design
│   ├── conventions.md     this file
│   └── decisions/         curated decision records (ADR-style)
├── scripts/               deterministic helpers
└── examples/              a committed sample run (a complete trace tree)
```

## 2. Skill naming

- The composer (top-level orchestrator) is `research`.
- Every leaf is `research-{verb}`, one verb, one job: `research-decompose`, `research-select`, `research-retrieve`, `research-consolidate`, `research-verify`, `research-synthesize`.
- A leaf does its one job, writes its artifact to the trace tree, and returns a short summary. Leaves never call each other; the composer orchestrates.

## 3. The run trace tree

Every run scaffolds one folder at the brief's `output_path`, named with the run id:

```
<output_path>/<run-id>/
├── brief.md                     the locked brief — the input contract for this run
├── decompose/
│   └── sub-questions.md         SQ-01 … SQ-NN, each with a claim type
├── select/
│   └── SQ-01.selection.md       per sub-question: candidates, scores, why chosen / rejected
├── retrieve/
│   └── SQ-01/
│       └── SRC-01.md            one file per source consulted, raw material + metadata
├── consolidate/
│   └── synthesis.draft.md       working synthesis; every claim tagged CLM-NN → sources
├── verify/
│   └── contestation.md          per claim: challenge, evidence check, verdict
├── controller/
│   └── loop-log.md              per cycle: signals read → action taken → why
├── synthesis/
│   └── result.md                the final deliverable
└── run.json                     run metadata (see §5)
```

A leaf only ever writes inside this tree. If an artifact has no documented home here, it does not get created.

## 4. Identifiers

Stable, zero-padded, two digits, referenced everywhere they are relevant so any claim traces back to its evidence:

| Prefix | Thing | Example |
|---|---|---|
| `SQ-NN` | sub-question | `SQ-03` |
| `SRC-NN` | a source consulted for a sub-question | `SQ-03/SRC-02` |
| `CLM-NN` | a claim in the synthesis | `CLM-07` |
| `CHL-NN` | a challenge raised by the verifier | `CHL-04` |

Numbering starts at `01` within its scope (sub-questions run engine-wide; sources are numbered within their sub-question). No `00` prefix.

## 5. Run id and metadata

- **Run id:** `{YYYYMMDD}-{HHMMSS}-{slug}`, where `slug` is a short kebab form of the objective. Sortable and unique.
- **`run.json`** carries the machine-readable record: run id, brief digest, cycles run, budget allotted vs spent, governor stop reason, the source access tiers used, and the reproducibility verdict (`reproducible` | `checkable`). This is what makes a run independently checkable without reading every file.

## 6. Reproducibility labelling

Each run is labelled by the weakest source it depended on:

- **reproducible** — every source was free/keyless or free-key; a stranger can re-run and get the same central result.
- **checkable** — at least one paid or gated source was load-bearing; the result can be checked against the recorded trace but not freely re-run. The `run.json` names which sources forced the label.

Never label a run `reproducible` when a paid source carried a load-bearing claim.

## 7. Writing

- Prose is not hard-wrapped: one paragraph is one line.
- Plain, factual voice. State what a thing is and does; let the artifacts carry the weight.
- Honesty about provenance is absolute: never imply a source was consulted that was not, or a capability shipped that was only designed.
