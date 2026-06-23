# PS-05 Verification Report

## Source Integrity

| Source | Type | Status | Issue |
| ---------- | ------------------ | -------- | -------------------- |
| AirFormer (yoshall/AirFormer) | Repo | ✅ | 163 stars, AAAI-23, active |
| s5p-tools (bilelomrani1/s5p-tools) | Repo | ⚠️ | 62 stars, MIT, but repo is **ARCHIVED** (read-only). Scripts still functional but no longer maintained. |
| sentinel5dl (emissions-api/sentinel5dl) | Repo | ✅ | 12 stars, MIT, pip-installable, stable. Last release v1.2. |
| OpenAQ API | API | ✅ | 66 stars, MIT, active, publicly documented |
| CPCB CAAQMS | Data Portal | ✅ | Accessible via data.gov.in with free API key registration |
| Sentinel-5P (Copernicus) | Data | ✅ | Free and open, accessible via Copernicus Data Space and GEE |
| MODIS (NASA EarthData) | Data | ✅ | Free, requires free EarthData login |
| IMD Weather | Data | ⚠️ | Public but API reliability and documentation quality varies by region |

## Cross-Dimension Consistency

| Pair | Status | Note |
| ----- | -------- | ---- |
| D1↔D2 | ✅ Consistent | Strong prior art (16) and solid building blocks (14) align. D2 slightly lower because no integrated platform exists. |
| D1↔D3 | ✅ Consistent | Prior art relies on the same public data sources cited in D3 (CPCB, Sentinel-5P, MODIS). |
| D2↔D4 | ✅ Consistent | Individual repos exist (14) but integration effort makes D4 moderate (12). Tension explainable: multi-source fusion is the hard part. |
| D5↔D1 | ✅ Consistent | Global AQI forecasting has lots of prior art (16), but India-specific deployment context (CPCB, NCAP, multi-language) justifies high D5 (17). |
| D3↔D4 | ✅ Consistent | Data is accessible (15) but fusing multi-resolution satellite + ground + met data is complex (12). |

## Bias Audit

- **Optimism flags:** None. Scores are grounded in verified evidence. "Most buildable high-scoring PS" is a comparative claim supported by data.
- **Pessimism flags:** None. Source attribution is correctly flagged as the hardest sub-component.
- **Calibration:** D1–D3 avg = 15.0, D4 = 12.0. Gap is 3 pts — acceptable and explainable by integration complexity. No correction needed.

## Devil's Advocate

- **D1 challenge:** "AQI forecasting is mature, but source attribution + enforcement dashboard is novel." — Already acknowledged in the score (16, not 18-20). No adjustment needed.
- **D2 challenge:** "s5p-tools is archived. Does it still work?" — Confirmed functional (scripts use stable APIs). sentinel5dl is pip-installable and active. No score change.
- **D3 challenge:** "CPCB API reliability varies; traffic data is gated." — Already noted in evaluation. Score 15 appropriately reflects these gaps.
- **D4 challenge:** "No single team can build forecasting + attribution + enforcement + citizen alerts." — Valid concern. Risk factors already flag scope creep and recommend MVP focus.
- **D5 challenge:** "Does the solution really need India-specific data, or could open global data work?" — CPCB and IMD are the primary ground data sources; they are India-specific. Score 17 justified.

## Adjustments

| Dimension | Original | Adjusted | Reason |
| --------- | -------- | -------- | --------------- |
| D1 | 16 | 16 | ✅ Confirmed — prior art is well-studied |
| D2 | 14 | 14 | ✅ Confirmed — s5p-tools is archived but functional; AirFormer and sentinel5dl are active |
| D3 | 15 | 15 | ✅ Confirmed — core data is free and public |
| D4 | 12 | 12 | ✅ Confirmed — complexity assessment is accurate |
| D5 | 17 | 17 | ✅ Confirmed — strong India specificity |

## Final Verified Scores

| D1 | D2 | D3 | D4 | D5 | **Total** |
| :-: | :-: | :-: | :-: | :-: | :--------: |
| 16 | 14 | 15 | 12 | 17 | **74/100** |

Research: 15.0 | Build: 12 | ET: 17

## Verdict

✅ **Confirmed** — All scores verified. No material adjustments needed. s5p-tools being archived is noted but does not affect the score since functional alternatives exist (sentinel5dl, GEE, direct Copernicus API).
