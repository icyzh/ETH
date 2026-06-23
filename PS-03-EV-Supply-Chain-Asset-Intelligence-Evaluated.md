### PS-03: AI for Industrial EV Supply Chain & Asset Intelligence: Accelerating Net Zero

**PS Description (from ET):**

> Build an AI platform that addresses the industrial EV transition from two interconnected angles: (1) helping asset-intensive organisations manage EV fleets with the same operational rigour as conventional industrial equipment — covering procurement intelligence, predictive asset performance management, and maintenance operations; and (2) helping EV manufacturers manage the complex, quality-critical supply chains that make reliable EVs possible.

**Core Technical Challenge:**

- Build a dual-focus AI system that (a) predicts battery degradation and optimises fleet operations for industrial EV adopters, while (b) monitoring multi-tier EV battery supply chain risk (critical minerals sourcing, supplier concentration, quality deviations) — requiring sensor fusion, time-series forecasting, supply chain graph analysis, and quality management integration across two distinct but related domains.

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 14/20 | Battery degradation RUL prediction is a mature field with multiple survey papers (Wang et al. 2025, Xu et al. 2025 — 200+ studies reviewed, 5 public datasets benchmarked). EV fleet management has strong commercial prior art (Datakrew, Volteum, Shift AI) and academic research (FleetPy, TUM). Supply chain traceability for EV batteries has active research: SHIELD framework (LLM + GCN for disruption prediction, arXiv 2408.05357), ChainSense (multi-agent supply chain risk), SupplyGraph AI. However, no single system integrates fleet APM + supply chain intelligence as described. |
| D2: Open Source | 15/20 | Microsoft BatteryML (714 stars, MIT, ICLR 2024) is production-ready for battery degradation modeling with preprocessing, feature extraction, and built-in SOTA models. FleetPy (TUM, open-source fleet simulation, multi-star) handles EV charging, routing, and dispatch. ChainSense SCM (multi-agent supply chain risk platform, Spring AI + React) directly addresses EV battery supply chain risk. Multiple supporting repos: celljar (data harmonisation), SHIELD (LLM-based disruption), SupplyLens (supply chain transparency). No single integrated repo combining fleet + supply chain, but strong building blocks exist for each. |
| D3: Data | 13/20 | Multiple public battery datasets: NASA PCoE (18650 cells, 6+ profiles, public domain), CALCE (LCO/LFP/NMC, prismatic/pouch, 15+ cells), MIT/Stanford (commercial cells). For supply chain: UN Comtrade (global trade flows), USGS (mineral summaries, public), IEA/BNEF (energy statistics). JMK Research and SIAM provide India-specific EV market data. However, fleet telematics data from industrial vehicles is proprietary (Datakrew, Volteum are commercial). Real factory QMS data is confidential. Lab-scale battery data may not transfer to pack-level industrial fleets. |
| D4: Complexity | 11/20 | Battery degradation modeling is well-understood (BatteryML provides one-click training). Fleet management dashboard is moderate complexity. The dual scope (fleet APM + supply chain) significantly increases integration surface. Multi-agent orchestration across telematics, BMS, and supplier data streams is non-trivial. Supply chain graph analysis with real-time disruption monitoring requires substantial engineering. Evaluation across both domains requires separate test frameworks. GPU needed for battery ML training. Synthetic data likely needed for fleet telematics. |
| D5: ET Relevance | 16/20 | Directly tied to India's EV transition: 2M+ EV registrations in FY2025, industrial EV penetration below 2.5%, 30% commercial EV target by 2030. India's ACC battery demand projected at 272GWh by FY2030 (IESA), with 75% of Li-ion cells imported from China — a strategic vulnerability covered extensively by ET. FAME-II policy, SIAM statistics, IEEFA/JMK reports provide India-specific context. Dual fleet + supply chain focus mirrors ET's coverage of both industrial operations and manufacturing policy. The battery component PLI scheme (Rs 12,000 crore) makes this highly timely. |
| **TOTAL** | **69/100** | |

### Composites

- Research: 14.0 | Build: 11 | ET: 16

### Risk Factors

- Dual focus (fleet + supply chain) doubles scope — likely need to pick one to build a credible prototype
- Fleet telematics data is proprietary — must rely on synthetic data or public transit datasets as proxy
- Lab-scale battery datasets (NASA, CALCE) may not generalise to industrial EV packs
- No single integrated open-source system exists — must compose from disparate tools
- Battery electrochemistry domain expertise needed for credible degradation modeling
- Supply chain data for Indian-specific EV supply chains requires manual curation from multiple sources

### Verdict

🟡 Moderate — Strong building blocks for battery degradation (BatteryML) and supply chain risk (ChainSense, SHIELD), with high ET relevance tied to India's EV import vulnerability and industrial adoption gap. The dual-scope is the main risk — best approached by focusing on one angle (fleet APM or supply chain) with a secondary connection to the other. Solid foundation for a compelling prototype.
