# Example runs

Real, unedited runs of the engine. Nothing here is staged: every source was fetched live, the verifier ran independently in its own context, and the trace is exactly what the engine produced.

## 20260625-135009-ai-notetaker-sea-gtm

A GTM market-opportunity brief — "Assess the market opportunity for an AI sales-call notetaker targeting SMB sales teams in Southeast Asia (Vietnam, Indonesia)."

Read it in trace order: `brief.md` → `decompose/sub-questions.md` → `select/` → `retrieve/` → `consolidate/synthesis.draft.md` → `verify/contestation.md` → `controller/loop-log.md` → `synthesis/result.md`.

What this run shows, end to end:

- **The verifier refused a real claim.** In cycle 1 the independent verifier caught CLM-02 — a Gong positioning claim — citing a web page that never mentions Gong, and refused it. A genuine defect, not a staged one. Several pricing claims were downgraded for the same root cause: borrowing a citation to a page that did not contain the figure.
- **Contestation shaped the research.** The refusal drove the controller to re-research rather than synthesize over the weak claim (see `controller/loop-log.md`, cycle 1 → cycle 2). The remediation re-grounded the claims to vendor-primary sources and materially corrected stale figures (Otter Pro $10 → $8.33; a phantom Fathom tier removed). Grounding rose from 26/34 to 33/33.
- **It refused to fabricate.** No open source scoped to the SMB-sales-notetaker SEA market, so the engine left the market size honestly unanswered (CLM-31) instead of inventing a number — and dropped a paywalled figure rather than rely on a source a stranger cannot reach.
- **It is reproducible.** Every load-bearing source is free and keyless; the central result can be re-run from the same brief.
