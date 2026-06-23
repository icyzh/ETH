### PS-06: AI for Digital Public Safety: Defeating Counterfeiting, Fraud & Digital Arrest Scams

**PS Description (from ET):**

> Build an AI-powered Digital Public Safety Intelligence platform that equips law enforcement agencies, financial institutions, and citizens with proactive tools to detect, disrupt, and respond to digital fraud networks, counterfeit currency circulation, and organised scam operations — shifting from reactive case investigation to predictive threat neutralisation.

**Core Technical Challenge:**

- Combine three distinct AI capabilities into a single intelligence platform: (1) CV-based counterfeit currency detection on mobile/banking devices, (2) graph neural network analysis of transaction metadata to map fraud networks, and (3) real-time NLP/LLM-based detection of digital arrest scam patterns in calls/text — with near-zero false positive tolerance for citizen-facing tools.

---

### Dimension Scores

| Dimension | Score | Evidence / Key Finding |
| ------------------ | :--------: | --------------------------------------- |
| D1: Prior Art | 15/20 | **Counterfeit detection:** Very well-studied — multiple papers on CNN/Xception/YOLO-based Indian currency detection (ICISD 2025, ICAIN 2024, Evergreen 2025) achieving 97-99% accuracy. UV-feature detection papers exist (YOLO-NAS 2025). **Fraud network GNN:** Highly active field — PMP (ICLR 2024), FraudGT (ICAIF 2024), comprehensive GNN surveys (arXiv 2024). **Digital arrest scam detection:** Emerging — Kavalan system (2025), VoxGuard multimodal detection, defense-optimized BERT (Telecommunications Systems 2025), LLM-based real-time detection (arXiv 2025). Each sub-problem individually has strong prior art; the **integrated platform** is novel. |
| D2: Open Source | 14/20 | **Counterfeit:** Multiple Indian currency detection repos (CurrencyGuard 8 stars MIT, Fake-Currency-Checker 8 stars MIT, MobileNetV2-based 99% acc). **Fraud GNN:** PMP official PyTorch code (ICLR 2024), FraudGT code (MIT 2024), AntiFraud framework (AI4Risk/antifraud), CryptoGraph, FinSentry. **Scam detection:** Kavalan browser extension (real-time digital arrest detection), VoxGuard, Digital Arrest Triage app (MIT). Each component has solid open-source building blocks. **Gap:** No integrated platform combining all three — heavy integration work needed. |
| D3: Data | 9/20 | **Counterfeit:** Real FICN datasets are **restricted to RBI/law enforcement** — cannot access. Public datasets exist (self-captured Indian note images, Colombian/Thai currency datasets) but limited in scale and not representative of high-quality fakes. **Fraud graphs:** Academic datasets exist (Yelp, Amazon, T-Finance, IEEE-CIS) but are transaction-based, not Indian-specific. **Scam detection:** Public scam call datasets are limited — some research datasets exist (IEEE fraud detection). Most data must be synthetically generated. **Core issue:** Restricted data for all 3 sub-problems — heavy reliance on synthetic/self-collected data. |
| D4: Complexity | 11/20 | **Three distinct sub-problems** — each individually tractable, but integrating them into one platform is significant. **Counterfeit CV:** Well-understood (transfer learning on MobileNetV2/EfficientNet), deployable via TensorFlow Lite on mobile. **Fraud GNN:** Moderate complexity — graph construction from transaction data requires domain knowledge. **Scam detection:** Real-time call analysis is hardest — requires audio streaming, NLP, low latency. **Evaluation:** Counterfeit accuracy is measurable but digital arrest precision/recall in real-world settings is hard to benchmark. Near-zero false positive requirement for citizen tools adds significant engineering burden. |
| D5: ET Relevance | 17/20 | Deeply India-specific: Indian currency design (Rs 200, Rs 500 security features), Indian phone numbering plan, MHA/CERT-In reporting structures, Hindi + 12 regional languages. Digital arrest scams are a uniquely Indian phenomenon (Rs 1,776 crore defrauded in 2024, 1.14M cybercrime complaints). References specific Indian institutions (MHA, NCRB, RBI). Core ET coverage: cybersecurity, public safety, financial fraud, policy. Would be substantially different for any other country. |
| **TOTAL** | **66/100** | |

### Composites

- Research: 12.7 | Build: 11 | ET: 17

### Risk Factors

- **Data is the critical bottleneck** — real FICN datasets are law-enforcement restricted; must generate synthetic fakes using known security features (watermark, security thread, microprint), which may not match real circulation quality
- Three sub-problems = scope risk — MVP must pick ONE (likely counterfeit detection) and deprioritize the others
- Near-zero false positive tolerance is technically very demanding for citizen-facing scam detection
- Scam call/scam audio data is difficult to source — must rely on synthetic generation or public scam call archives which may not represent Indian digital arrest patterns
- Legal admissibility of AI-generated evidence packages adds non-trivial complexity
- Domain expertise in counterfeit security features, telecom fraud, and graph analytics required across different team members

### Verdict

🟡 Moderate — Technically interesting with strong ET relevance and solid prior art for each sub-problem independently. The data restriction is the most serious risk — especially the lack of real FICN datasets and real scam call recordings. Best approached by focusing on a single sub-problem (e.g., counterfeit currency CV alone, or digital arrest LLM detection alone) as an MVP rather than attempting the full integrated platform. Each individual agent would score higher on D2/D3/D4; the integration scope drags the composite score down.
