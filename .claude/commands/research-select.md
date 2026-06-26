---
name: research-select
description: The selection leaf: for each sub-question, choose sources from the v1 catalog and write an inspectable selection log (candidates considered, fit-for-claim and verifiability judgement per candidate, what was chosen and what was rejected and why, and how far each chosen source is trusted).
---

# research-select

This is the differentiator. The whole point of the engine is that a reader can see **why this source, and why not the others**, so the selection log you write is the deliverable, not a side effect. A rubber stamp ("picked the web") fails the job. Make every judgement legible.

You are a leaf. Read `docs/conventions.md` (trace layout, identifiers) and `docs/source-catalog.md` (the only sources you may choose from, the tiny v1 set). You read `decompose/sub-questions.md`, you write one `select/SQ-NN.selection.md` per sub-question, and you return a short summary. You do not call other leaves. You may only choose sources that appear in the catalog; if the catalog has nothing that fits, say so in the log rather than inventing a source.

## Input

The composer gives you the run root. Read `<run-root>/decompose/sub-questions.md` for the sub-questions and their claim types.

## How to select (v1, three moves)

For each sub-question, in order:

1. **Deterministic trigger (free, before any judgement).** The claim type routes first. In the v1 catalog: `quantitative` country-level statistics trigger World Bank; research-basis `factual`/`technical` questions trigger OpenAlex; everything else, and any open-web `factual`/`competitive`/`technical` question, triggers the built-in Web tools. The web is also the universal fallback when nothing more specific fits.
2. **Shortlist from the catalog.** List the catalog sources that could plausibly answer this sub-question, usually the triggered source plus the web as a candidate. Naming a candidate does not mean choosing it; it means it was considered.
3. **Fit-for-claim + verifiability score.** Judge each shortlisted candidate on two axes, and let the scores decide:
   - **Fit-for-claim**: is this source the *right type* for this specific claim? A quantitative country statistic fits World Bank (primary owner) over a web page that merely quotes a number (derivative). A research-basis claim fits OpenAlex (peer-reviewed/preprint) over a vendor blog.
   - **Verifiability**: how primary, citable, fresh, and re-checkable is it? Prefer the primary owner of a fact over a source that restates it. Note the access tier (all v1 sources are open/keyless, so all are reproducible).

   Score each axis `high` / `medium` / `low`. Choose the candidate(s) that win on fit first, verifiability second. Reject the rest **with a reason**: "less primary for this claim", "would only restate the figure", "wrong claim type". A rejection with a reason is what makes the log informative.

Skip the CRAG escalation ladder; it is a later version. Do not re-search or broaden here; choose from the catalog once and log the choice.

## Trust calibration

For each **chosen** source, state how far it is trusted for this claim: `primary` (the authoritative owner, cite directly), `corroborating` (good, but confirm against another source), or `context-only` (use for framing, not as the load-bearing citation). This is the "how far trusted" half of the log; do not omit it.

## Write: one file per sub-question

Write `<run-root>/select/SQ-NN.selection.md`. Use exactly this structure so every selection log reads the same:

```markdown
# Selection: SQ-NN

**Sub-question:** <the sub-question text>
**Claim type:** <factual | quantitative | regulatory | competitive | technical>
**Deterministic trigger:** <which catalog source the claim type routed to, and why>

## Candidates considered

| Source | Fit-for-claim | Verifiability | Access tier | Verdict |
|---|---|---|---|---|
| <source> | high: <one-line why> | high: <one-line why> | open | chosen |
| <source> | medium: <one-line why> | low: <one-line why> | open | rejected |

## Chosen

- **<source>** (trust: <primary | corroborating | context-only>). <one line: what it will answer and how it will be queried, per the catalog>.

## Rejected

- **<source>**: <the reason it lost: less primary, wrong claim type, would only restate, etc.>.
```

Every chosen source here must be retrievable by the next leaf, so name the exact catalog source (the Web tools, OpenAlex, or World Bank) and how it is reached.

## Worked example

For a sub-question `SQ-02: What was Vietnam's GDP in current US dollars in the most recent reported year? (quantitative)`:

```markdown
# Selection: SQ-02

**Sub-question:** What was Vietnam's GDP in current US dollars in the most recent reported year?
**Claim type:** quantitative
**Deterministic trigger:** quantitative country-level statistic → World Bank (the primary owner of the indicator).

## Candidates considered

| Source | Fit-for-claim | Verifiability | Access tier | Verdict |
|---|---|---|---|---|
| World Bank | high: GDP (current US$) is a first-class World Bank indicator (NY.GDP.MKTP.CD), keyed by country and year | high: primary owner; exact, dated, re-queryable by stable indicator code | open | chosen |
| Web (WebSearch/WebFetch) | medium: the figure is findable on the open web | low: any page is a derivative that restates the World Bank or IMF number, often without the reporting year | open | rejected |

## Chosen

- **World Bank** (trust: primary). Answers the GDP figure directly; queried at `https://api.worldbank.org/v2/country/VN/indicator/NY.GDP.MKTP.CD?format=json`, taking the most recent non-null year.

## Rejected

- **Web (WebSearch/WebFetch)**: would only restate the World Bank/IMF figure; using a derivative for a primary-owned statistic loses the reporting year and the exact value. Reserved as a fallback only if the API is unreachable at run time.
```

## Return

A one-line summary: how many selection logs written, and the source spread (e.g. "5 selection logs: 3 web, 1 World Bank, 1 OpenAlex, written to select/").
