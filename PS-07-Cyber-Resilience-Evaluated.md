### PS-07: AI-Driven Cyber Resilience for Critical National Infrastructure

**PS Description (from ET):**

> Build an AI-powered Cyber Resilience platform for critical national infrastructure that autonomously detects behavioural anomalies, correlates weak signals across heterogeneous IT and OT environments, maps attack progression against known threat frameworks, and orchestrates containment actions — compressing the time from initial compromise to detection and response from weeks to hours.

**Core Technical Challenge:**

- Build a multi-agent UEBA system that profiles normal behaviour across users, devices, and network segments — fusing IT and OT telemetry — maps anomalies to MITRE ATT&CK techniques in real time, and executes SOAR playbooks for containment, all while operating within Indian critical infrastructure constraints (end-of-life systems, CERT-In compliance, OT air-gapped environments).

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 15/20 | UEBA is mature: A-UEBA 2025, Deep Autoencoder UEBA (AIMS Mathematics 2025), Gurucul/Splunk commercial platforms. MITRE ATT&CK mapping is well-studied with official tools (Navigator, Python library, STIX/TAXII). SOAR automation is widely deployed (Google SOAR, Elastic Workflows 2026, Swimlane AI Agent 2026). APT campaign attribution is active research (Anthropic LLM ATT&CK Navigator 2026). BUT: the specific integration of UEBA + ATT&CK mapping + autonomous SOAR for Indian critical infrastructure is novel — no operational system found. |
| D2: Open Source | 15/20 | MITRE ATT&CK Python library (`mitreattack-python`, official, active). ATT&CK Navigator (open source web tool, GitHub). OpenCTI for threat intelligence platform. `nids-datasets` pip package for UNSW-NB15/CICIDS2017 loading. Multiple anomaly detection repos (PyOD, DeepOD, `shannonasmith/AI-Assisted-SOC-MITRE-ATTACK-Mapping-Engine` 2026). Shuffle SOAR (open source SOAR, 5k+ stars). No single integrated platform combining full pipeline for Indian CI. |
| D3: Data | 13/20 | UNSW-NB15 (2.5M records, public, well-documented) and CICIDS2017 (80+ features, labeled) are excellent network intrusion benchmarks. MITRE ATT&CK (fully public API, STIX data). CVE/NVD (daily updates, public). CERT-In advisories (public). BUT: Real OT/SCADA datasets are extremely restricted (SANS/ICS-CERT samples exist but limited). Real endpoint telemetry is proprietary. Indian-specific critical infrastructure network data is not public. Core ML data is solid; operational data is restricted. |
| D4: Complexity | 12/20 | Core algorithms are well-understood (autoencoders, isolation forests, LSTM for UEBA; graph traversal for attack paths). MITRE ATT&CK integration is API-level work. SOAR playbook development is engineering, not research. Real-time inference requires moderate engineering (low-latency pipeline). Evaluation is manageable: benchmark datasets + clear metrics (F1, detection rate, MTTD/MTTR). Demo-ability: Streamlit dashboard with alert timeline + playbook simulation. Main challenges: OT data access, risk of false-positive autonomous containment, integration of heterogeneous log formats. |
| D5: ET Relevance | 17/20 | Directly addresses Indian critical infrastructure cybersecurity. References CERT-In (1.59M incidents 2023, 29.44 lakh 2025), AIIMS ransomware (2022), CBSE breaches (2024/2026). Uses India-specific regulatory context: CERT-In 6-hour reporting mandate, NCIIPC, National Cyber Security Policy (70% end-of-life IT). Core ET coverage domain. Can prototype with benchmark datasets and simulate Indian CI context. |
| **TOTAL** | **72/100** | |

### Composites

- Research: 14.3 | Build: 12 | ET: 17

### Risk Factors

- Real OT/SCADA data from Indian critical infrastructure is restricted and may not be accessible for training/validation
- Autonomous containment carries risk of false-positive damage in critical CI environments — requires careful human-in-the-loop design
- Public benchmark datasets (UNSW-NB15, CICIDS2017) may not reflect APT behavior or Indian CI network characteristics
- Deep cybersecurity + OT security domain expertise required (Purdue model, ICS protocols)
- Evaluation of MTTD/MTTR improvement requires SOC baseline comparison, which is hard to simulate credibly
- CERT-In data sharing policies and sensitivity/classification of CI network data are potential blockers

### Verdict

🟢 Strong — Highest total score so far (72/100). UEBA, MITRE ATT&CK mapping, and SOAR automation are all well-studied with mature open-source building blocks. Benchmark datasets are solid for core ML. ET relevance is very high with strong Indian critical infrastructure context. The main risk is data access (real OT/SCADA data) and the operational complexity of deploying autonomous response in live CI environments, but a compelling prototype can be built using public benchmark data with simulated Indian CI scenarios.
