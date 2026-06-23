### PS-02: AI-Driven Energy Supply Chain Resilience for Import-Dependent Economies

**PS Description (from ET):**

> Design an AI-powered Energy Supply Chain Resilience system that monitors geopolitical and logistics risk signals continuously, models disruption scenarios and their downstream economic impacts, and generates executable procurement rerouting recommendations — turning a reactive crisis response into a managed, anticipatory process.

**Core Technical Challenge:**

- Continuously fuse heterogeneous signals (news/GDELT, AIS vessel tracking, commodity pricing, sanctions data) into a real-time geopolitical risk score for energy supply corridors, then simulate disruption scenarios and recommend alternative procurement routes — all in an integrated multi-agent system.

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 15/20 | Substantial research body on AI for supply chain resilience under geopolitical risk (2024-2025 special issues in Transportation Research Part E; Dong et al. 2025; systematic review by López et al. 2025). IEA, IRENA, McKinsey reports. Supply chain digital twin concepts well-documented (Cimino et al. 2024). Geopol Forecaster open-source pipeline exists. |
| D2: Open Source | 12/20 | GDELT Python clients exist (gdeltdoc, gdelt-py — MIT license, active). OpenAIS tools for AIS data processing. Maritime anomaly detection repos (Bi-LSTM on AIS, 93-star PhantomTide for maritime intelligence). Supply chain digital twin repos exist but are small (0-5 stars) and unmaintained. No single integrated "energy supply chain resilience" system. |
| D3: Data | 12/20 | GDELT API — free, massive geopolitical event database (7 years, 15-min updates). AIS data available via MarineCadastre (free) and MarineTraffic (rate-limited free tier). IEA, BP, EIA — free energy statistics. OFAC/UN sanctions registries — public. Port congestion partially public. But Platts/S&P pricing data is subscription-only, and high-res AIS in Indian Ocean is gated. |
| D4: Complexity | 11/20 | Multi-source real-time fusion (news + AIS + pricing + sanctions) is a significant integration challenge. Scenario simulation/digital twin for energy supply chains requires substantial engineering. Risk scoring is more signal fusion than novel ML. Evaluation difficult without real disruptions — must use historical scenarios (2020 oil price war, 2022 Russia-Ukraine, 2025 US-Iran). |
| D5: ET Relevance | 18/20 | Directly about India's structural energy vulnerability (88% import dependence, 40-45% via Strait of Hormuz, 9.5-day SPR). References specific Indian refiners (IOCL, BPCL, HPCL) and SPR sites (Mangalore, Visakhapatnam, Padur). Core ET coverage domain: energy markets, geopolitics, trade policy, industrial economics. Extremely timely given 2025-2026 Persian Gulf and Red Sea tensions. |
| **TOTAL** | **68/100** | |

### Composites

- Research: 13.0 | Build: 11 | ET: 18

### Risk Factors

- Platts/S&P Global commodity pricing data is subscription-only — must use simulated or delayed free alternatives
- Free AIS data has coverage gaps in Indian Ocean / Persian Gulf — critical for this problem
- Scenario model fidelity is hard to validate without real disruption events
- Energy economics + geopolitics domain expertise is essential
- No single integrated open-source system exists — must compose from multiple disparate tools
- Digital twin simulation can be compute-intensive

### Verdict

🟡 Moderate — Strongest ET relevance of any PS so far, with good underlying research base. The main challenges are data integration complexity and evaluation difficulty. A compelling demo using historical scenarios (2025 Hormuz crisis) is feasible. Best suited for a team with supply chain or energy economics background.
