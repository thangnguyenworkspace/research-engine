# Synthesis draft

Working synthesis for run 20260625-135009-ai-notetaker-sea-gtm. Every claim is atomic and traces to retrieved material by its `[SQ-NN/SRC-NN]` id. No claim is made beyond what was retrieved; gaps are recorded as gaps. This draft is for the independent verifier to contest — claims are stated as the evidence presents them, not pre-defended.

## SQ-01 — Leading vendors and positioning

- **CLM-01** — A 2025 multi-vendor round-up names a wide AI meeting/notetaker field: Otter, Fireflies, Fathom, tl;dv, Granola, Fellow, Avoma, Gong, Grain and Read.ai. [SQ-01/SRC-02]
- **CLM-02** — Gong's own home page positions it as the "#1 AI OS for Revenue Teams" / "Revenue AI" for sales, CS, enablement and RevOps, and uses the term "Revenue Graph" — described as "a living network of your revenue data that automatically captures and connects every interaction across your business"; third-party round-ups describe the same product as a conversation-/deal-intelligence platform for sales and revenue teams. [SQ-01/SRC-02]
- **CLM-03** — Fireflies positions itself toward sales and customer-success teams using CRM workflows, with its headline capability being CRM integration (Salesforce, HubSpot, Asana) and automatic task creation. [SQ-01/SRC-01]
- **CLM-04** — Fathom positions itself for small, remote, budget-conscious Zoom-first teams, with a free, lightweight offering as its headline. [SQ-01/SRC-01]
- **CLM-05** — Otter is described as the category pioneer offering broad cross-platform capture (Zoom, Google Meet, Teams, in-person), with a marketed transcription accuracy of up to 95%. [SQ-01/SRC-01]
- **CLM-06** — A federal class-action lawsuit, *Brewer v. Otter.ai*, was filed in August 2025 in federal court in California, alleging Otter's tool joins meetings, records participants (including non-accountholders) without consent, and uses the recordings to train its ASR/ML models. [SQ-01/SRC-03]
- **CLM-07** — The competitive set is segmented by use case rather than uniform: revenue/deal-intelligence for sales and revenue teams (Gong), CRM-automation for sales teams (Fireflies), and budget/individual capture (Fathom). [SQ-01/SRC-02, SQ-01/SRC-01]

> Trust note: SQ-01 material mixes vendor-primary positioning (Gong's own home page for CLM-02; the "Revenue Graph" term) with corroborating third-party round-up content (CLM-01, CLM-03–05, CLM-07). Vendor-specific accuracy/feature claims (e.g. Otter's 95%) originate from vendor marketing as relayed by third parties, not independently measured here. CLM-06's lawsuit facts come from a directly-fetched National Law Review article (corroborated by NPR coverage of the same filing); the cycle-1 "fallen behind in features" framing is retired — no fetched source states it.

## SQ-02 — Pricing and SMB entry point

- **CLM-08** — Fireflies' own pricing page (accessed 2026-06-25) lists four tiers: Free ($0), Pro ($10/seat/month billed annually), Business ($19/seat/month annually), and Enterprise ($39/seat/month, annual only). [SQ-02/SRC-01]
- **CLM-09** — Fireflies' Free tier includes unlimited transcription, unlimited AI summaries, 400 minutes of team storage and 20 AI credits. [SQ-02/SRC-01]
- **CLM-10** — Otter's own pricing page (accessed 2026-06-25) lists: Basic (free, 300 monthly transcription minutes), Pro ($8.33/user/month annual; $16.99 monthly), Business ($19.99/user/month annual; $30 monthly), and Enterprise (custom quote). [SQ-02/SRC-02]
- **CLM-11** — Fathom's own pricing page (accessed 2026-06-25) lists: Free ($0, unlimited recordings/transcriptions), Premium ($16/user/month annual; $20 monthly), Team ($15/user/month annual; $19 monthly, min 2 users), and Business ($25/user/month annual; $34 monthly, min 2 users). [SQ-02/SRC-03]
- **CLM-12** — The entry paid price point for an SMB-sized team clusters in the high-single-digit-to-mid-teens per seat/month on annual billing: Fireflies Pro $10 and Otter Pro $8.33, with Fathom's lowest paid tier (Premium) at $16. [SQ-02/SRC-01, SQ-02/SRC-02, SQ-02/SRC-03]
- **CLM-13** — Multiple leading vendors offer a functional free tier (Fireflies, Otter, Fathom), so the practical floor for adoption is $0 with feature/usage caps. [SQ-02/SRC-01, SQ-02/SRC-02, SQ-02/SRC-03]

> Trust note: all three vendors' figures are now vendor-primary (each vendor's own pricing page — Fireflies SRC-01, Otter SRC-02, Fathom SRC-03). Cycle-1's derivative round-up figures (Otter Pro $10 / Enterprise $39; Fathom Premium ~$15) were corrected against the vendor pages: Otter Pro is $8.33 annual and Enterprise is a custom quote, and Fathom's lowest paid tier is $16 annual. List prices change frequently — figures are accurate-as-of 2026-06-25.

## SQ-03 — Transcription (ASR) reliability in the research literature

- **CLM-14** — Reducing automatic-speech-recognition word error rate (WER) is an established, citable research area; the ROVER method (Fiscus), a system-output voting technique for reducing ASR WER, has ~1,099 citations in OpenAlex. [SQ-03/SRC-01]
- **CLM-15** — The keyless OpenAlex free-text search for "automatic speech recognition word error rate" did NOT return a clean quantitative WER benchmark figure; three of its five top results were off-topic high-citation works, so no specific transcription-accuracy percentage was retrieved from this source. [SQ-03/SRC-01]

> Gap note: SQ-03 establishes that WER/ASR-accuracy is a real, measurable research field but the free stack did not yield a numeric accuracy figure to cite. Any specific "X% accuracy" claim is unsupported by retrieved evidence.

## SQ-04 — Summarization reliability and failure modes in the research literature

- **CLM-16** — Multiple peer-reviewed/preprint works converge on a documented failure mode: abstractive (neural) summarization systems frequently produce factual inconsistencies relative to their source input. [SQ-04/SRC-01]
- **CLM-17** — Wang et al. (2020, QAGS, ~321 citations) report that standard automatic summarization metrics are "largely insensitive" to factual errors in generated summaries. [SQ-04/SRC-01]
- **CLM-18** — Entity-level factual consistency (e.g. hallucinated or incorrect named entities) is studied as a specific summarization failure mode (Nan, 2021, ~111 citations). [SQ-04/SRC-01]
- **CLM-19** — Researchers describe ensuring factual consistency in abstractive summarization as an unsolved challenge requiring dedicated techniques (e.g. post-hoc factual error correction; Cao, 2020). [SQ-04/SRC-01]
- **CLM-20** — The retrieved summarization-reliability works date from 2020–2021 and therefore document the failure-mode class, not the accuracy of current frontier LLMs; no single quantitative reliability rate was retrieved. [SQ-04/SRC-01]

## SQ-05 — Business base in Vietnam and Indonesia

- **CLM-21** — World Bank indicator IC.BUS.NREG records 122,487 new businesses registered in Vietnam in 2022, the most recent non-null year (2023–2024 are null). Data-currency caveat: Vietnam's latest year (2022) is six years more recent than Indonesia's latest (2016, CLM-23), so the two countries' figures are NOT comparable like-for-like. [SQ-05/SRC-01]
- **CLM-22** — Vietnam's new-business-registration count rose broadly from 73,817 (2015) to 122,487 (2022) on this indicator. [SQ-05/SRC-01]
- **CLM-23** — For Indonesia, World Bank indicator IC.BUS.NREG has no data for any year 2017–2024; its most recent non-null value is 58,426 new businesses registered in 2016. Data-currency caveat: this 2016 figure is six years staler than Vietnam's 2022 figure (CLM-21), so the headline gap (122,487 vs 58,426) must NOT be read as a current, like-for-like difference in business formation. [SQ-05/SRC-02]
- **CLM-24** — IC.BUS.NREG measures the annual flow of newly registered firms, not the total stock of SMBs, so it is a proxy for formal-business creation rather than a count of the addressable SMB base. [SQ-05/SRC-01, SQ-05/SRC-02]
- **CLM-25** — A like-for-like cross-country comparison of the addressable business base is not possible from this indicator because Vietnam's latest figure is 2022 while Indonesia's is 2016. [SQ-05/SRC-01, SQ-05/SRC-02]

> Gap note: the free stack gives only a stale registration-FLOW proxy (badly stale for Indonesia), not a current SMB stock count. SQ-05 is partially answered.

## SQ-06 — Macroeconomic context for Vietnam and Indonesia

- **CLM-26** — Vietnam's GDP (current US$) was approximately $476.4 billion in 2024, the most recent reported year (World Bank, NY.GDP.MKTP.CD). [SQ-06/SRC-01]
- **CLM-27** — Vietnam's total population was approximately 101.0 million in 2024 (World Bank, SP.POP.TOTL). [SQ-06/SRC-01]
- **CLM-28** — Indonesia's GDP (current US$) was approximately $1.40 trillion in 2024, the most recent reported year (World Bank, NY.GDP.MKTP.CD). [SQ-06/SRC-02]
- **CLM-29** — Indonesia's total population was approximately 283.5 million in 2024 (World Bank, SP.POP.TOTL). [SQ-06/SRC-02]
- **CLM-30** — On 2024 figures, Indonesia's economy is roughly 2.9x Vietnam's GDP and its population roughly 2.8x Vietnam's, making Indonesia the larger of the two focus markets by raw scale. [SQ-06/SRC-01, SQ-06/SRC-02]

## SQ-07 — Market size for SMB sales-call AI notetakers in Southeast Asia

- **CLM-31** — No published market-size figure scoped to the specific category requested (SMB sales-call AI notetaker, Southeast Asia) was retrievable from the v1 free stack; SQ-07 is recorded as UNANSWERED for its specific ask. [SQ-07/SRC-01]
- **CLM-32** — For the BROADER "AI meeting assistants" category, one market-research source (Market Research Future) reports a global market of ~$3.5 billion in 2025, forecast to ~$34.28 billion by 2035, at a 25.62% CAGR. [SQ-07/SRC-01]
- **CLM-33** — That same source attributes ~20% of the global AI-meeting-assistants market to Asia-Pacific as a whole, with no Southeast Asia, SMB, or sales-call-notetaker sub-breakdown. [SQ-07/SRC-01]
- **CLM-34** — RETIRED. Cycle-1 carried a ~US$12.03B "Southeast Asia AI market, 2025" figure attributed to Statista via search digest. On re-research the Statista SEA-AI outlook page was fetched directly and its figures are paywalled (rendered as "US$*****bn"); the $12.03B value exists only in search-result snippets, not on any openly-fetchable page. Statista is therefore a GATED source incompatible with this run's `reproducible` label, and the figure is dropped — not retained as "context." Separately, it would be scope-incommensurable anyway: a whole-economy SEA AI figure cannot be compared with a global meeting-assistants category figure (CLM-32) or used to size the requested SMB-sales-notetaker slice. No figure is substituted. [SQ-07/SRC-02]

> Gap note: CLM-32/CLM-33 are broad-global-category context, explicitly NOT the requested slice and not to be combined with any regional whole-AI figure. CLM-34's SEA-AI figure is retired (gated source + scope-incommensurable). The brief's market-size ask (SMB sales-call AI notetaker, Southeast Asia) stays UNANSWERED (CLM-31): a defensible scoped TAM would require paid analyst reports or a bottom-up build not performed in this run. No figure was fabricated.

## Tensions

- **Tension 1 — CLM-21 (Vietnam 2022) vs CLM-23 (Indonesia 2016): RESOLVED via data-currency caveat.** The two countries' most-recent business-registration figures come from different years (Vietnam 2022, Indonesia 2016) and cannot be compared like-for-like; the apparent gap (122,487 vs 58,426) partly reflects a six-year data-currency difference, not purely a real difference in business formation. The caveat is now stated explicitly inside both affected claims (CLM-21, CLM-23) and in CLM-25, so the non-comparable years are never presented as comparable.
- **Tension 2 — CLM-32 (~$3.5B global meeting-assistants, 2025) vs the former CLM-34 (~$12.03B SEA whole-AI, 2025): RESOLVED via retirement.** These measured incommensurable scopes (a narrow product category globally vs all AI in one region) and must never be combined or compared. The SEA-AI figure (CLM-34) is now retired entirely — both because its only source (Statista) is paywalled/gated and unfetchable on the open web (incompatible with this run's `reproducible` label), and because it is scope-incommensurable. CLM-32/CLM-33 remain only as explicitly-labelled broad-global-category context. The market-size ask itself stays honestly UNANSWERED (CLM-31); no scope-mismatched figure is carried forward as a stand-in.
