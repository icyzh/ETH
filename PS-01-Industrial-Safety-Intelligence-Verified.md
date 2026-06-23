# PS-01 Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| Liu et al. 2024 — Deep Industrial Image Anomaly Detection survey | Paper | ✅ | Open-access on Springer. Canonical survey, well-cited. |
| Jiang et al. 2022 — Visual sensory anomaly detection survey | Paper | ✅ | arXiv preprint, open access. |
| MFGAN 2024 — Multimodal Fusion for Industrial Anomaly Detection | Paper | ✅ | MDPI Sensors, open access. |
| RGBD fusion 2025 — Accurate industrial anomaly detection | Paper | ✅ | ScienceDirect Array, CC license. |
| Anomalib (open-edge-platform/anomalib) | Repo | ✅ | 3.6k stars, MIT license, active (v2.5.0 May 2026). pip-installable. |
| PPE Detection (ZijianWang-ZW/PPE_detection) | Repo | ✅ | 67 stars, public, CHV dataset available. Last commit 2022 (stale but functional). |
| ADTK (arundo/adtk) | Repo | ✅ | Active, documented, pip-installable. |
| MVTec AD dataset | Dataset | ✅ | Public, standard format, well-documented. Not for multi-sensor safety. |
| CIC IIoT Dataset 2025 | Dataset | ✅ | Free download from UNB. Sensor+network data, not safety-scenario specific. |
| AI4I Predictive Maintenance (UCI) | Dataset | ✅ | Public, synthetic, widely used. CC0 license. |

**Liveness note:** No URLs embedded in the evaluation text — sources are cited by name. All repos and datasets verified during research. All are reachable and correctly described.

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | Consistent | D1 correctly notes compound risk is novel; D2 finds code for sub-problems, not the full problem. No contradiction. |
| D1↔D3 | Consistent | Prior art uses different datasets (visual defects, cybersecurity) than what this PS needs (safety sensor fusion). Aligns. |
| D2↔D4 | Consistent | Good libraries for sub-components explain D2=14; integration and domain adaptation explain D4=11. |
| D5↔D1 | Tension exists but explainable | D5=17 (strong ET relevance) and D1=13 (emerging prior art). The prior art is in adjacent domains (generic anomaly detection), not Indian industrial safety compound risk. The ET angle (OISD/DGFASLI regulatory context) is genuinely different. |
| D3↔D4 | Consistent | Data scarcity (D3=8) is part of why complexity is moderate-high (D4=11). Bottleneck is data + integration, not algorithm. |
| D1↔D5 | Tension exists but explainable | Prior art exists but in adjacent fields. ET angle is specific. No contradiction. |

## Bias Audit

- **Optimism flags:** None. Scores are in the 8-17 range (not inflated). Evidence is specific (named papers, authors, repos). No "should be easy" or vague claims.
- **Pessimism flags:** Potential pessimism on D3 — the AI4I dataset at UCI is a reasonable proxy for sensor data, and the MVTec AD family has expanded. However, the core issue (no labeled compound risk dataset) remains valid.
- **Calibration:** D1-D3 avg = 11.7, D4 = 11. Aligned — no calibration issue.

## Devil's Advocate

- **D1 challenge:** "The prior art solves a different problem." Valid. Anomalib detects visual defects on manufactured parts. MFGAN uses DCS+acoustic signals for machinery faults. Neither fuses gas sensors + permit-to-work + CCTV for compound safety risk. The gap between cited work and this PS is significant. **Suggests D1 should be 10-11.**
- **D2 challenge:** "The repos are for different tasks." Valid. Anomalib is for visual defect detection, not safety sensor fusion. PPE repos are single-task CV. ADTK is generic time-series. None address the core compound risk fusion problem. **Suggests D2 should be 12-13.**
- **D3 challenge:** "Labels don't exist." Confirmed. No public labeled dataset for multi-sensor compound risk scenarios. **D3=8 is already appropriately low.**
- **D4 challenge:** "Chain of 5 models." Valid. Integration of IoT gas sensors + SCADA + permit-to-work logs + CCTV + shift records + RAG + geospatial dashboard = 5+ distinct systems. The hardest 10% is making compound risk detection work without ground truth labels. Domain expertise in industrial safety is required. **Suggests D4 should be 10.**
- **D5 challenge:** "Could use other regulatory frameworks." Partial valid. OISD/DGFASLI is India-specific, but the core challenge (multi-sensor safety fusion) is universal. However, the PS is deeply anchored in Indian incidents (Visakhapatnam 2025) and Indian regulatory context. **D5=17 is defensible.**

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 13 | 11 | Devil's advocate: cited prior art solves adjacent problems, not compound risk |
| D2 | 14 | 13 | Devil's advocate: repos solve sub-tasks, none address core compound risk fusion |
| D3 | 8 | 8 | — Already validated as appropriately low |
| D4 | 11 | 10 | Devil's advocate: chain of 5+ models + no ground truth = harder than initial assessment |
| D5 | 17 | 17 | — India-specific regulatory context is genuine and defensible |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| **11** | **13** | **8** | **10** | **17** | **59/100** |

Research: 10.7 | Build: 10 | ET: 17

## Verdict

🟡 **Adjusted** — Scores adjusted down by 4 points total after devil's advocate pass revealed the gap between prior art (which solves adjacent problems) and the core compound risk challenge. The ET relevance remains the strongest signal. This is a high-risk/high-reward PS: deeply relevant to ET's coverage, but the novel core problem + data scarcity + evaluation difficulty make it challenging. Best suited for a team with industrial safety domain expertise who can build a compelling synthetic-data demo.
