### PS-04: AI Intelligence Platform for Data Centre EPC Project Delivery

**PS Description (from ET):**

> Build an AI-powered EPC Project Intelligence platform for data centre construction that unifies project documents, specifications, schedules, procurement data, and quality records into a living intelligence layer — enabling proactive schedule management, automated compliance and quality checking, and real-time commissioning support across the full project lifecycle.

**Core Technical Challenge:**

- Build a multi-agent system that ingests heterogeneous EPC project data (specifications, schedules, submittals, RFIs, test records, BIM) and delivers RAG-powered compliance checking, predictive schedule risk analysis, supply chain tracking, and commissioning QA — all within a unified project intelligence layer requiring deep domain knowledge of data centre construction standards (TIA-942, Uptime Institute).

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 12/20 | Construction schedule risk prediction is an active research area with papers on ML methods (Gondia et al. 2021, AbdElMottaleb 2025, Arshad 2026 on AI for mega EPC projects). RAG for construction/AEC documents is emerging (AEC-RAG systems, 2025-2026). Data centre commissioning with AI is very new — Build.inc articles (2026) document AI for test script generation (40-60% drafting time reduction), AI for punch list automation and photo-based defect detection. SGS launched digital commissioning services (2026). TIA DCE 9000 quality standard for data centres is in active drafting (target Sep 2026). However, no operational "EPC intelligence platform" for data centres exists in published form. |
| D2: Open Source | 12/20 | MeridianIQ (open-source schedule intelligence, implements AACE RP 29R-03, DCMA 14-Point, Monte Carlo risk, ML delay prediction — Apache license, active development). AEC-RAG-System (MIT, production-grade GraphRAG for AEC with CAD/PDF parsing, version tracking, impact analysis). certAIn (MIT, LLM + Monte Carlo project risk forecasting). BuildSense (Indian construction market focus, Streamlit, FastAPI). Multiple RAG repos for construction documents (construction-rag-doc-copilot, AECAgent-RAG, buildcore-rag). Lineo-PM (Apache 2.0, Monte Carlo schedule simulation). Most repos are early-stage (<50 stars, single contributor). No single repo integrates all 5 sub-systems (schedule, specs, supply chain, commissioning, RAG). |
| D3: Data | 10/20 | TIA-942-C standard white paper is publicly available (TIA, 2024). Uptime Institute Tier standards are publicly summarised. Construction datasets exist on Kaggle (Construction Project Management dataset with schedule/risk data). Public BIM datasets available from IFC repositories. However, detailed EPC project data (real schedules, procurement logs, RFI archives, commissioning test records) is confidential and proprietary. TIA/Uptime full standards are behind paywalls. No public dataset exists for "data centre EPC project data" specifically. Synthetic data generation is feasible but adds effort. |
| D4: Complexity | 12/20 | RAG pipeline is well-understood (LangChain, LlamaIndex, ChromaDB) — moderate engineering. Schedule risk prediction (Monte Carlo + ML) is established methodology. CV for drawing/submittal review requires GPU and domain-specific training. The main challenge is integration: 5 distinct sub-systems (compliance, schedule, supply chain, commissioning, RAG) each require their own pipeline. Multi-agent orchestration is non-trivial. Standards knowledge (TIA-942, BICSI, ASHRAE) is essential. Demo feasible with synthetic data and public standards. |
| D5: ET Relevance | 16/20 | Directly tied to India's data centre boom: 900MW → 2,700MW by 2027 ($15B+ capital deployment). 67% of APAC EPC projects have >10% schedule overruns (Turner & Townsend 2024). India positioning as AI infrastructure hub. JLL India Data Centre Report 2025 provides market context. Core ET coverage domain: industrial infrastructure, construction economy, digital transformation. TIA-942 is a global standard but the problem is anchored in India's specific DC ecosystem (local contractors, state permits, Indian hyperscaler investments). Highly timely given 2025-2026 AI infrastructure buildout. |
| **TOTAL** | **62/100** | |

### Composites

- Research: 11.3 | Build: 12 | ET: 16

### Risk Factors

- Real EPC project data is confidential — prototype must use synthetic or sanitised data
- TIA/Uptime Institute standards may require purchased access for full text
- Data centre EPC domain expertise (Tier III/IV, MEP, commissioning sequences) is essential
- Five sub-systems is broad scope — likely need to prioritise 1-2 for hackathon prototype
- Evaluation requires domain experts to rate compliance/schedule prediction quality
- Most open-source tools are early-stage and single-contributor

### Verdict

🟡 Moderate — Strong ET relevance tied to India's data centre construction boom, with emerging open-source building blocks for schedule intelligence (MeridianIQ) and AEC document RAG (AEC-RAG-System). The main risks are data confidentiality, broad scope (5 sub-systems), and need for domain expertise. Best approached by focusing on one sub-system (e.g., specification compliance RAG + schedule risk) and demonstrating integration potential. Feasible for a team with construction tech or document AI experience.
