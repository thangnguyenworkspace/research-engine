# SRC-01 — OpenAlex

**Sub-question:** SQ-03 — What does the research literature report about the reliability (word error rate / accuracy) of automatic speech recognition / transcription systems?
**Source:** OpenAlex
**URL:** https://api.openalex.org/works?search=automatic%20speech%20recognition%20word%20error%20rate&per-page=5&mailto=research-engine@example.com
**Access tier:** open
**Retrieved-at:** 2026-06-25T14:00:00Z

## Material

The free-text search returned 5 works ranked by OpenAlex relevance, but the ranking was NOISY — three of the five are off-topic high-citation works that match on a token rather than on ASR/WER subject matter. Recording all five honestly with that caveat:

1. **Gradient-based learning applied to document recognition** — Yann LeCun — 1998 — DOI 10.1109/5.726791 — cited_by_count 58,200. OFF-TOPIC (CNN/document image recognition; matched on "recognition"). No WER content.
2. **Enriching Word Vectors with Subword Information** — Piotr Bojanowski — 2017 — DOI 10.1162/tacl_a_00051 — cited_by_count 9,783. OFF-TOPIC (word embeddings; matched on "word"). No WER content.
3. **A post-processing system to yield reduced word error rates: Recognizer Output Voting Error Reduction (ROVER)** — J. Fiscus — 2002 (record), original ASRU 1997 — DOI 10.1109/asru.1997.659110 — cited_by_count 1,099. ON-TOPIC. Title explicitly addresses reducing ASR word error rates via system-output voting; specific WER figures not present in the returned abstract index.
4. **Understanding face recognition** — Vicki Bruce — 1986 — DOI 10.1111/j.2044-8295.1986.tb02199.x — cited_by_count 3,953. OFF-TOPIC (facial-recognition psychology). No WER content.
5. **Dialogue Act Modeling for Automatic Tagging and Recognition of Conversational Speech** — Andreas Stolcke — 2000 — DOI 10.1162/089120100561737 — cited_by_count 1,113. PARTIALLY ON-TOPIC (conversational-speech modelling/recognition); no specific WER figure in the returned abstract index.

Honest assessment: this OpenAlex query established that ASR word-error-rate IS an established, citable research area (ROVER is a primary, well-cited methods work on reducing WER), but the keyless free-text endpoint did NOT return a clean, quantitative WER benchmark figure. No specific WER percentage was retrieved. A downstream claim can assert the *existence and citability* of WER-reduction research, but cannot state a numeric accuracy figure from this material without overreaching.
