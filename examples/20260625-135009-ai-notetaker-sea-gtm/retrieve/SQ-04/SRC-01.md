# SRC-01 — OpenAlex

**Sub-question:** SQ-04 — What does the research literature report about the reliability and known failure modes of automatic (LLM/abstractive) meeting or conversation summarization?
**Source:** OpenAlex
**URL:** https://api.openalex.org/works?search=abstractive%20meeting%20summarization%20factual%20consistency&per-page=5&mailto=research-engine@example.com
**Access tier:** open
**Retrieved-at:** 2026-06-25T14:00:00Z

## Material

The search returned 5 on-topic works on the factual-consistency / reliability of abstractive summarization (a clean, relevant result set):

1. **Enhancing Factual Consistency of Abstractive Summarization** — Chenguang Zhu — 2021 — DOI 10.18653/v1/2021.naacl-main.58 — cited_by_count 123. States abstractive summarization systems have "frequent factual inconsistencies with respect to their input," limiting practical deployment.
2. **Asking and Answering Questions to Evaluate the Factual Consistency of Summaries** — Alex Wang — 2020 — DOI 10.18653/v1/2020.acl-main.450 — cited_by_count 321. Proposes the QAGS evaluation protocol; observes existing automatic metrics are "largely insensitive" to factual errors in generated summaries.
3. **Entity-level Factual Consistency of Abstractive Text Summarization** — Nan Feng — 2021 — DOI 10.18653/v1/2021.eacl-main.235 — cited_by_count 111. Studies entity-level factual consistency (e.g. hallucinated/incorrect named entities).
4. **Factual Error Correction for Abstractive Summarization Models** — Meng Cao — 2020 — DOI 10.18653/v1/2020.emnlp-main.506 — cited_by_count 124. Post-editing error correction; emphasises that ensuring factual consistency "remains a challenge" for neural systems.
5. **Evaluating the Factual Consistency of Abstractive Text Summarization** — Wojciech Kryściński — 2020 — DOI 10.18653/v1/2020.emnlp-main.750 — cited_by_count 67. Evaluation of factual consistency in abstractive summaries.

Honest assessment: clean retrieval. Multiple independent, peer-reviewed/preprint works converge on a documented failure mode — abstractive (neural/LLM) summarization frequently produces factual inconsistencies / hallucinations relative to the source, and standard summarization metrics are insensitive to these errors. This is a corroborated qualitative finding. No single quantitative reliability rate was returned (the works propose evaluation methods rather than reporting one universal accuracy number); a downstream claim should stay qualitative (failure mode exists and is well-documented) rather than asserting a specific error percentage. Note these are 2020–2021 works (pre-dating the latest LLMs), so they document the failure-mode *class*, not the current frontier-model rate.
