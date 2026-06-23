# PS-02 Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| Dong et al. 2025 — Enhanced SCR under geopolitical risks (Transportation Research Part E) | Paper | ✅ | ScienceDirect, open access. Peer-reviewed. |
| López et al. 2025 — Modeling supply chain disruptions due to geopolitical reasons | Paper | ✅ | ScienceDirect, open access. Systematic review of 80 articles. |
| Cimino et al. 2024 — Supply Chain Digital Twin methodology | Paper | ✅ | Cleaner Logistics and Supply Chain, open access. |
| Geopol Forecaster (Daniel Rosehill blog, 2026) | Tool | ✅ | Blog post describing open-source pipeline. Functional but new (April 2026). |
| gdeltdoc 1.12.0 (alex9smith/gdelt-doc-api) | Repo | ✅ | GitHub, MIT license, active. pip-installable. |
| gdelt-py 0.1.6 (RBozydar/py-gdelt) | Repo | ✅ | PyPI, MIT license. Python 3.11+. |
| OpenAIS (open-ais.org) | Repo | ✅ | Open-source AIS processing tools. Active, documented. |
| PhantomTide (tg12/phantomtide) | Repo | ✅ | 93 stars, 10 forks. Data platform (not a buildable library). README confirms it's a public interface for feedback, app code not published. |
| Supply chain DT repos (MasterSoroush, akshsgaur) | Repo | ⚠️ | 0-2 stars, unmaintained or academic code. Correctly flagged as fragile. |
| GDELT API | Data | ✅ | Free, massive, 15-min updates. Active since 2013. |
| MarineCadastre AIS | Data | ✅ | Free, US waters. Indian Ocean coverage limited. |
| MarineTraffic AIS | Data | ⚠️ | Free tier rate-limited. Full coverage requires paid plan. |
| IEA Oil Market Report | Data | ✅ | Free summary data; detailed reports require subscription. |
| Platts / S&P Global | Data | ⚠️ | Subscription-only pricing. Correctly flagged. |
| OFAC/UN Sanctions | Data | ✅ | Public, regularly updated. |

**Liveness note:** No URLs embedded in evaluation text — all sources verified during research. Supply chain digital twin repos correctly flagged as fragile.

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | Consistent | D1 finds strong research body; D2 finds scattered code implementations. Research outpacing open-source code is expected in this domain. |
| D1↔D3 | Consistent | Research uses combination of public (GDELT, IEA) and proprietary (Platts) data. D3 correctly notes the paid data gap. |
| D2↔D4 | Consistent | Scattered code means significant integration work, confirming D4 complexity score. |
| D5↔D1 | Tension exists but explainable | D5=18 (strong ET uniqueness) and D1=15 (substantial prior art). The prior art studies generic supply chain resilience; the ET angle is India-specific energy security (88% import dependence, specific refiners, SPR sites). These are genuinely different. |
| D3↔D4 | Consistent | Partial data accessibility contributes to integration complexity. Bottleneck is multi-source fusion, not a single data pipeline. |
| D1↔D5 | Tension exists but explainable | Same as D5↔D1. Prior art is general; ET angle is India-specific energy security. |

## Bias Audit

- **Optimism flags:** None. Scores in 11-18 range. Evidence specific (named papers, authors, repos, data portals). No vague claims.
- **Pessimism flags:** Potential pessimism on D2 — the Geopol Forecaster pipeline exists and is functional (published April 2026). However, it's a single pipeline from a single developer, which is fragile. The assessment of supply chain DT repos as "0-5 stars, unmaintained" is accurate.
- **Calibration:** D1-D3 avg = 13.0, D4 = 11. Small gap is normal for integration-heavy problems. No calibration issue.

## Devil's Advocate

- **D1 challenge:** "The prior art is mostly theoretical." Valid. Most cited papers are conceptual frameworks or literature reviews, not operational systems. Few build and deploy working systems. The gap between research claims and operational reality is significant. **Suggests D1 should be 13-14.**
- **D2 challenge:** "GDELT clients are thin wrappers. PhantomTide is a data platform, not a buildable library." Valid. gdeltdoc is a useful but thin API wrapper. PhantomTide explicitly states "application code is not published here." Supply chain DT repos are academic or empty. **Suggests D2 should be 10-11.**
- **D3 challenge:** "Free, but only technically." Valid. MarineCadastre has poor Indian Ocean coverage. MarineTraffic free tier is heavily rate-limited. Without Platts pricing data, the procurement optimization loses credibility. IEA detailed data requires subscription. **Suggests D3 should be 10-11.**
- **D4 challenge:** "The hardest part is domain expertise, not code." Valid. Making executable procurement recommendations requires knowledge of refinery crude slates, tanker availability, port infrastructure, contract structures, and energy economics. A team without this expertise will produce naive outputs. **D4=11 is already reasonable; no further adjustment needed.**
- **D5 challenge:** "Pattern is universal." Partial valid. The multi-source fusion → risk scoring → simulation → recommendation pattern is generic. However, the specific inputs (Indian SPR sites, Indian refinery crude slates, Indian Ocean AIS, Strait of Hormuz dependency) and regulatory context (Ministry of Petroleum) make this genuinely India-specific. **D5=18 is defensible.**

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 15 | 14 | Devil's advocate: most cited prior art is theoretical/conceptual, not operational systems |
| D2 | 12 | 11 | Devil's advocate: GDELT clients are thin wrappers; PhantomTide not a buildable lib; DT repos are empty |
| D3 | 12 | 11 | Devil's advocate: free AIS has Indian Ocean gaps; no Platts = degraded procurement optimization |
| D4 | 11 | 11 | — Already validated. Integration complexity is real but well-captured. |
| D5 | 18 | 18 | — India-specific energy security context is genuine and defensible |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| **14** | **11** | **11** | **11** | **18** | **65/100** |

Research: 12.0 | Build: 11 | ET: 18

## Verdict

🟡 **Adjusted** — Scores adjusted down by 3 points after devil's advocate review. The strongest signal remains ET relevance (18/20), which is genuinely unique to India's energy security context. The research base is solid but mostly theoretical. Data and code are scattered. Best suited for a team with energy economics or supply chain background who can build a compelling historical-scenario demo (e.g., 2025 Hormuz crisis backtest). If the team has domain expertise, this is the strongest candidate so far.
