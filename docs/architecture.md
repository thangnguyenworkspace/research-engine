# Architecture

The design of record for `research-engine`. It describes the whole engine and marks clearly what ships in the current version versus what is designed but not yet built. The build is staged; this document leads the build, so a section describing the verifier or controller is the target the code is held to, not a claim that it already runs. Each skill states inline what it actually wires versus what it defers (e.g. the composer's `How a run loops` note), and §6 below is the canonical ships-now-versus-designed split.

## 1. What the engine is

A research engine that contests its own findings and shows its work. It takes a research objective, decomposes it, selects sources and logs why, retrieves real evidence, consolidates it into traceable claims, contests those claims with an independent verifier that can refuse the unsupported ones, and synthesizes a defensible result, bounded by a governor so a stranger can re-run it affordably. The differentiator and its rationale are in [README.md](../README.md); the pillars it commits the design to are: refuse-capable adversarial verification (the headline), inspectable source selection-and-trust (the proof), a broad real-source stack (the substrate), and open + reproducible runs (the public-evidence pillar).

It ships as a Claude Code skill bundle: a composer skill (`research`) orchestrates primitive leaf skills (`research-{verb}`) and sub-agents. The control structure is orchestrator-worker (the composer is the orchestrator, the leaves are the workers), which gives the selection log a clean per-sub-question home and the verifier its independence by construction.

## 2. Pipeline

A run is a single human gate (the brief) followed by an autonomous pipeline. After the brief is locked, nothing requires the user until the result is ready.

```
INTAKE  brief template: compare request vs required fields, backfill gaps in <=5 questions,
        mandatory output/trace path -> LOCK BRIEF        <- the only human gate
   |
   v   (autonomous from here; nested sub-agents; clean surface)
decompose -> select -> retrieve -> consolidate -> [ controller loop <-> verify ] -> synthesize
   |
   v
FINAL RESULT to the user  +  a complete, traceable run folder on disk
```

| Stage | Leaf | Does | Writes |
|---|---|---|---|
| Intake | `research` (composer) | Lock the brief; scaffold the run tree | `brief.md` |
| Decompose | `research-decompose` | Objective -> typed sub-questions | `decompose/sub-questions.md` |
| Select | `research-select` | Choose sources, log why | `select/SQ-NN.selection.md` |
| Retrieve | `research-retrieve` | Fetch the chosen sources | `retrieve/SQ-NN/SRC-NN.md` |
| Consolidate | `research-consolidate` | Atomic, source-tagged claims | `consolidate/synthesis.draft.md` |
| Verify | `research-verify` | Contest load-bearing claims; refuse the unsupported | `verify/contestation.md` |
| Synthesize | `research-synthesize` | The deliverable + machine record | `synthesis/result.md`, `run.json` |

The trace layout and identifier scheme are fixed in [conventions.md](conventions.md). The selection knowledge base is [source-catalog.md](source-catalog.md).

## 3. The controller

The controller decides what the engine does after each cycle. Its defining constraint: it runs on explicit, computed signals and a fixed, readable policy, never an opaque "the model decides." The intelligence lives in *producing* the signal values (which are logged with their reasoning); the routing itself is a deterministic priority ladder anyone can read.

**The four signals**, each written to `controller/loop-log.md`:

| Signal | Measures | How it is computed | Drives |
|---|---|---|---|
| Coverage | Is the whole decomposition answered | Fraction of sub-questions with enough acceptable-type sources (deterministic) | supplement-gap / go-deeper |
| Confidence | Does each claim hold up against its source | Per-claim groundedness judgement -> supported / partial / unsupported; aggregated | targeted re-retrieve / go-deeper |
| Gap | What is missing | Unanswered sub-questions + newly-surfaced needs | supplement-gap / explore-adjacent |
| Contradiction | Conflict among sources or a verifier refusal | Count of source-conflicts + `unsupported/refuse` verdicts | adversarial-round / re-research |

**Each cycle the controller stops or routes, in this order:** stop with `criterion-met` if the success criterion holds (coverage ≥ 0.8, confidence ≥ 0.7, no contradiction); else force-stop with `governor` if the cycle ceiling is reached (the backstop that guarantees termination, carrying any standing refusal honestly into the result); else apply the priority ladder (deterministic; first match wins):

```
1. refusal or contradiction pending?  -> adversarial-round / re-research   (never synthesize over a refuted load-bearing claim)
2. gap present?                        -> supplement-gap / explore-adjacent
3. coverage below threshold?          -> go-deeper on uncovered sub-questions
4. confidence below threshold?        -> targeted re-retrieve on weak claims
5. branch-worthy insight + budget?    -> branch (optional, governed)
6. otherwise                          -> STOP -> synthesize
```

In v1's keyless stack every sub-question gets at least a web source, so coverage and confidence rarely fall below their thresholds; the contradiction rung (a verifier refusal or an unresolved tension) is the primary live path, and ladder rungs 2–4 mainly fire under a retrieval failure. The full ladder is the documented end-state, exercised more as the source stack and the adaptive controller grow (§6).

The adversarial verifier feeds the loop rather than gating it at the end: its refusals are a contradiction signal that can trigger re-research, so contestation shapes the research instead of rubber-stamping it.

## 4. The adversarial verifier

The headline. An independent verifier (a separate agent that re-fetches each cited source itself, never trusting the author's `retrieve/` files, and may run one corroboration query, with an explicit mandate to break the claim) challenges each load-bearing claim against its cited evidence and returns a verdict: `supported`, `partial`, or `unsupported / refuse`. Independence is a hard design rule: the agent that authored a claim never verifies it, because same-author self-critique shares the author's blind spots. Judge-bias controls (reference-guided grading; no knowledge of which path produced a claim) apply. Verifiability is operationalized FACT-style: extract each claim-source pair, fetch the source, judge whether it supports the claim, and report both accuracy and how many claims were even checkable, penalizing un-cited claims rather than ignoring them.

The verdicts are an inspectable artifact (`verify/contestation.md`) and, doubled, the contradiction signal the controller reads.

## 5. Governor and reproducibility

A run is bounded so it terminates and stays cheap enough to repeat, the same mechanism that makes reproducibility affordable.

- **Depth/cycle ceiling.** A hard cap on cycles and recursion depth, set from the brief's `depth` (a spend cap is recorded but not yet enforced; see §6). When the ceiling is hit, the controller force-stops and synthesizes from what it has, recording the stop reason.
- **Measurable stopping criterion.** The loop stops when coverage and confidence clear their thresholds and no contradiction is pending, a measured condition, not a felt one.
- **Reproducibility by type.** Each run is labelled by the weakest source it relied on: `reproducible` (every source free/keyless, so a stranger re-runs and gets the same central result) or `checkable` (a paid/gated source was load-bearing, so the result is checkable against the trace, not freely re-runnable). The label and its cause are recorded in `run.json`. Because the engine ships as a skill bundle, "a stranger" means a Claude Code user; stated plainly rather than implied.

## 6. What ships now vs designed-not-shipped

The current version is a deliberately scoped v1 (the smallest thing that runs end to end and proves the differentiator), not a reduced ambition. The fuller design above is documented so the gap is honest, not hidden.

| Capability | v1 ships | Designed, not yet shipped |
|---|---|---|
| Pipeline | Full straight-through: decompose -> select -> retrieve -> consolidate -> synthesize | none |
| Source stack | 3 keyless sources (web, OpenAlex, World Bank) | The full ~95-source catalog across 8 clusters |
| Selection | Deterministic trigger -> shortlist -> fit + verifiability scoring, logged | CRAG-style escalation ladder |
| Verifier | A real, scoped, refuse-capable pass (re-fetches cited sources + ≤1 corroboration query) backed by a FACT-style grounding check | Multi-round adversarial rounds + an independent separate-source-set, driven by the controller |
| Controller | Fixed-few cycles + the priority ladder | The full adaptive loop; a novelty/saturation signal |
| Governor | Depth/cycle ceiling + measurable stop (criterion-met) | A hard spend cap + per-source call budgeting |

The commitment from the differentiator stands regardless of scope: v1 must ship a verifier that *visibly refuses* on the sample run, not a checkbox that never fires.
