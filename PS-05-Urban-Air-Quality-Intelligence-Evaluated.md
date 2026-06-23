### PS-05: AI-Powered Urban Air Quality Intelligence for Smart City Intervention

**PS Description (from ET):**

> Build an AI-powered Urban Air Quality Intelligence platform that fuses monitoring station data, satellite imagery, mobility feeds, meteorological forecasts, and geospatial land use layers to move from reactive monitoring to proactive, evidence-based intervention — giving city administrators the tools to reduce pollution at source rather than just measure it.

**Core Technical Challenge:**

- Fuse heterogeneous data (CAAQMS ground stations, Sentinel-5P TROPOMI, MODIS AOD, IMD meteorology, traffic, land use) into a unified geospatial air quality intelligence system delivering hyperlocal AQI forecasting, source attribution, and enforcement prioritization for Indian cities.

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 16/20 | AQI forecasting is a **mature field** with hundreds of papers (CNN-LSTM hybrid, Transformer-BiLSTM, GNN-based spatiotemporal models, FuXi-Air, MAST-Net 2025, AirTrace-SA 2025). Multi-modal fusion (satellite + ground + met) is well-documented (STMFNet 2025, physics-informed CNN-LSTM 2026). Source attribution has emerging hybrid approaches (AirTrace-SA, EGUsphere 2025). What is **novel** is the specific integration of enforcement intelligence and operational dashboard — no single system combines all 3 capabilities in an Indian-city context. |
| D2: Open Source | 14/20 | AirFormer (163 stars, AAAI-23) for nationwide AQI forecasting. Multiple Sentinel-5P tools (s5p-tools 62 stars, sentinel5dl pip-installable, Sentinel5P-automated, pys5p). AQI forecasting repos exist (AQI-Hybrid-Model 2025, TopoFlow MIT 2026, BAQ Bangkok forecasting). Google Earth Engine (GEE) has Sentinel-5P/MODIS collections accessible via Python. **Gap:** No single open-source "urban air quality intelligence platform" integrating forecasting + attribution + enforcement. Heavy glue code required. |
| D3: Data | 15/20 | **Excellent primary data:** CPCB CAAQMS (public, 900+ stations via OpenAQ API), Sentinel-5P TROPOMI (free, daily 3.5-7km via Copernicus), MODIS AOD (free, daily via NASA EarthData), IMD weather (public). **Gaps:** CPCB API reliability varies by city. Traffic data is partially public (Google Maps has rate limits). Emission inventories for verification are limited. Station density is ~1 per 200 sq km in most cities — sparse for hyperlocal 1km grid. All core satellite + ground data is free and well-documented. |
| D4: Complexity | 12/20 | **Data ingestion** is straightforward (CPCB API, Copernicus Data Space, GEE). **Preprocessing** requires multi-source fusion — aligning satellite (3.5-7km), ground (point), and met (grid) data at different resolutions — non-trivial. **Core algorithm** (CNN-LSTM/GNN for forecasting) is well-documented. **Source attribution** is the hardest sub-problem — requires atmospheric dispersion modeling or advanced ML (AirTrace-SA approach). **Training** needs GPU. **Evaluation** has clear metrics (RMSE, attribution accuracy vs inventories) but ground-truth inventories are limited. **Demo** achievable as an interactive dashboard (Streamlit) with visual forecasts and source attribution maps. |
| D5: ET Relevance | 17/20 | Directly about India's urban air quality crisis (1.67M premature deaths/year, 24 of 50 most polluted cities are Tier 1/2). Uses India-specific data sources: CPCB CAAQMS network, IMD weather, NCAP framework, Indian city ward boundaries. Requires multi-language citizen alerts (Kannada, Tamil, Hindi, Bengali). Core ET coverage domain: environment, public health, smart cities, urban governance. Strong India context — would not make sense for a generic hackathon. |
| **TOTAL** | **74/100** | |

### Composites

- Research: 15.0 | Build: 12 | ET: 17

### Risk Factors

- Source attribution is the hardest sub-component — AirTrace-SA and similar methods are from 2025 (very recent) and may not generalize to Indian cities
- Traffic data access is gated (Google Maps API rate limits) — may need proxy data or synthetic generation
- CPCB data API reliability varies — station downtime and data gaps are common
- Atmospheric dispersion physics expertise needed for rigorous source attribution
- Station density is too sparse for true 1km grid forecasting — must rely heavily on satellite interpolation
- Multiple sub-components (forecasting, attribution, enforcement, citizen alerts) risk scope creep — MVP focus critical

### Verdict

🟢 Strong — Excellent prior art and data availability for the core AQI forecasting task. Source attribution is the main challenge but recent 2025 papers (AirTrace-SA) show it's tractable. Strong ET relevance with clear India-specific use. Best suited as a multi-agent system with separate forecasting, attribution, and enforcement agents. The most buildable high-scoring PS among the set.
