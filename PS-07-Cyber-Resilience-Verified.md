# PS-07 Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | :----: | -------------------- |
| `mitre-attack/mitreattack-python` | Repo | 🟢 | 717 stars, Apache-2.0, active (v6.1.0 May 2026) |
| `rdpahalavan/nids-datasets` | Repo | 🟢 | 33 stars, pip-installable, functional |
| `shannonasmith/AI-Assisted-SOC-MITRE-ATTACK-Mapping-Engine` | Repo | 🟡 | 0 stars, 0 forks — exists but no community validation; cited alongside PyOD (8k+) which carries the weight |
| OpenCTI | Repo | 🟢 | 6k+ stars, active, Apache-2.0 |
| Shuffle SOAR | Repo | 🟢 | 5k+ stars, active |
| UNSW-NB15 | Dataset | 🟢 | Public, well-documented, 2.5M records |
| CICIDS2017 | Dataset | 🟢 | Public, 80+ features, labeled, on UNB CIC site |
| MITRE ATT&CK API/STIX | API | 🟢 | Fully public, well-documented |
| CERT-In advisories | Data | 🟢 | Public |
| Gurucul UEBA | Commercial | 🟢 | Active product |
| Elastic Workflows (SOAR) | Commercial | 🟢 | Announced Mar 2026, active |
| A-UEBA 2025 | Paper | 🟢 | Published at ACM 2025 conference |
| Deep Autoencoder UEBA 2025 | Paper | 🟢 | Published AIMS Mathematics 2025 |
| Anthropic LLM ATT&CK Navigator 2026 | Report | 🟢 | Published Jun 2026, live |
| Swimlane MITRE AI Agent 2026 | Commercial | 🟢 | Live product, blog Mar 2026 |

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | :----: | ---- |
| D1↔D2 | 🟢 Consistent | Both reflect well-studied sub-components with no integrated solution |
| D1↔D3 | 🟢 Consistent | Prior art uses public benchmarks (D3 solid for benchmarks); real OT data restricted (keeps D3 moderate) |
| D2↔D4 | 🟢 Consistent | Excellent libraries exist but pipeline integration (SOAR+UEBA+ATT&CK) is complex |
| D5↔D1 | 🟡 Tension explainable | Global cybersecurity prior art exists; Indian CI context (CERT-In, NCIIPC, end-of-life IT) is genuinely different |
| D3↔D4 | 🟢 Consistent | Data solid for benchmarks; real challenge is log format integration, not data acquisition |
| D1↔D5 | 🟡 Tension explainable | Prior art solves adjacent global problems; D5 reflects uniquely Indian CI application context |

## Bias Audit

- **Optimism flags:** None. Scores are not inflated (72/100, not 80+). Concrete evidence cited for all claims.
- **Pessimism flags:** Minor — UNSW-NB15 and CICIDS2017 are legitimate benchmarks; score of 13/20 on D3 is fair given OT restrictions. `shannonasmith` repo cited despite 0 stars, but it's listed alongside PyOD/DeepOD which are the primary anchors.
- **Calibration:** Research avg (14.3) vs Build (12): difference of 2.3 — reasonable. Integration complexity is the bottleneck, not algorithms.

## Devil's Advocate

- **D1 challenge:** OT-specific anomaly detection (Modbus, DNP3, IEC 61850) has less prior art than enterprise IT UEBA. Evaluation acknowledges this in risk factors.
- **D2 challenge:** `shannonasmith` repo has 0 stars — weak citation. Mitigated by PyOD (8k+), DeepOD, and official MITRE tools being the primary anchors.
- **D3 challenge:** Real OT/SCADA data from Indian CI is restricted and may not reflect APT behavior. Evaluation acknowledges this in risk factors.
- **D4 challenge:** Real-time inference across heterogeneous log formats at Indian CI scale is genuinely hard. Score of 12/20 appropriately reflects this.
- **D5 challenge:** Indian CI context is strong and well-documented; CERT-In reporting mandate, NCIIPC, AIIMS/CBSE incidents are real. Score of 17/20 justified.

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | :------: | :------: | --------------- |
| D1 | 15 | 15 | — |
| D2 | 15 | 15 | `shannonasmith` repo has 0 stars but is peripheral to primary evidence (PyOD, DeepOD, official MITRE tools) |
| D3 | 13 | 13 | — |
| D4 | 12 | 12 | — |
| D5 | 17 | 17 | — |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| 15 | 15 | 13 | 12 | 17 | **72/100** |

Research: 14.3 | Build: 12 | ET: 17

## Verdict

🟢 Confirmed — All sources verified, cross-dimension consistency holds, no significant bias found. Minor issues (0-star repo citation) do not affect scores. Original evaluation is solid.
