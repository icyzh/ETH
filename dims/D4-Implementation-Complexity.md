# D4: Implementation Complexity (20 pts)

> **Core Question:** Given the prior art (D1), code (D2), and data (D3) — how hard is it to actually build a working prototype? Are the building blocks plug-and-play, or does this require novel research?

This dimension synthesizes D1–D3 into a practical buildability assessment. It answers: "Can we ship something that works?" A high score means the path from idea to working prototype is short and well-paved.

---

## What We're Measuring

Implementation complexity is not just about code difficulty — it's about the full engineering stack:

| Factor | What to Assess |
| ------------------------ | ----------------------------------------------------------------- |
| **Algorithm Maturity** | Is the core algorithm well-understood with clear pseudo-code? |
| **Integration Surface** | How many different systems/components need to talk to each other? |
| **Compute Requirements** | Laptop, cloud GPU, or HPC cluster? |
| **Dependency Chain** | How many libraries, and how well do they play together? |
| **Uncertainty** | What don't we know? What could go wrong? |
| **Demo-ability** | Can we show something visually compelling to judges? |

---

## The Build Pipeline Assessment

For each PS, mentally walk through the full pipeline and score each stage:

### Stage 1: Data Ingestion

```
How hard is it to get data into your training/inference pipeline?
- Just point a library at a URL → Easy (18-20)
- Download from portal, standard format → Medium (14-17)
- Multi-source fusion, reprojection, resampling → Hard (10-13)
- Proprietary format, custom reader needed → Very Hard (6-9)
- Data doesn't exist, must simulate → Extremely Hard (0-5)
```

### Stage 2: Preprocessing

```
What needs to happen before the data is ML-ready?
- Already preprocessed, just normalize → Easy
- Standard geospatial ops (reproject, clip, resample) → Medium
- Complex calibration (radiometric, atmospheric correction) → Hard
- Novel preprocessing pipeline → Very Hard
```

### Stage 3: Core Algorithm

```
How complex is the main algorithm?
- Import pretrained model, run inference → Easy
- Fine-tune existing architecture on new data → Medium
- Adapt architecture from adjacent domain → Hard
- Design novel architecture from scratch → Very Hard
```

### Stage 4: Training (if applicable)

```
What does training require?
- CPU, < 1 hour → Easy
- Single GPU, < 12 hours → Medium
- Multi-GPU, > 24 hours → Hard
- HPC cluster, hyperparameter search → Very Hard
```

### Stage 5: Evaluation

```
How do we know if it works?
- Standard benchmark with public leaderboard → Easy
- Clear metrics, comparison baselines exist → Medium
- Need to create evaluation framework from scratch → Hard
- Success is ill-defined, subjective assessment → Very Hard
```

### Stage 6: Demo / Deployment

```
How do we present it?
- Static visualization (matplotlib, folium) → Easy
- Interactive web dashboard (Streamlit, Gradio) → Medium
- Real-time inference on live data → Hard
- Multi-component system with backend → Very Hard
```

---

## Scoring Guide for D4

Score D4 by assessing the **whole pipeline** holistically, not just the algorithm. Use the stage assessments above as input, then apply this rubric:

### 18–20: Assembly Required (Not Invention)

The pipeline is well-understood end to end. You're composing existing components with minimal glue code. The main challenge is integration, not innovation.

**Indicators:**

- Core algorithm: import library → 10 lines of Python → working
- Preprocessing: standard pipeline, reference implementation exists
- Training: optional — pretrained model available, or fine-tuning is lightweight
- Evaluation: standard metrics, benchmark exists
- Compute: laptop or single GPU, runs in < 4 hours
- Demo: can build an interactive visualization in Streamlit in 2 hours
- **Risk level:** Very Low — this will definitely work

**Example:**

- PS-07 (Exoplanet detection): `lightkurve` loads data, `exoplanet` runs transit search, done
- PS-10 (IR colorization): download pretrained Pix2Pix, run inference, before/after demo

### 14–17: Known Path With Moderate Work

The approach is clear but requires meaningful integration work. You'll need to write real code, but you're not researching — you're engineering.

**Indicators:**

- Core algorithm: known architecture, needs adaptation and training
- Preprocessing: standard but non-trivial (e.g., SAR calibration)
- Training: single GPU, 4-12 hours, straightforward hyperparameters
- Evaluation: clear metrics, need to assemble test set
- Compute: consumer GPU sufficient
- **Risk level:** Low — unlikely to fail, but may take all available time

**Example:**

- PS-03 (AQI from satellite): TROPOMI data pipeline + XGBoost/LSTM → deploy as dashboard
- PS-06 (Crop classification): Sentinel-2 pipeline → U-Net segmentation → irrigation map

### 10–13: Challenging But Feasible

The approach is plausible but involves significant technical challenges. You need domain expertise or substantial debugging time.

**Indicators:**

- Core algorithm: needs non-trivial adaptation from adjacent domain
- Preprocessing: complex, multi-source, error-prone
- Training: multi-GPU or long training times, tricky convergence
- Evaluation: need to create ground truth or validation framework
- At least one "unknown unknown" in the pipeline
- **Risk level:** Medium — could fail if the hard part turns out to be harder than expected

**Example:**

- PS-09 (Wavefront reconstruction): AO simulation with AOtools → ML model → validate on synthetic data. ML-AO intersection is niche.
- PS-12 (Temporal satellite enhancement): RIFE on satellite → need to handle seasonal change, not just motion. Non-trivial adaptation.

### 6–9: Research-Heavy

The problem requires novel research or substantial original development. Building a working prototype would require breakthroughs, not just engineering.

**Indicators:**

- Core algorithm: no clear approach, you'd be inventing
- Multiple components are poorly understood
- Requires expertise from multiple domains (rare combination)
- No reference implementation for key components
- Training: unknown if approach will converge
- **Risk level:** High — significant chance of no working prototype

**Example:**

- PS-05 (Climate Digital Twin): even a "mini" twin requires physics + ML + massive data integration

### 0–5: Unsolved Research Problem

This is a PhD thesis, not a prototype. The core technical challenge has no known solution.

**Indicators:**

- The problem statement is essentially: "invent something new"
- No paper, repo, or even clear approach exists
- Would require fundamental advances in the field
- Even major labs/agencies haven't solved this
- **Risk level:** Extremely High — almost certainly won't produce a working prototype

---

## The "Unknown Unknowns" Assessment

Beyond the known challenges, ask these questions to surface hidden complexity:

1. **Data × Algorithm mismatch:** Does the available data actually support the proposed approach? (e.g., SAR for crop type — works but requires expertise)
2. **Scale cliff:** Does the approach work on a small test case but break at real scale? (e.g., global model from local training)
3. **Domain gap:** Does the prior art come from a different domain where assumptions don't transfer? (e.g., natural image GANs on multispectral satellite data)
4. **Temporal trap:** Does the approach need historical data that doesn't exist, or future data for validation?
5. **Expertise requirement:** Does this require knowledge no one on the team has? (e.g., radar signal processing, orbital mechanics)
6. **Integration hell:** Do 3 different libraries use incompatible versions of the same dependency?

---

## Red Flags

- **"This should work in theory"** — but nobody has shown it does
- **Papers exist but no working code** — implementation gap is real
- **"We'll figure out the details during the hackathon"** — famous last words
- **Core algorithm is from a paper published <6 months ago** — bleeding edge, unvetted
- **Requires >1 TB of data to train** — infrastructure problem
- **Dependencies that conflict** (e.g., library A needs PyTorch 1.x, B needs 2.x)
- **The PS is actually 3 separate problems** — scope explosion

## Green Flags 🟢

- **Step-by-step tutorial exists for the core pipeline** — proven path
- **Pretrained model on Hugging Face** — inference-only, skip training entirely
- **The approach is "boring but reliable"** — established method on established data
- **You can sketch the full pipeline on a whiteboard in 5 minutes** — understood
- **Reference implementation runs in a Colab notebook** — minimal setup
- **Gradio/Streamlit demo of a similar system exists** — proven demo-ability
- **A single person could build the core in a weekend** — right-sized for a team of 3-4

---

## Quick Complexity Scorecard

For each stage, assign 1 (easy) to 5 (hard). Average = complexity rating.

| Pipeline Stage | 1 (Trivial) | 2 (Easy) | 3 (Medium) | 4 (Hard) | 5 (Very Hard) |
| -------------- | ---------------- | -------------------- | -------------------------- | -------------------- | ----------------------- |
| Data Ingestion | API call | Download from portal | Multi-source fuse | Custom format parser | Simulate from scratch |
| Preprocessing | Already clean | Standard ops | Complex calibration | Novel pipeline | Unknown requirements |
| Core Algorithm | Pretrained model | Fine-tune existing | Adapt from adjacent domain | Modify architecture | Novel research |
| Training | Not needed | < 1 hr CPU | < 12 hr GPU | > 24 hr multi-GPU | Unknown feasibility |
| Evaluation | Benchmark exists | Clear metrics | Need test set | Need ground truth | Subjective only |
| Demo | Static plot | Interactive viz | Real-time dashboard | Multi-service system | Requires specialized HW |

**Scoring:**

- Average 1.0–1.5 → D4 = 18-20
- Average 1.6–2.5 → D4 = 14-17
- Average 2.6–3.5 → D4 = 10-13
- Average 3.6–4.5 → D4 = 6-9
- Average 4.6–5.0 → D4 = 0-5
