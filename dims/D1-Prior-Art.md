# D1: Prior Art Availability (20 pts)

> **Core Question:** Has another organization, research lab, or company already solved this problem — or something close enough that we can learn from it?

This dimension measures how much existing work exists in the world. The more prior art, the less risk. A high score means we're standing on shoulders; a low score means we're the shoulders.

---

## What We're Looking For

Evidence that this problem has been tackled before, in any of these forms:

| Evidence Type | Weight | Example |
| --------------------------------------- | ---------- | ------------------------------------------------------------ |
| Operational system at another organization | Very High | NOAA's operational air quality forecast system |
| Published paper with clear methodology | High | CVPR paper on GAN-based cloud removal for Sentinel-2 |
| Conference talk / workshop presentation | Medium | Talk at ESA Φ-lab week on cross-modal retrieval |
| Government/industry technical report | Medium | CPCB technical report on air quality monitoring |
| Blog post / tutorial with approach | Low-Medium | Towards Data Science article on satellite image segmentation |
| Graduate thesis / university project | Low | Masters thesis on lunar radar processing |
| Patent filing | Low | Indicates someone thought it was worth protecting |

---

## Where to Search

### Tier 1: Research Repositories (Highest Signal)

| Source | Search Approach |
| ----------------------------------------------- | ------------------------------------------------------------------------- |
| **arXiv** | `arxiv.org` — `cs.AI`, `cs.CV`, `cs.LG`, `cs.CR`, `cs.SE` |
| **Google Scholar** | `scholar.google.com` — catch-all; use "cited by" to trace influence |
| **Semantic Scholar** | `semanticscholar.org` — AI-powered search, citation graph |
| **IEEE Xplore** | `ieeexplore.ieee.org` — industrial AI, cybersecurity, signal processing |
| **ScienceDirect / Springer** | `sciencedirect.com`, `link.springer.com` — broad scientific coverage |
| **Papers With Code** | `paperswithcode.com` — papers with linked implementations |
| **ACL Anthology** | `aclanthology.org` — NLP research |
| **Government Tech Reports** | NIST, CPCB, CERT-In, NCRB publications |

### Tier 2: Domain-Specific Repositories

| Source | URL | Best For |
| ---------------------------- | ---------------------------------------- | --------------------------------------------------------- |
| **IEEE Xplore** | `ieeexplore.ieee.org` | Industrial AI, cybersecurity, signal processing |
| **ACM Digital Library** | `dl.acm.org` | Computing, software engineering, AI |
| **Papers With Code** | `paperswithcode.com` | Benchmarks, SOTA, linked implementations |
| **Google Scholar** | `scholar.google.com` | Catch-all; use "cited by" to trace influence |
| **Scopus / Web of Science** | Institutional access required | Systematic literature reviews |
| **SSRN** | `ssrn.com` | Preprints in business, economics, policy |

### Tier 3: Industry & Government Reports

| Source | Search Approach |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **NIST** | `nist.gov` — cybersecurity frameworks, AI standards, technical reports |
| **CERT-In** | `cert-in.org.in` — cybersecurity advisories, incident reports |
| **CPCB** | `cpcb.nic.in` — air quality data, reports, standards |
| **McKinsey / BCG / Deloitte** | Industry reports on AI, supply chain, industrial digitalization |
| **Government Open Data** | `data.gov.in` — Indian government open datasets |
| **World Bank / IEA** | Energy, climate, supply chain datasets and reports |

### Tier 4: Competition & Benchmark Sites

| Source | What It Tells You |
| -------------------- | ---------------------------------------------------- |
| **Papers With Code** | If it's here with a leaderboard, the field is mature |
| **Kaggle** | Past competitions = working solutions + discussion |
| **Grand Challenge** | Medical imaging, but methodology transfers |
| **CodaLab** | Many academic competitions hosted here |

---

## How to Search (Systematic Strategy)

### Step 1: Extract Search Tokens from the PS

From the PS title and description, pull out:

- **Domain keywords**: e.g., "industrial safety", "supply chain resilience", "air quality"
- **Technical keywords**: e.g., "anomaly detection", "predictive maintenance", "RAG", "knowledge graph"
- **Data source names**: e.g., "SCADA", "CCTV", "AIS", "CAAQMS", "IoT sensors"
- **Equivalent industry terms**: e.g., "safety intelligence" → "process safety management", "predictive analytics"

### Step 2: Build Search Queries

For each combination of [domain] + [industry] + [technique]:

```
# Example: PS-01 Industrial Safety
("industrial safety" OR "process safety") AND ("AI" OR "anomaly detection") AND ("sensor data" OR "IoT")
site:ieee.org "industrial safety" AI
site:arxiv.org "safety intelligence" deep learning
"predictive maintenance" safety dataset github
```

**Search query template:**

```bash
# General search
("[core technique 1]" OR "[core technique 2]") AND ("[domain]" OR "[alternate domain name]")

# Domain-specific
site:[domain-specific source] "[core technique]" "[domain]"

# Code-tethered (indicates implementation exists)
"[problem]" "[technique]" (github OR "open source" OR repository)
```

### Step 3: Trace the Citation Graph

Once you find one relevant paper:

1. **Backward:** Check its references — what prior work does it cite?
2. **Forward:** Use Google Scholar "cited by" — who built on this?
3. **Lateral:** "Related articles" on Google Scholar / Semantic Scholar
4. **Code search:** Does the paper mention a GitHub repo? Search the lead author on GitHub.

### Step 4: Cast the Net Wider

If direct hits are sparse, search for:

- The **underlying problem** without the domain (e.g., "image inpainting" rather than "satellite cloud removal")
- The **inverse problem** (e.g., if searching for "ice detection radar", also search "subsurface water mapping GPR")
- **Adjacent domains** (e.g., medical imaging denoising techniques transfer to satellite denoising)

---

## Scoring Guide for D1

### 18–20: Operational / Heavily Published

Multiple space agencies or major labs have production systems, or the problem has been studied for decades with clear, reproducible approaches.

**Indicators:**

- 3+ papers from different agencies solving the same problem
- At least one operational system (e.g., NOAA SWPC, ESA Sen4CAP, NASA Landsat processing)
- Dedicated conference sessions or workshops on this exact topic
- Papers With Code has a leaderboard for this task

**Example:** Cloud removal for optical satellite imagery — ESA (Sen2Cor), NASA (MCD43), JAXA (ALOS SAR-optical fusion), multiple GAN architectures published.

### 14–17: Well-Studied

Significant research exists with multiple published approaches. No single "solved" system, but the building blocks are clear.

**Indicators:**

- 5-15 papers from credible groups
- Clear naming conventions for the problem (people agree on what it's called)
- Survey papers exist that compare approaches
- At least one PhD thesis or major grant on the topic

**Example:** ML-based solar flare prediction — multiple papers from different solar physics groups, Kaggle competition, but no single operational system.

### 10–13: Emerging

Some prior work exists but it's early-stage. Approaches are diverse (no consensus on best method).

**Indicators:**

- 2-5 papers, mostly from a single group or two
- Problem definition is still evolving (people describe it differently)
- Mostly conference papers, few journal publications
- Some theoretical contributions but limited empirical validation

**Example:** Lunar subsurface ice characterization from SAR — active research area but methods are still being established.

### 6–9: Theoretical / Speculative

Limited to theoretical papers or proposals. Very little implementation.

**Indicators:**

- 1-2 papers, possibly white papers or concept studies
- No working implementations described
- Problem may be described differently by different authors
- Mostly from the proposing organization's own researchers

### 0–5: Novel / First-of-its-Kind

Nothing found. This problem appears to be genuinely new.

**Indicators:**

- No papers found after exhaustive search
- Problem statement uses novel terminology not found in literature
- Appears to be domain-specific with no equivalent elsewhere

---

## Red Flags

- **Only one research group has published on this** — fragile foundation
- **All prior art is from the same group that proposed the PS** — circular, no external validation
- **Papers are all >10 years old with no recent follow-ups** — likely a dead end
- **Problem has different names in different communities** — harder to aggregate knowledge, but also means it's cross-disciplinary
- **All prior art is behind paywalls** — academic access helps but slows research

## Green Flags 🟢

- **Operational system with public documentation** — gold standard
- **"State of the Art" or "Benchmark" paper published within last 3 years** — active field
- **Dedicated competition or challenge on this topic** — indicates community maturity
- **Open-access survey paper** — someone already did the literature review for you
- **Cross-industry collaboration** (e.g., academic-industry partnership) — broad interest

---

## Quick Search Reference

| PS Domain | Key Search Terms | Best Sources to Search |
| --------------------------- | ----------------------------------------------------------- | -------------------------------- |
| Industrial Safety | "process safety", "anomaly detection", "hazard identification" | IEEE, arXiv, OSHA, DGFASLI |
| Energy Supply Chain | "supply chain resilience", "geopolitical risk", "disruption" | IEA, EIA, arXiv, S&P Global |
| EV / Manufacturing | "battery degradation", "quality management", "supply chain" | BNEF, IEEE, arXiv, SAE |
| Data Centre EPC | "project delivery", "commissioning", "quality compliance" | JLL, Turner & Townsend, IEEE |
| Air Quality | "AQI forecasting", "source attribution", "air pollution" | CPCB, OpenAQ, NASA, ESA |
| Public Safety / Fraud | "fraud detection", "counterfeit", "cybercrime", "deepfake" | IEEE, ACM, arXiv, MHA |
| Cybersecurity | "anomaly detection", "threat intelligence", "APT", "MITRE" | MITRE, CERT-In, IEEE, arXiv |
| Industrial Knowledge | "knowledge graph", "RAG", "document intelligence" | arXiv, IEEE, ACM, NASSCOM |
