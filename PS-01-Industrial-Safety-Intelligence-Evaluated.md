### PS-01: AI-Powered Industrial Safety Intelligence for Zero-Harm Operations

**PS Description (from ET):**

> Build an AI-powered Industrial Safety Intelligence platform that brings together data from IoT sensors, SCADA systems, permit-to-work logs, CCTV feeds, and shift records into a single predictive layer. The system should detect compound risk conditions — like the co-occurrence of maintenance activity and hazardous gas accumulation — that no single sensor would flag alone, and trigger preemptive interventions before they escalate.

**Core Technical Challenge:**

- Fuse heterogeneous data streams (time-series sensors, video, tabular permits, shift records) into a unified compound risk detection model that identifies multi-factor hazard conditions unseen by any single sensor, and deliver preemptive alerts and compliance intelligence.

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 13/20 | Industrial anomaly detection is well-studied (survey papers: Liu et al. 2024, Jiang et al. 2022; multimodal fusion papers: MFGAN 2024, RGBD fusion 2025). BUT the specific "compound risk detection" fusing gas sensors + permit-to-work + CCTV is novel — no operational system found. Problem definition is still emerging. |
| D2: Open Source | 14/20 | Anomalib (3.6k stars, pip-installable, MIT, active) is production-ready for visual anomaly detection. Multiple PPE-detection repos (YOLO-based, 67+ stars). ADTK, Orion, Telemanom for time-series anomaly detection. No single repo implements the full compound risk fusion pipeline. |
| D3: Data | 8/20 | MVTec AD dataset exists for visual inspection but not multi-sensor safety. CIC IIoT Dataset 2025 has sensor+network data but no safety scenario labels. AI4I Predictive Maintenance (UCI, synthetic) available. Real IoT/SCADA data from operational plants is proprietary and security-sensitive. No labeled dataset for compound risk scenarios. |
| D4: Complexity | 11/20 | Core multi-sensor fusion architecture is known but compound risk adaptation requires non-trivial engineering. Multi-modal alignment (time-series + video + tabular) is complex. GPU needed for CV models. Evaluation hard — "incidents prevented" is not measurable in a prototype. Dashboard demo achievable with synthetic data. |
| D5: ET Relevance | 17/20 | Directly addresses Indian industrial safety (6,500+ fatalities FY2023, Visakhapatnam 2025 incident). Uses OISD/DGFASLI/Factory Act regulatory context — uniquely Indian. Core ET coverage domain. Can prototype with synthetic data but solution targets Indian heavy industry plants. |
| **TOTAL** | **63/100** | |

### Composites

- Research: 11.7 | Build: 11 | ET: 17

### Risk Factors

- No public labeled dataset for compound risk scenarios — synthetic data generation required and may not capture real failure modes
- Real IoT/SCADA data from operational plants is proprietary — prototype limited to simulation
- Evaluation of "incidents prevented" is inherently unverifiable in a hackathon setting
- Domain expertise in industrial safety (OISD, DGMS standards) needed
- Compound risk detection has no established baseline to benchmark against

### Verdict

🟡 Moderate — Strong ET relevance and solid building blocks for sub-components (anomaly detection, PPE CV), but the core compound risk fusion problem has limited prior art, no labeled data, and evaluation is inherently difficult. High risk/reward profile.
