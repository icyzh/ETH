# PS-03: EV Supply Chain & Asset Intelligence — Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| microsoft/BatteryML (758★, MIT) | Repo | ✅ | Active, ICLR 2024, pip-installable. Last commit Dec 2024. |
| TUM-VT/FleetPy (101★, MIT) | Repo | ✅ | Active, 3 releases (latest Mar 2026), 45 forks. |
| alpgi1/chainsense-scm (1★) | Repo | ⚠️ | No license file visible. Single contributor. Only 1 star, 0 forks. Useful as reference architecture but not production-ready. |
| F1y1113/MFI - SHIELD (69★, MIT) | Repo | ✅ | EMNLP 2024 Oral. MIT license, 11 forks. Dataset included. |
| NASA PCoE Battery Dataset | Dataset | ✅ | Public domain, direct download from data.nasa.gov. Updated Jul 2025. |
| CALCE Battery Data | Dataset | ✅ | Public access via calce.umd.edu. Multiple chemistries (LCO, LFP, NMC). |

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | Consistent | Both well-studied with multiple repos and public datasets. Battery degradation has excellent coverage. Supply chain side is newer but has SHIELD (69★, EMNLP) and ChainSense (reference architecture). |
| D1↔D3 | Consistent | Multiple public battery datasets (NASA, CALCE, MATR, HUST, SNL) support the battery degradation research. Supply chain data gaps (proprietary telematics) are acknowledged. |
| D2↔D4 | Consistent | Building blocks exist (BatteryML for degradation, SHIELD for supply chain), but integration across both domains drives complexity. No single integrated solution exists. |
| D5↔D1 | Tension exists | High ET relevance (16) with strong prior art (14) is explainable: the battery degradation field is globally mature but the India-specific EV supply chain context (75% import dependence, FAME-II, 272GWh demand) is the distinctive angle. |
| D3↔D4 | Consistent | Data availability is moderate (13) — public battery data exists but fleet telematics is proprietary — matching the moderate-high complexity (11) for pipeline integration. |
| D1↔D5 | Consistent | The dual scope (fleet + supply chain) is genuinely novel in combination, even though each sub-problem individually has prior art. |

## Bias Audit

- **Optimism flags:** D2 initially scored 15 based on ChainSense as a "strong" repo — but its 1★ and no license lower its value. Adjusted.
- **Pessimism flags:** None. Scores reflect a balanced assessment.
- **Calibration:** D1-D3 avg = 13.3 | D4 = 11 — consistent (moderate research with moderate complexity). D5 = 16 — justified by deep India-specific context.

## Devil's Advocate

- **D1 challenge:** "The prior art solves a different problem." — Partially true. Battery degradation prediction is well-trodden, but the fleet APM + supply chain integration is novel. Scores reflect this split.
- **D2 challenge:** "ChainSense has no license — can't use it." — Valid. Removed heavy weight from ChainSense. BatteryML (MIT) and SHIELD (MIT) remain solid.
- **D3 challenge:** "Lab-scale battery data won't transfer to industrial EV packs." — Valid concern. NASA/CALCE data uses small 18650 cells (1.1-2.8Ah), not EV-scale 50-100kWh packs. Generalisation gap noted.
- **D4 challenge:** "Looks easy until you try to integrate telematics + BMS + supply chain." — Valid. The dual-scope integration is the hardest part.
- **D5 challenge:** "Would ET judges care about battery RUL prediction that uses NASA data?" — The India-specific context (FAME-II, import dependence, SIAM data) anchors this to ET's coverage fairly strongly.

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 14 | 14 | Consistent — well-validated by verification |
| D2 | 15 | 13 | ChainSense has no license and 1★ — over-weighted initially. BatteryML (758★, MIT) and SHIELD (69★, MIT) are solid. |
| D3 | 13 | 13 | Confirmed — NASA, CALCE, UN Comtrade all public. Fleet telematics gap correctly flagged. |
| D4 | 11 | 11 | Confirmed — dual scope integration is the main challenge. |
| D5 | 16 | 16 | Confirmed — IEEFA/JMK/IESA reports verify the India EV supply chain vulnerability narrative. |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| 14 | 13 | 13 | 11 | 16 | **67/100** |

Research: 13.3 | Build: 11 | ET: 16

## Verdict

🟡 Moderate — Strong verified building blocks (BatteryML at 758★, SHIELD at 69★, NASA/CALCE datasets) with high ET relevance confirmed by current India EV supply chain data. D2 adjusted down from 15 to 13 to reflect ChainSense's unlicensed, single-contributor status. The dual-scope remains the primary risk. Best approached by focusing on one angle (fleet APM or supply chain) with linkage to the other.
