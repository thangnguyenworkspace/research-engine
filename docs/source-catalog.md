# Source Catalog (v1)

The selection knowledge base the `research-select` leaf chooses from. This is a deliberately tiny v1 subset: three modalities, three sources, all free and keyless so that any Claude Code user can reproduce a run end to end. The full retrieval-stack survey behind this subset is documented separately (a catalogue of ~95 sources across eight clusters); the rest of that stack is designed-but-not-yet-shipped and is added in later versions. The `select` leaf reaches for nothing outside this file.

Every source here is **open** (no key, no signup) and **reproducible** (a stranger re-running the brief reaches the same source the same way). There are no paid or gated sources in v1, so a v1 run is always labelled `reproducible` unless a source is unreachable at run time.

## Web

**Source:** the engine's built-in `WebSearch` and `WebFetch` tools.

| Field | Value |
|---|---|
| Access tier | open (built into Claude Code; no key, no setup) |
| Reproducible | yes |
| Modality | open-web search and page read |

**Select it when** the claim type is `factual`, `competitive`, or `technical` and the answer lives on the open web: vendor pages, product docs, news, blog posts, pricing pages, comparison write-ups. It is the default modality: if no specialised source fits a sub-question, the web is the fallback.

**How to query it.** Two built-in tools, no endpoint:
- `WebSearch` with a natural-language query returns a ranked result list (titles + URLs + snippets). Use it to discover candidate pages.
- `WebFetch` with a result URL returns the page content as text. Use it to read the page the search surfaced.

The `retrieve` leaf records the search query, the chosen result URL, and the retrieved-at timestamp so the path from query to source is inspectable.

## Academic

**Source:** OpenAlex, the open scholarly graph (works, authors, venues, citations across every field).

| Field | Value |
|---|---|
| Access tier | open (keyless; no signup required) |
| Reproducible | yes |
| Base API URL | `https://api.openalex.org` |
| Modality | scholarly works, citation metadata, bibliometrics |

**Select it when** the claim type is `factual` or `technical` and the question is about *research*: what the literature says, who published a finding, how cited a paper is, when work first appeared. Prefer it over an open-web search whenever the sub-question asks for a peer-reviewed or preprint basis rather than a vendor's own claim.

**How to query it.** Fetch the public REST API directly (via `WebFetch` or any HTTP fetch). The works endpoint takes a free-text search and returns structured JSON:

```
https://api.openalex.org/works?search=retrieval%20augmented%20generation&per-page=5
```

Each result carries `title`, `publication_year`, `doi`, `cited_by_count`, and authorship, enough to cite the primary work without scraping a publisher page. Append `&mailto=you@example.com` to use the faster "polite pool"; it is optional and changes no results.

## Structured / reference

**Source:** World Bank Open Data, official cross-country development indicators (GDP, population, inflation, and ~16k other series).

| Field | Value |
|---|---|
| Access tier | open (keyless; no signup required) |
| Reproducible | yes |
| Base API URL | `https://api.worldbank.org/v2` |
| Modality | structured statistics, country-by-indicator time series |

**Select it when** the claim type is `quantitative` and the value is an official country-level statistic (economic, demographic, or development data) where the primary owner is authoritative and an open-web number would be a derivative. Prefer it over a web search for any "country X's GDP / population / inflation" style figure.

**How to query it.** Fetch the public REST API directly. The pattern is `/country/{ISO3}/indicator/{INDICATOR}?format=json`:

```
https://api.worldbank.org/v2/country/VN/indicator/NY.GDP.MKTP.CD?format=json&per_page=5
```

This returns Vietnam's GDP (current US$) time series as JSON: each entry carries the indicator code, country, year, and value. Indicator codes are stable (e.g. `SP.POP.TOTL` for total population, `FP.CPI.TOTL.ZG` for inflation), so the query is exactly reproducible.

## Note on scope

This is the lean v1 set: one web modality plus one academic and one structured source, chosen because all three are keyless and re-runnable by anyone. More modalities and sources (financial filings, code/dependency data, news/real-time signal, vertical sources, and the paid `checkable` reserve) are designed and catalogued but not shipped in this version; the `select` leaf must not invent or reach for them. When it does add them, each gains a row here first.
