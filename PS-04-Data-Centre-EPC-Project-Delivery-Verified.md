# PS-04: Data Centre EPC Project Delivery — Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| VitorMRodovalho/meridianiq (★0, MIT) | Repo | ✅ | Very actively developed (515 commits, 10 releases, v4.3.0, last push Jun 2026). MIT license. Implements AACE RP standards, DCMA 14-Point, ML delay prediction. However 0 stars and 48 open issues — single-contributor risk. |
| hah23255/aec-rag-system (★1, MIT) | Repo | ⚠️ | MIT license, production-grade RAG for AEC with GraphRAG. But 1 star, 9 commits, single contributor, last updated Nov 2025. Still in early stages. |
| meysamesh/certAIn (★1, MIT) | Repo | ⚠️ | MIT license, Streamlit app with Monte Carlo + ML risk. 1 star, 1 contributor, Mar 2026. Very new. |
| Build.inc "Data Center Commissioning with AI" (2026) | Article | ✅ | Live article (build.inc/insights). Documents real industry practice: 40-60% test script drafting reduction using AI. Published Apr 2026. |
| SGS Digital Commissioning (2026) | Article | ✅ | Live (sgs.com). Confirms the industry trend toward digital commissioning with real-time visibility. Published Feb 2026. |
| Turner & Townsend 2024 survey | Report | ✅ | Industry benchmark — 67% of APAC DC EPC projects have >10% schedule overruns. Widely cited. |
| JLL India Data Centre Report 2025 | Report | ✅ | 900MW → 2,700MW by 2027 projection. Industry standard reference. |

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | Consistent | Both are emerging — few papers (D1=12) match few mature repos (D2=11). Construction schedule AI exists (MeridianIQ) but data centre EPC specifically is new. |
| D1↔D3 | Consistent | Prior art is limited partly because data is proprietary (D3=10). The chicken-and-egg problem of EPC data confidentiality is a real bottleneck. |
| D2↔D4 | Consistent | Open-source tools exist but are early-stage (0-1★), which matches the moderate-high complexity (D4=12) of composing them into an integrated platform. |
| D5↔D1 | Tension exists but explainable | High ET relevance (16) with moderate prior art (12) is coherent: the India data centre boom is a specific, timely context, but the underlying AI techniques (RAG, schedule prediction) have prior art in adjacent construction domains. |
| D3↔D4 | Consistent | Hard-to-access data (D3=10) matches the moderate-high complexity (D4=12) — synthetic data generation adds pipeline effort. |
| D1↔D5 | Consistent | The PS targets a globally general problem (data centre EPC) in a specific Indian context. D1 reflects the general prior art; D5 reflects the India-specific timeliness. |

## Bias Audit

- **Optimism flags:** D2 initially scored 12 but MeridianIQ has 0 stars and 48 open issues — valuable as infrastructure but fragile. AEC-RAG and certAIn are single-contributor. Adjusted D2 down.
- **Pessimism flags:** None. The D3=10 score could be argued as pessimistic — public BIM datasets and Kaggle construction datasets do exist — but the core EPC project data (schedules, RFIs, test records) is genuinely confidential.
- **Calibration:** D1-D3 avg = 11.0 | D4 = 12 — consistent (limited research with moderate engineering complexity). D5 = 16 — justified by India-specific data centre boom context.

## Devil's Advocate

- **D1 challenge:** "The prior art is in adjacent domains, not data centre EPC specifically." — Valid. Construction schedule prediction and AEC RAG are adjacent, not identical. The "data centre EPC intelligence" framing is genuinely novel.
- **D2 challenge:** "MeridianIQ has 0 stars and 48 open issues — is it usable?" — Partially valid. The repo has high engineering quality (1687 tests passing, CI/CD, 10 releases) but single-contributor risk is real. Not production-ready for enterprise.
- **D3 challenge:** "TIA-942 standard is behind a paywall — can't build compliance checking without it." — Partially valid. The white paper is free (summary), but full standard text requires purchase. Compliance checking without the full standard text is imprecise.
- **D4 challenge:** "Five sub-systems is too broad for a hackathon." — Valid. The PS explicitly suggests 5 agents. A team would need to prioritise 1-2.
- **D5 challenge:** "The data centre boom is real, but would ET judges value an EPC schedule tool over EV/safety problems?" — The $15B capital deployment and India's AI infrastructure ambitions make this timely, but it lacks the human impact angle of PS-01 (industrial safety) or PS-03 (EV adoption).

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 12 | 12 | Confirmed — emerging field with adjacent prior art. |
| D2 | 12 | 11 | MeridianIQ is 0★ with 48 open issues; AEC-RAG and certAIn are 1★ single-contributor. Ecosystem is very early-stage. |
| D3 | 10 | 10 | Confirmed — TIA-942 paywall issue noted. BIM/CAD public datasets exist. |
| D4 | 12 | 12 | Confirmed — 5 sub-systems is broad; integration complexity correctly assessed. |
| D5 | 16 | 16 | Confirmed — JLL 2025 report and Turner & Townsend survey verify the India DC boom narrative. |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| 12 | 11 | 10 | 12 | 16 | **61/100** |

Research: 11.0 | Build: 12 | ET: 16

## Verdict

🟡 Moderate — D2 adjusted down from 12 to 11 after source verification revealed the key repos (MeridianIQ, AEC-RAG, certAIn) are single-contributor and very early-stage (0-1★). The India data centre boom context (verified by JLL 2025 report and Turner & Townsend) keeps ET relevance strong at 16. The core challenge remains data confidentiality and the broad 5-sub-system scope — best tackled by focusing on 1-2 sub-systems (spec compliance RAG + schedule risk) for a credible hackathon prototype.
