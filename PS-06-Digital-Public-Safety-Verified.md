# PS-06 Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| CurrencyGuard (febisarju) | Repo | ⚠️ | 2 stars (evaluation stated 8 — minor factual error). MIT, last push 2025-03. Single contributor. |
| rowhitswami/Indian-Paper-Currency-Classification | Repo | ✅ | 147 stars, Apache 2.0 — **missed in initial evaluation**. Stronger counterfeit detection reference. |
| PMP (Xtra-Computing/PMP) | Repo | ✅ | 18 stars, ICLR 2024 paper code, functional. |
| FraudGT (junhongmit/FraudGT) | Repo | ✅ | 38 stars, CC-BY-4.0, ICAIF 2024, documented, active. |
| Kavalan (Keerthivasan-Venkitajalam) | Repo | ⚠️ | 1 star, MIT, created Dec 2025 — very new, single contributor, unvetted. |
| Real FICN datasets | Data | 🔴 | Confirmed restricted to RBI/law enforcement. No public access. |
| Academic fraud graph datasets (Yelp, Amazon, T-Finance) | Data | ✅ | Public, documented in PMP and FraudGT papers. |
| Scam call audio datasets | Data | 🔴 | Public research datasets are limited and do not specifically cover Indian digital arrest patterns. |

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | ✅ Consistent | Strong prior art per sub-problem (15) and solid per-component repos (14) align. No integrated platform exists. |
| D1↔D3 | ⚠️ Tension explainable | Strong research exists but real operational data (FICN, call metadata) is restricted. Research generally uses academic/synthetic datasets — this is correctly reflected in D3's low score (9). |
| D2↔D4 | ✅ Consistent | Individual building blocks exist (14) but integrating 3 sub-problems with near-zero FP tolerance makes D4 moderate (11). |
| D5↔D1 | ✅ Consistent | India-specific fraud patterns (digital arrest scams, Indian currency) have dedicated research. Score 17 justified. |
| D3↔D4 | ✅ Consistent | Data scarcity (9) drives the need for synthetic data generation, which adds complexity (11). |

## Bias Audit

- **Optimism flags:** Slight — CurrencyGuard stars overstated (8→2). However, the stronger rowhitswami repo (147 stars) was missed, offsetting this. Net effect neutral.
- **Pessimism flags:** None. D3 score of 9 is appropriate given confirmed data restrictions. D4 = 11 is fair for 3 sub-problems.
- **Calibration:** D1–D3 avg = 12.7, D4 = 11.0. Gap of 1.7 pts is reasonable and consistent. No correction needed.

## Devil's Advocate

- **D1 challenge:** "Digital arrest scam detection is brand new (all papers from 2025)." — Score 15 already reflects this (emerging sub-field within a broader well-studied domain). No change.
- **D2 challenge:** "Kavalan has 1 star and 1 contributor." — True, flagged as a risk. But FraudGT (38 stars) and rowhitswami (147 stars) are solid. No score change.
- **D3 challenge:** "Real FICN and scam call data simply don't exist publicly." — Correct. Score 9 already reflects this critical bottleneck. Adjustment considered: -1? No — 9 is already in the "very limited" band (6-9). Staying at 9.
- **D4 challenge:** "Three sub-problems means triple the work. Near-zero false positive is PhD-level." — Valid. Score 11 appropriately reflects high complexity.
- **D5 challenge:** "Is the India context really essential, or could you build a generic fraud detection system?" — Digital arrest scams are uniquely Indian (Rs 1,776Cr, MHA-specific). Indian currency design is unique. Score 17 justified.

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 15 | 15 | ✅ Confirmed — prior art per sub-problem is solid |
| D2 | 14 | **15** | ⬆️ **+1** — Initial eval cited CurrencyGuard (2 stars) but missed rowhitswami/Indian-Paper-Currency-Classification (147 stars, Apache 2.0), a much stronger repo. Net improvement. |
| D3 | 9 | 9 | ✅ Confirmed — data restrictions verified as critical |
| D4 | 11 | 11 | ✅ Confirmed — complexity assessment is accurate |
| D5 | 17 | 17 | ✅ Confirmed — India specificity is genuine |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| 15 | **15** | 9 | 11 | 17 | **67/100** |

Research: 13.0 | Build: 11 | ET: 17

## Verdict

✅ **Adjusted** — D2 adjusted upward (+1) from 14→15 due to discovery of stronger open-source repo (rowhitswami 147 stars, Apache 2.0) missed in initial evaluation. Total revised from 66→67. Verdict remains 🟡 Moderate.
