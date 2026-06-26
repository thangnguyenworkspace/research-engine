---
name: research-retrieve
description: For each selected source, fetch the material (built-in Web tools or the documented API endpoint) and write one retrieve/SQ-NN/SRC-NN.md per source: raw material plus source metadata (url, access tier, retrieved-at).
---

# research-retrieve

One job: get the material the `select` leaf chose, and record it with its provenance. You are a leaf. Read `docs/conventions.md` (trace layout, identifiers) and `docs/source-catalog.md` (how each source is queried). You read the selection logs, you write `retrieve/SQ-NN/SRC-NN.md`, and you return a short summary. You do not call other leaves. You retrieve only the sources the `select` leaf chose; do not add or substitute sources here.

## Input

The composer gives you the run root. Read every `<run-root>/select/SQ-NN.selection.md`. For each, the **Chosen** section names the source(s) and how to reach them.

## Do: per sub-question, per chosen source

Number sources `SRC-01` onward **within their sub-question** (each SQ restarts at SRC-01), two-digit zero-padded. Fetch each chosen source exactly as the catalog documents:

- **Web**: run `WebSearch` with a query derived from the sub-question, then `WebFetch` the most relevant result URL. Record the search query, the chosen URL, and the page material.
- **OpenAlex**: fetch `https://api.openalex.org/works?search=<query>&per-page=5` (URL-encode the query). Record the request URL and the returned works (title, year, DOI, cited_by_count, authors).
- **World Bank**: fetch `https://api.worldbank.org/v2/country/{ISO3}/indicator/{INDICATOR}?format=json`. Record the request URL and the returned series; note the most recent non-null value and its year.

Honesty about provenance is absolute: record only what you actually fetched. If a fetch fails or returns nothing, write the file and say so in **Material**; never invent content or imply a source answered when it did not.

## Write: one file per source

Write `<run-root>/retrieve/SQ-NN/SRC-NN.md`:

```markdown
# SRC-NN: <source name>

**Sub-question:** SQ-NN, <sub-question text>
**Source:** <Web | OpenAlex | World Bank>
**URL:** <the fetched URL, or the WebSearch query + chosen result URL>
**Access tier:** open
**Retrieved-at:** <ISO-8601 timestamp>

## Material

<the raw fetched material: page text, the relevant JSON fields, or the extracted figure. Trim to what is relevant to the sub-question; keep enough that the next leaf can make a traceable claim from it. If the fetch returned nothing, state that plainly here.>
```

## Return

A one-line summary: how many sources retrieved across how many sub-questions, and any that failed to fetch (e.g. "7 sources retrieved across 5 sub-questions; all fetched, written to retrieve/").
