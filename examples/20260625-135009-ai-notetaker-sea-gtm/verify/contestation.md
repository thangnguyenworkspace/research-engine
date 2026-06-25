# Contestation (cycle 2 — final)

Independent adversarial re-verification of the load-bearing claims in `consolidate/synthesis.draft.md` after the cycle-2 targeted re-research. The verifier did not author or remediate these claims. Every verdict is graded against evidence the verifier fetched itself this cycle — World Bank and OpenAlex endpoints, web pages re-fetched via `WebFetch`. The author's `retrieve/` files were used only to recover each claim's cited target (which URL/endpoint), never as ground truth.

Cycle 1 found one refusal (CLM-02, Gong cited to a page that never mentions Gong) and a cluster of partials caused by one systemic flaw: SQ-01 and SQ-07 claims cited a single fetched page (`SRC-01`) but actually rested on the author's un-fetched "WebSearch digest." Cycle 2 re-grounded those claims to pages that actually carry the material (new `SRC-02`/`SRC-03` rows under SQ-01 and SQ-02), corrected stale derivative pricing against vendor-primary pages, and retired the paywalled Statista figure (CLM-34). This contestation re-fetches each remediated source independently and re-grades it. The structured spine (World Bank CLM-21–30, OpenAlex CLM-14–20) was already `supported` in cycle 1 against re-queried endpoints and was not changed in cycle 2; those verdicts are carried forward without re-fetch, as noted per block.

## CLM-01 — A 2025 multi-vendor round-up names a wide AI meeting/notetaker field: Otter, Fireflies, Fathom, tl;dv, Granola, Fellow, Avoma, Gong, Grain and Read.ai.

- **Challenge:** CHL-01
- **Cited source(s):** SQ-01/SRC-02 (https://otter.ai/blog/best-ai-meeting-notetakers-and-assistants-in-2025)
- **Independent check (re-verified cycle 2):** WebFetched the otter.ai round-up directly. It names all ten vendors literally: Otter, Fireflies.ai, Fathom, tl;dv, Granola, Fellow, Avoma, Gong, Grain, Read.ai. The wider list (Gong, Avoma, Grain, Granola, Read.ai) that cycle-1's index.dev page lacked is present on this newly-cited page.
- **Verdict:** supported
- **Reason:** The now-cited round-up page literally names every vendor in the claim; the cycle-1 citation–evidence mismatch is cured.

## CLM-02 — Gong's own home page positions it as the "#1 AI OS for Revenue Teams" / "Revenue AI" for sales, CS, enablement and RevOps, uses the term "Revenue Graph" — "a living network of your revenue data that automatically captures and connects every interaction across your business"; third-party round-ups describe the same product as a conversation-/deal-intelligence platform.

- **Challenge:** CHL-02
- **Cited source(s):** SQ-01/SRC-02 (https://www.gong.io/ — vendor-primary)
- **Independent check (re-verified cycle 2):** WebFetched gong.io directly. The page literally carries "#1 AI OS for Revenue Teams", "Revenue AI Built To Close deals faster", and "Gong Revenue Graph: A living network of your revenue data that automatically captures and connects every interaction across your business." Target audiences named on the page: sales, customer success, enablement, RevOps (plus CROs/leadership). The otter.ai round-up (CLM-01 source) separately positions Gong for "sales organizations and revenue teams that need deal intelligence, forecasting, and coaching."
- **Verdict:** supported
- **Reason:** Vendor-primary page carries the positioning and the "Revenue Graph" definition verbatim; the deal-/conversation-intelligence framing is corroborated on the cited round-up. Cycle-1 refusal cleared.

## CLM-03 — Fireflies positions toward sales/CS teams using CRM workflows; headline capability is CRM integration (Salesforce, HubSpot, Asana) and automatic task creation.

- **Challenge:** CHL-03
- **Cited source(s):** SQ-01/SRC-01 (index.dev comparison article)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 WebFetch of index.dev confirmed CRM-driven positioning, Salesforce/HubSpot/Asana, automatic task creation from recaps. (My cycle-2 re-fetch of index.dev for CLM-07 re-confirmed the Salesforce/HubSpot/Asana + "produced tasks directly from the meeting recap" content incidentally.)
- **Verdict:** supported
- **Reason:** Cited page directly states the CRM-integration positioning, the named CRMs, and automatic task creation.

## CLM-04 — Fathom positions for small, remote, budget-conscious Zoom-first teams, with a free, lightweight offering as its headline.

- **Challenge:** CHL-04
- **Cited source(s):** SQ-01/SRC-01 (index.dev comparison article)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 WebFetch confirmed "absolutely free", "Zoom-first", "go-to for basic, no-fuss Zoom summaries", small/low-budget teams. (Re-confirmed incidentally on my cycle-2 index.dev re-fetch.)
- **Verdict:** supported
- **Reason:** Cited page directly supports the budget / Zoom-first / free-and-lightweight positioning.

## CLM-05 — Otter is the category pioneer with broad cross-platform capture and a marketed transcription accuracy of up to 95%.

- **Challenge:** CHL-05
- **Cited source(s):** SQ-01/SRC-01 (index.dev comparison article)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 WebFetch confirmed the marketed "95%" figure and broad-capture/accuracy framing on the cited page.
- **Verdict:** supported
- **Reason:** The cited page carries the marketed 95% accuracy figure and the broad-capture positioning (marketing-relayed, as the draft flags).

## CLM-06 — A federal class-action lawsuit, *Brewer v. Otter.ai*, was filed in August 2025 in federal court in California, alleging Otter's tool joins meetings, records participants (including non-accountholders) without consent, and uses the recordings to train its ASR/ML models.

- **Challenge:** CHL-06
- **Cited source(s):** SQ-01/SRC-03 (https://natlawreview.com/article/ai-notetaking-tools-under-fire-lessons-otterai-class-action-complaint)
- **Independent check (re-verified cycle 2):** WebFetched the National Law Review article directly. It states the case name *Brewer v. Otter.ai*, filing in August 2025, "federal court in California" with **no specific district named**, a lead plaintiff who is "not an Otter accountholder", and the three core allegations verbatim: Otter "Joins Zoom, Google Meet, and Microsoft Teams meetings as a participant and transmits conversations to Otter in real time", "Records meeting participants' conversations even if they are not Otter accountholders", and "Uses those recordings to train Otter's automatic speech recognition (ASR) and machine learning models." The cycle-1 "fallen behind in features" framing is absent from the draft now.
- **Verdict:** supported
- **Reason:** The cited source directly carries every lawsuit fact as stated, and the draft correctly says "federal court in California" rather than over-specifying the district — the article does not name one. Citation–evidence mismatch from cycle 1 is cured; over-claim avoided.

## CLM-07 — The competitive set is segmented by use case: revenue/deal-intelligence (Gong), CRM-automation (Fireflies), budget/individual capture (Fathom).

- **Challenge:** CHL-07
- **Cited source(s):** SQ-01/SRC-02 (otter.ai round-up), SQ-01/SRC-01 (index.dev comparison)
- **Independent check (re-verified cycle 2):** The Gong leg is now grounded on the otter.ai round-up I fetched, which positions Gong for "sales organizations and revenue teams that need deal intelligence, forecasting, and coaching." The Fireflies and Fathom legs are on index.dev, which I re-fetched: Fireflies "designed for CRM-heavy workflows … Salesforce, HubSpot, Pipedrive … produced tasks directly from the meeting recap", and Fathom "absolutely free … go-to for basic, no-fuss Zoom summaries … Ideal for remote engineers and small teams working on a low budget." All three legs are now carried by a cited, fetched source.
- **Verdict:** supported
- **Reason:** Each of the three segmentation legs is supported by one of the two cited sources; the missing-Gong-leg gap from cycle 1 is filled by the new SRC-02 citation.

## CLM-08 — Fireflies' pricing page lists four tiers: Free $0, Pro $10, Business $19, Enterprise $39 (annual-only).

- **Challenge:** CHL-08
- **Cited source(s):** SQ-02/SRC-01 (https://fireflies.ai/pricing — vendor-primary)
- **Independent check (re-verified cycle 2):** WebFetched fireflies.ai/pricing directly. Free $0; Pro $10/seat/mo annual ($18 monthly); Business $19/seat/mo annual ($29 monthly, "MOST POPULAR"); Enterprise $39/seat/mo "ANNUAL ONLY." Exact match.
- **Verdict:** supported
- **Reason:** Vendor-primary page states all four tiers and prices exactly as claimed (re-confirmed this cycle).

## CLM-09 — Fireflies' Free tier includes unlimited transcription, unlimited AI summaries, 400 minutes of team storage and 20 AI credits.

- **Challenge:** CHL-09
- **Cited source(s):** SQ-02/SRC-01 (fireflies.ai/pricing)
- **Independent check (re-verified cycle 2):** WebFetched the page. Free tier lists "Unlimited transcription," "Unlimited AI summaries," "400 mins of storage/team," "20 AI credits." Exact match.
- **Verdict:** supported
- **Reason:** Every Free-tier feature matches the vendor-primary page (re-confirmed this cycle).

## CLM-10 — Otter's own pricing page lists Basic (free, 300 monthly transcription minutes), Pro ($8.33/user/mo annual; $16.99 monthly), Business ($19.99/user/mo annual; $30 monthly), Enterprise (custom quote).

- **Challenge:** CHL-10
- **Cited source(s):** SQ-02/SRC-02 (https://otter.ai/pricing — vendor-primary)
- **Independent check (re-verified cycle 2):** WebFetched otter.ai/pricing directly. Basic free, "300 monthly transcription minutes"; Pro $8.33/user/mo annual (save 51%) / $16.99 monthly; Business $19.99/user/mo annual (save 33%) / $30 monthly; Enterprise custom quote ("Schedule a demo"). Exact match — and the cycle-1 derivative figures (Pro $10 / Enterprise $39) are correctly retired.
- **Verdict:** supported
- **Reason:** Now grounded to Otter's own pricing page, which carries every figure exactly; the stale digest numbers were corrected. Cycle-1 partial cleared.

## CLM-11 — Fathom's own pricing page lists Free ($0, unlimited recordings/transcriptions), Premium ($16/user/mo annual; $20 monthly), Team ($15/user/mo annual; $19 monthly, min 2 users), Business ($25/user/mo annual; $34 monthly, min 2 users).

- **Challenge:** CHL-11
- **Cited source(s):** SQ-02/SRC-03 (https://fathom.ai/pricing — vendor-primary)
- **Independent check (re-verified cycle 2):** WebFetched fathom.ai/pricing directly. Free $0, "Unlimited recordings + transcriptions"; Premium $16/user annual / $20 monthly; Team $15/user annual / $19 monthly, min 2 users; Business $25/user annual / $34 monthly, min 2 users. Exact match — the cycle-1 ~$15/$19 derivative figures and the bogus "Team Edition Pro" tier are corrected.
- **Verdict:** supported
- **Reason:** Now grounded to Fathom's own pricing page, which carries every figure and the min-2-users conditions exactly. Cycle-1 partial cleared.

## CLM-12 — Entry paid price clusters high-single-digit-to-mid-teens per seat/month annual: Fireflies Pro $10, Otter Pro $8.33, Fathom Premium $16.

- **Challenge:** CHL-12
- **Cited source(s):** SQ-02/SRC-01, SQ-02/SRC-02, SQ-02/SRC-03 (all three vendor-primary pricing pages)
- **Independent check (re-verified cycle 2):** Each of the three legs is now independently confirmed against the vendor's own page this cycle: Fireflies Pro $10 (CLM-08), Otter Pro $8.33 (CLM-10), Fathom Premium $16 (CLM-11). The "high-single-digit-to-mid-teens" characterization is accurate for $8.33–$16.
- **Verdict:** supported
- **Reason:** All three anchor figures are now vendor-primary and verified; the synthesis no longer rests on unfetched derivative numbers. Cycle-1 partial cleared.

## CLM-13 — Multiple leading vendors (Fireflies, Otter, Fathom) offer a functional free tier, so the practical adoption floor is $0 with caps.

- **Challenge:** CHL-13
- **Cited source(s):** SQ-02/SRC-01, SQ-02/SRC-02, SQ-02/SRC-03
- **Independent check (re-verified cycle 2):** All three free tiers are now confirmed on vendor-primary pages I fetched this cycle: Fireflies Free $0, Otter Basic free (300 min/mo cap), Fathom Free $0 (unlimited recordings/transcriptions). All three legs grounded, not just two.
- **Verdict:** supported
- **Reason:** Every free-tier leg is independently verified on a vendor page; the $0-floor-with-caps conclusion holds. (Was already supported in cycle 1; now fully grounded.)

## CLM-14 — Reducing ASR WER is an established research area; ROVER (Fiscus) has ~1,099 citations in OpenAlex.

- **Challenge:** CHL-14
- **Cited source(s):** SQ-03/SRC-01 (OpenAlex works search)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query returned ROVER with cited_by_count = 1099, DOI 10.1109/asru.1997.659110. Not re-fetched this cycle (unchanged by cycle-2 remediation).
- **Verdict:** supported
- **Reason:** Endpoint returned the exact paper and the exact 1,099 citation count.

## CLM-15 — The OpenAlex free-text search did NOT return a clean quantitative WER benchmark; three of five top results were off-topic high-citation works.

- **Challenge:** CHL-15
- **Cited source(s):** SQ-03/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query reproduced the identical noisy result set (LeCun 1998, Bojanowski 2017, ROVER, Bruce 1986, Stolcke 2000).
- **Verdict:** supported
- **Reason:** The negative/limitation claim about the retrieval reproduced exactly.

## CLM-16 — Peer-reviewed/preprint works converge that abstractive summarization frequently produces factual inconsistencies relative to source input.

- **Challenge:** CHL-16
- **Cited source(s):** SQ-04/SRC-01 (OpenAlex)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query returned on-topic factual-consistency works; QAGS abstract verbatim confirmed the failure mode.
- **Verdict:** supported
- **Reason:** Multiple re-fetched works and a verbatim abstract converge on the stated failure mode.

## CLM-17 — Wang et al. (2020, QAGS, ~321 citations) report standard summarization metrics are "largely insensitive" to factual errors.

- **Challenge:** CHL-17
- **Cited source(s):** SQ-04/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 fetch of the QAGS record (DOI 10.18653/v1/2020.acl-main.450): cited_by_count = 321; "largely insensitive" wording verbatim.
- **Verdict:** supported
- **Reason:** Author, count, and exact wording confirmed against the primary record.

## CLM-18 — Entity-level factual consistency is studied as a specific failure mode (Nan, 2021, ~111 citations).

- **Challenge:** CHL-18
- **Cited source(s):** SQ-04/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 fetch (DOI 10.18653/v1/2021.eacl-main.235): title, year, cited_by_count = 111 confirmed.
- **Verdict:** supported
- **Reason:** Exact title, year and citation count confirmed; attribution matches (name-order artifact only).

## CLM-19 — Researchers describe ensuring factual consistency as an unsolved challenge requiring dedicated techniques (e.g. post-hoc factual error correction; Cao, 2020).

- **Challenge:** CHL-19
- **Cited source(s):** SQ-04/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 fetch (DOI 10.18653/v1/2020.emnlp-main.506): "Factual Error Correction for Abstractive Summarization Models," 2020, Meng Cao.
- **Verdict:** supported
- **Reason:** Cao 2020 confirmed by title, year and author; supports the dedicated-technique claim.

## CLM-20 — The retrieved summarization works date from 2020–2021, documenting the failure-mode class, not current frontier-LLM accuracy; no quantitative reliability rate was retrieved.

- **Challenge:** CHL-20
- **Cited source(s):** SQ-04/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-fetch confirmed all five works are 2020–2021 with no universal accuracy rate.
- **Verdict:** supported
- **Reason:** The dating and the "no single quantitative rate" limitation are accurate against the re-queried set.

## CLM-21 — World Bank IC.BUS.NREG records 122,487 new businesses registered in Vietnam in 2022, the most recent non-null year (2023–2024 null). Data-currency caveat: Vietnam's 2022 figure is six years more recent than Indonesia's 2016 (CLM-23) — not comparable like-for-like.

- **Challenge:** CHL-21
- **Cited source(s):** SQ-05/SRC-01 (World Bank IC.BUS.NREG, VNM)
- **Independent check:** Carried from cycle 1 — figure unchanged (2024 null, 2023 null, 2022 = 122487, re-queried exactly in cycle 1). Cycle 2 added the data-currency caveat, which is factually correct: VN latest is 2022, IDN latest is 2016 (CLM-23), a six-year gap. The caveat is now stated inside the claim.
- **Verdict:** supported
- **Reason:** Endpoint figure verified in cycle 1; the cycle-2 caveat is accurate and resolves Tension 1 at the claim level.

## CLM-22 — Vietnam's new-business registration rose broadly from 73,817 (2015) to 122,487 (2022).

- **Challenge:** CHL-22
- **Cited source(s):** SQ-05/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query: 2015 = 73817, 2022 = 122487, intervening dip 2021 = 94243.
- **Verdict:** supported
- **Reason:** Both range endpoints and the qualified "broadly" match the series.

## CLM-23 — For Indonesia, IC.BUS.NREG has no data 2017–2024; most recent non-null value is 58,426 in 2016. Data-currency caveat: this 2016 figure is six years staler than Vietnam's 2022 (CLM-21) — the headline gap must not be read as a current like-for-like difference.

- **Challenge:** CHL-23
- **Cited source(s):** SQ-05/SRC-02 (World Bank IC.BUS.NREG, IDN)
- **Independent check:** Carried from cycle 1 — figure unchanged (2017–2024 null; 2016 = 58426, re-queried exactly in cycle 1). Cycle 2 added the data-currency caveat, which is accurate.
- **Verdict:** supported
- **Reason:** Endpoint figure verified in cycle 1; the cycle-2 caveat correctly prevents the stale 2016 figure from being read against VN 2022. Tension 1 resolved at the claim level.

## CLM-24 — IC.BUS.NREG measures the annual flow of newly registered firms, not the stock of SMBs, so it is a proxy for formal-business creation rather than the addressable SMB base.

- **Challenge:** CHL-24
- **Cited source(s):** SQ-05/SRC-01, SQ-05/SRC-02
- **Independent check:** Carried from cycle 1 — unchanged. The indicator name "New businesses registered (number)" is a yearly flow by definition.
- **Verdict:** supported
- **Reason:** The indicator's own name confirms it is a registration flow; the proxy caveat is methodologically correct.

## CLM-25 — A like-for-like cross-country comparison is not possible because Vietnam's latest figure is 2022 while Indonesia's is 2016.

- **Challenge:** CHL-25
- **Cited source(s):** SQ-05/SRC-01, SQ-05/SRC-02
- **Independent check:** Carried from cycle 1 — unchanged. VN latest = 2022, IDN latest = 2016, a six-year currency gap.
- **Verdict:** supported
- **Reason:** The differing latest-year per country is verified; the no-like-for-like conclusion follows. Reinforces Tension 1's resolution.

## CLM-26 — Vietnam's GDP (current US$) was ~$476.4 billion in 2024, the most recent reported year (NY.GDP.MKTP.CD).

- **Challenge:** CHL-26
- **Cited source(s):** SQ-06/SRC-01 (World Bank NY.GDP.MKTP.CD, VNM)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query: 2024 = 476,388,230,307.18 (~$476.4B), most recent non-null.
- **Verdict:** supported
- **Reason:** Primary endpoint returns the exact 2024 GDP figure.

## CLM-27 — Vietnam's total population was ~101.0 million in 2024 (SP.POP.TOTL).

- **Challenge:** CHL-27
- **Cited source(s):** SQ-06/SRC-01
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query: 2024 = 100,987,686 (~101.0M).
- **Verdict:** supported
- **Reason:** Endpoint returns the exact 2024 population figure.

## CLM-28 — Indonesia's GDP (current US$) was ~$1.40 trillion in 2024, the most recent reported year (NY.GDP.MKTP.CD).

- **Challenge:** CHL-28
- **Cited source(s):** SQ-06/SRC-02 (World Bank NY.GDP.MKTP.CD, IDN)
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query: 2024 = 1,396,300,098,190.97 (~$1.40T), most recent non-null.
- **Verdict:** supported
- **Reason:** Primary endpoint returns the exact 2024 GDP figure.

## CLM-29 — Indonesia's total population was ~283.5 million in 2024 (SP.POP.TOTL).

- **Challenge:** CHL-29
- **Cited source(s):** SQ-06/SRC-02
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 re-query: 2024 = 283,487,931 (~283.5M).
- **Verdict:** supported
- **Reason:** Endpoint returns the exact 2024 population figure.

## CLM-30 — On 2024 figures, Indonesia's economy is ~2.9x Vietnam's GDP and its population ~2.8x Vietnam's, making Indonesia the larger focus market by raw scale.

- **Challenge:** CHL-30
- **Cited source(s):** SQ-06/SRC-01, SQ-06/SRC-02
- **Independent check:** Carried from cycle 1 — unchanged. Cycle-1 computation: 1.3963e12 / 4.7639e11 = 2.93x GDP; 283,487,931 / 100,987,686 = 2.81x population.
- **Verdict:** supported
- **Reason:** The ratios derive correctly from independently fetched figures.

## CLM-31 — No published market-size figure scoped to the specific category (SMB sales-call AI notetaker, SEA) was retrievable from the v1 free stack; SQ-07 is recorded as UNANSWERED for its specific ask.

- **Challenge:** CHL-31
- **Cited source(s):** SQ-07/SRC-01 (https://www.marketresearchfuture.com/reports/ai-meeting-assistants-market-12218)
- **Independent check (re-verified cycle 2):** WebFetched the MRF page directly. It carries only the broad AI-meeting-assistants category global figures and a coarse Asia-Pacific ~20% regional share, with no Southeast Asia, SMB, or sales-call-notetaker slice. The honest "unanswered for the specific ask" status holds.
- **Verdict:** supported
- **Reason:** The cited page confirms it carries no SEA/SMB/sales-notetaker-scoped figure; the UNANSWERED verdict is accurate and the gap is honestly preserved.

## CLM-32 — For the broader "AI meeting assistants" category, Market Research Future reports a global market of ~$3.5B in 2025, forecast to ~$34.28B by 2035, at 25.62% CAGR.

- **Challenge:** CHL-32
- **Cited source(s):** SQ-07/SRC-01 (MRF report page)
- **Independent check (re-verified cycle 2):** WebFetched the cited page. 2024 = $2.789B, 2025 = $3.503B (~$3.5B), 2035 = $34.28B, CAGR 2025–2035 = 25.62%. All match.
- **Verdict:** supported
- **Reason:** Every figure matches the cited page verbatim, correctly framed as the broader category, not the requested slice.

## CLM-33 — That same source attributes ~20% of the global market to Asia-Pacific as a whole, with no SEA/SMB/sales-call sub-breakdown.

- **Challenge:** CHL-33
- **Cited source(s):** SQ-07/SRC-01 (MRF report page)
- **Independent check (re-verified cycle 2):** WebFetched the page: regional shares NA ~45%, Europe ~30%, Asia-Pacific ~20%, MEA ~5%; no SEA/SMB/sales-notetaker sub-breakdown.
- **Verdict:** supported
- **Reason:** The ~20% APAC share and the absence of finer breakdowns are confirmed on the cited page.

## CLM-34 — RETIRED (cycle 2). The cycle-1 ~US$12.03B "Southeast Asia AI market, 2025" figure (Statista via search digest) is dropped: the Statista page is paywalled and the figure is scope-incommensurable.

- **Challenge:** CHL-34
- **Cited source(s):** SQ-07/SRC-02 (https://www.statista.com/outlook/tmo/artificial-intelligence/southeast-asia)
- **Independent check (re-verified cycle 2):** WebFetched the Statista SEA-AI outlook page directly. The headline figures are paywalled, rendered literally as "US$*****bn" and "CAGR ********* of *****%", behind a "Limited Access" notice requiring a Professional Account or Business Suite. The $12.03B value is not on the openly-fetchable page. The draft's retirement of the figure — both because the source is gated (incompatible with this run's `reproducible` label) and because a whole-economy SEA-AI figure is scope-incommensurable with the requested SMB-sales-notetaker slice — is correct and honest.
- **Verdict:** retired (not counted as a checkable claim)
- **Reason:** I independently confirmed the Statista figure is paywalled and unfetchable on the open web; the claim is correctly dropped, not relabelled "context." No figure is substituted, so there is nothing to ground — this is the honest outcome, not a refusal. The market-size ask stays UNANSWERED via CLM-31.

## Summary

- Claims checked: 33 (CLM-01 … CLM-33; CLM-34 is RETIRED and not a checkable claim)
- Supported: 33 · Partial: 0 · Refused: 0
- Grounding score: 33 / 33 = 1.00
- Refusals: 0
- Retired: 1 (CLM-34 — paywalled/gated Statista figure dropped, independently confirmed unfetchable; honest non-answer, not a refusal)
- Tensions: 2 / 2 resolved — Tension 1 (CLM-21 vs CLM-23) resolved via the data-currency caveat now present inside CLM-21, CLM-23 and CLM-25; Tension 2 (CLM-32 vs former CLM-34) resolved via retirement of CLM-34, with CLM-32/33 retained only as explicitly-labelled broad-global context.

### Cycle-2 disposition vs cycle 1

The cycle-2 re-research cured every cycle-1 partial and the single refusal, each re-verified against a source I fetched myself this cycle:

- **CLM-02 (was refused → supported):** Gong positioning + "Revenue Graph" now cited to gong.io, which carries them verbatim.
- **CLM-01 (was partial → supported):** wider vendor list now cited to the otter.ai round-up, which literally names all ten vendors.
- **CLM-06 (was partial → supported):** lawsuit re-cited to the National Law Review article, which carries every fact; the un-sourced "fallen behind in features" framing was dropped, and the draft correctly says "federal court in California" without over-specifying the district (the article names none).
- **CLM-07 (was partial → supported):** the Gong segmentation leg now grounded on the otter.ai round-up; Fireflies/Fathom legs on the re-fetched index.dev article.
- **CLM-10 / CLM-11 / CLM-12 (were partial → supported):** Otter and Fathom pricing now cited to each vendor's own pricing page; the stale derivative figures (Otter Pro $10 / Enterprise $39; Fathom ~$15/$19; the phantom "Team Edition Pro" tier) were corrected against the vendor pages.
- **CLM-13 (was supported, now fully grounded):** all three free tiers verified on vendor-primary pages.
- **CLM-34 (was partial → retired):** the paywalled Statista figure is dropped entirely rather than carried as "context"; I independently confirmed the page is gated.
- **Structured spine (CLM-14–30):** unchanged from cycle 1 and carried forward — all supported against re-queried OpenAlex/World Bank endpoints.

The contradiction signal is now fully cleared: 0 refusals and both tensions resolved. The remediation was real, not cosmetic — each fix re-grounds the claim to a source that actually contains it, and the corrections (Otter/Fathom pricing) materially changed the figures rather than just re-pointing the citation. Grounding rose from 26/34 = 0.76 (cycle 1) to 33/33 = 1.00 (cycle 2).
