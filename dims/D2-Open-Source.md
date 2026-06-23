# D2: Open Source Code Availability (20 pts)

> **Core Question:** Can we find working code on GitHub, Hugging Face, or elsewhere that we can fork, adapt, and build upon — or are we writing everything from scratch?

This dimension measures the availability of existing software implementations. The more code we can reuse, the faster we can build a credible prototype. A high score means we're composing, not creating.

---

## What We're Looking For

Code artifacts ranked by how directly useful they are:

| Artifact Type | Value | Example |
| ---------------------------------------- | ---------- | --------------------------------------------------------------------- |
| Full implementation of this exact PS | Priceless | GitHub repo that does satellite cloud removal with pretrained weights |
| Implementation of core algorithm | Very High | GAN repo that we can adapt from faces→satellite imagery |
| Library/framework for this domain | High | `sunpy` for solar data, `lightkurve` for exoplanet light curves |
| Pretrained model on similar data | High | RemoteCLIP pretrained on satellite imagery |
| Tutorial/notebook for related task | Medium | Google Earth Engine tutorial for NDVI calculation |
| Data loader / preprocessing script | Medium | Script that reads and preprocesses Sentinel-2 SAFE format |
| Configuration / baseline training script | Low-Medium | Generic training loop we can adapt |

---

## Where to Search

### Tier 1: Code Hosts

| Platform | Search Strategy |
| ---------------- | ---------------------------------------------------------------------------------------------- |
| **GitHub** | Search by topic, org, and code. Use advanced search operators. |
| **Hugging Face** | Models, datasets, and Spaces (running demos). Filter by `image-segmentation`, `text-to-image`. |
| **GitLab** | Some organizations host internally — search `gitlab.com` + organization name. |
| **Bitbucket** | Less common but some academic groups use it. |
| **PyPI / npm** | Package registries — if there's a pip-installable library, it's well-packaged. |

### Tier 2: Key GitHub Organizations

Search these orgs directly — they host official and community code:

| Organization | GitHub | What You'll Find |
| -------------------------------- | ---------------------------------------- | -------------------------------------------- |
| **NASA** | `github.com/nasa` | Mission software, data processing, ML models |
| **NASA JPL** | `github.com/nasa-jpl` | Planetary science, radar processing |
| **NASA GSFC** | `github.com/nasa-gsfc` | Earth science, heliophysics |
| **ESA** | `github.com/esa` | Mission planning, data processing |
| **ESA Φ-lab** | `github.com/esa-philab` | AI for Earth observation |
| **JAXA** | `github.com/jaxa` | Satellite data tools |
| **USGS** | `github.com/usgs` | Landsat processing, EarthExplorer tools |
| **NOAA** | `github.com/noaa` | Weather models, space weather |
| **ECMWF** | `github.com/ecmwf` | Climate and weather data tools |
| **DLR** | `github.com/dlr-eoc` | SAR processing, geospatial |
| **Planet Labs** | `github.com/planetlabs` | Satellite imagery SDKs, data tools |
| **Maxar** | `github.com/maxar-analytics` | Geospatial ML, GBDX tools |
| **Microsoft Planetary Computer** | `github.com/microsoft/PlanetaryComputer` | Cloud-based geospatial analysis |

### Tier 3: Community & Academic Repos

| Source | How to Find |
| --------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Papers With Code** | Each SOTA paper has a "Code" link — direct to implementation |
| **Awesome Lists** | `github.com/topics/awesome` — search "awesome [domain]" e.g., "awesome remote sensing", "awesome satellite imagery" |
| **Kaggle Notebooks** | Competition solutions, exploratory analysis |
| **Colab Notebooks** | Search Google for `colab.research.google.com [topic]` |
| **Model Zoo** | PyTorch Hub, TensorFlow Hub, ONNX Model Zoo |
| **Zenodo / Figshare** | Research data repositories often include code |

### Tier 4: Domain-Specific Hubs

| Hub | URL | Domain |
| ----------------- | ------------------------------- | ----------------------------------------- |
| **Radiant MLHub** | `mlhub.earth` | Geospatial ML models and training data |
| **TorchGeo** | `github.com/microsoft/torchgeo` | PyTorch domain library for geospatial |
| **SunPy** | `sunpy.org` | Solar physics Python ecosystem |
| **Astropy** | `astropy.org` | Core astronomy Python library |
| **SpacePy** | `spacepy.github.io` | Space physics (radiation, magnetosphere) |
| **Pangeo** | `pangeo.io` | Big data geoscience |
| **OpenCV** | `opencv.org` | General computer vision, image processing |
| **scikit-image** | `scikit-image.org` | Scientific image processing |

---

## How to Search (Systematic Strategy)

### Step 1: GitHub Advanced Search

GitHub's search is the most important tool. Use these operators:

```bash
# Exact phrase matching
"cloud removal" satellite

# Filter by language
"land cover classification" language:python

# Filter by stars (indicator of quality/activity)
"exoplanet detection" stars:>10

# Filter by last update (inactive repos are risky)
"adaptive optics" pushed:>2024-01-01

# Search within specific orgs
org:nasa "space weather"

# Search README files (richer context than code)
"solar flare" in:readme

# Exclude forks (noise reduction)
"sar processing" fork:false

# Combined power query
("road extraction" OR "road segmentation") language:python stars:>5 fork:false pushed:>2024-01-01
```

### Step 2: Hugging Face Search

```bash
# Models
huggingface.co/models?search=[domain]+[modality]
# Example: huggingface.co/models?search=satellite+segmentation

# Spaces (running demos)
huggingface.co/spaces?search=[domain]
# Example: huggingface.co/spaces?search=image+colorization

# Datasets
huggingface.co/datasets?search=[sensor]+[region]
# Example: huggingface.co/datasets?search=sentinel+agriculture
```

### Step 3: Trace Paper → Code

For each relevant paper found in D1:

1. Check the paper itself for a "Code Availability" section or footnote
2. Search the lead author's GitHub (`github.com/[firstname][lastname]`)
3. Search Papers With Code for the paper title
4. Search `"paper title" github` on Google

### Step 4: Climb the Dependency Tree

Once you find one good repo:

1. Check its `requirements.txt`, `environment.yml`, `pyproject.toml` — what libraries does it depend on?
2. Check the "Used by" / "Dependents" tab on GitHub
3. Check "Similar repositories" in GitHub's sidebar
4. Look at the issues/discussions for links to related projects

---

## Scoring Guide for D2

### 18–20: Production-Ready Implementations

Multiple full, maintained implementations exist. You could fork a repo and have a working baseline in hours.

**Indicators:**

- 3+ GitHub repos implementing the core idea, each with >50 stars
- At least one repo has pretrained model weights you can download
- Domain-specific library exists (`pip install`able)
- Active maintenance (commits in last 3 months)
- Docker image or easy setup script (no dependency hell)
- Examples/tutorials showing usage

**Example:** Exoplanet detection — `lightkurve` (NASA) is production-quality, `exoplanet` library has comprehensive tutorials, multiple Kaggle solutions are open source.

### 14–17: Solid Building Blocks

No single "plug and play" solution, but excellent libraries exist that do 80% of the work. You'd need to compose them and write glue code.

**Indicators:**

- Domain library exists (data loading, preprocessing handled)
- 1-2 repos implementing a similar problem on different data
- Training scripts available that can be adapted
- Active community (Stack Overflow questions, blog posts)

**Example:** Crop classification — `eo-learn` handles Sentinel data pipeline, pretrained segmentation models on Hugging Face, but no single "crop type classifier for India" repo.

### 10–13: Partial Implementations

Some relevant code exists but it's incomplete, outdated, or requires significant modification.

**Indicators:**

- 1 repo with a basic implementation, possibly unmaintained
- Code from a paper exists but is "research quality" (messy, no docs)
- Only works on a specific dataset/region, not generalizable
- Installation is painful (outdated dependencies, no environment file)

**Example:** Lunar radar ice detection — some SAR processing scripts exist, but no turnkey analysis pipeline.

### 6–9: Scraps and Scripts

Very limited code — maybe a single script or notebook from a tutorial.

**Indicators:**

- Only preprocessing/visualization scripts, no model code
- Academic code that doesn't run without modification
- Bare repository with no README
- Code from >3 years ago using deprecated frameworks (TensorFlow 1.x)

### 0–5: Nothing Usable

No relevant code found. Starting from an empty file.

**Indicators:**

- GitHub search returns zero relevant results
- All related repos are private or internal
- The problem requires proprietary/classified software

---

## Red Flags

- **Repo has no license** — can't legally use it without contacting the author
- **Last commit >2 years ago with >20 open issues** — abandoned
- **No README or documentation** — you'll spend hours just understanding what it does
- **Hardcoded file paths** — won't work on your machine without modification
- **Requires MATLAB with expensive toolboxes** — not portable
- **"Works on my machine" syndrome** — no environment/container file
- **Single contributor, no stars, no forks** — unvetted code

## Green Flags 🟢

- **MIT, Apache 2.0, or BSD license** — freely usable
- **>100 stars and active in last 3 months** — community-validated and maintained
- **Pretrained weights on Hugging Face** — skips training, straight to inference
- **Docker Compose or devcontainer setup** — one-command environment
- **CI/CD pipeline with tests** — code actually works
- **Multiple contributors from different organizations** — not dependent on one person
- **Used in a published paper** — peer-reviewed validation

---

## Quick Code Discovery Commands

Save these as bash aliases or search templates:

```bash
# Search GitHub for topic + language + recency
gh search repos "[TOPIC]" --language=python --sort=stars --limit=20

# Search for awesome lists (curated resource collections)
gh search repos "awesome [DOMAIN]" --sort=stars

# Check if a domain has a PyPI package
pip search "[domain]" # or browse pypi.org

# Find models on Hugging Face
# URL: https://huggingface.co/models?pipeline_tag=[task]&sort=downloads

# Search arXiv papers that link to GitHub
# Add "github.com" to your arXiv search query
```

| Common Domain | GitHub Search | Hugging Face Pipeline |
| -------------------------- | ------------------------------------------------- | ------------------------- |
| Image segmentation | `"semantic segmentation" satellite` | `image-segmentation` |
| Object detection | `"object detection" remote sensing` | `object-detection` |
| Image-to-image translation | `pix2pix OR cyclegan satellite` | `image-to-image` |
| Time series forecasting | `"time series" space weather OR solar` | `time-series-forecasting` |
| Classification | `"land cover" OR "crop type" classification` | `image-classification` |
| Super-resolution | `"super resolution" satellite` | `image-super-resolution` |
| Inpainting | `"image inpainting" cloud OR gap` | `image-inpainting` |
| NLP / RAG | `rag OR "retrieval augmented" aerospace OR space` | `text-generation` |
