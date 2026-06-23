# D3: Dataset Accessibility (20 pts)

> **Core Question:** Can we get the data we need — right now, legally, and in a usable format — or are we blocked by access restrictions, licensing, or preprocessing nightmares?

This dimension measures how easy it is to obtain and use the data required to build and evaluate a solution. A high score means data is a few clicks away; a low score means data is the bottleneck.

---

## What We're Looking For

Data access assessed across multiple axes:

| Axis | Question |
| ---------------- | --------------------------------------------------------------------- |
| **Availability** | Is the data publicly downloadable, or does it require approval/money? |
| **Coverage** | Does it cover the geography, time period, and conditions we need? |
| **Quality** | Is it calibrated, validated, and well-documented? |
| **Format** | Is it in a standard format (GeoTIFF, NetCDF, HDF5) or proprietary? |
| **Volume** | Does it fit on a laptop, or do we need cloud storage/GPU servers? |
| **Labels** | For supervised learning: are ground truth labels available? |

---

## Where to Search

### Tier 1: Major Open Data Portals

| Portal | URL | Coverage | Best For |
| ------------------------- | ------------------------- | ---------------------- | --------------------------------------- |
| **NASA EarthData** | `earthdata.nasa.gov` | Global | All NASA Earth science missions |
| **Copernicus Data Space** | `dataspace.copernicus.eu` | Global | Sentinel-1/2/3/5P complete archive |
| **USGS EarthExplorer** | `earthexplorer.usgs.gov` | Global | Landsat 1-9 (50+ years), ASTER, MODIS |
| **NOAA NCEI** | `ncei.noaa.gov` | Global | GOES, POES, environmental monitoring |
| **EUMETSAT** | `data.eumetsat.int` | Europe/Africa/Atlantic | Meteosat, Metop |
| **Bhuvan (NRSC)** | `bhuvan.nrsc.gov.in` | India | Satellite imagery, thematic maps |
| **data.gov.in** | `data.gov.in` | India | Government open datasets — all domains |

### Tier 2: Domain-Specific Portals

| Source | Portal | Key Datasets |
| -------- | ---------------------- | ------------------------------------------------- |
| **NASA** | `earthdata.nasa.gov` | MODIS, Landsat, VIIRS, TROPOMI — global coverage |
| **ESA** | `dataspace.copernicus.eu` | Sentinel-1/2/3/5P — complete archive |
| **USGS** | `earthexplorer.usgs.gov` | Landsat 1-9 (50+ years), ASTER |
| **ECMWF** | `cds.climate.copernicus.eu` | ERA5 reanalysis, CAMS air quality |
| **OpenAQ** | `openaq.org` | Global real-time air quality measurements |
| **IEA** | `iea.org` | Energy statistics, supply chain data |
| **World Bank** | `data.worldbank.org` | Development, climate, economic indicators |
| **Kaggle** | `kaggle.com/datasets` | Diverse community-curated datasets |

### Tier 3: Science Archives

| Archive | URL | Domain |
| ------------ | --------------------------- | -------------------------------------------------- |
| **NASA PDS** | `pds.nasa.gov` | Planetary data (LRO, Lunar Reconnaissance Orbiter) |
| **ESA PSA** | `archives.esac.esa.int/psa` | Planetary science archive |
| **MAST** | `mast.stsci.edu` | Kepler, TESS, HST, JWST |
| **HEASARC** | `heasarc.gsfc.nasa.gov` | High-energy astrophysics (X-ray, gamma) |
| **JSOC** | `jsoc.stanford.edu` | SDO/HMI solar data |
| **SDAC** | `umbra.nascom.nasa.gov` | Solar data analysis center |
| **IRIS** | `iris.lmsal.com` | Interface Region Imaging Spectrograph |

### Tier 4: Specialized Data Repositories

| Repository | URL | Domain |
| -------------------------------- | ----------------------------------- | ------------------------------- |
| **Radiant MLHub** | `mlhub.earth` | Geospatial ML training data |
| **Kaggle Datasets** | `kaggle.com/datasets` | Diverse, community-curated |
| **Hugging Face Datasets** | `huggingface.co/datasets` | ML-ready datasets |
| **Zenodo** | `zenodo.org` | Research data, DOI-backed |
| **Figshare** | `figshare.com` | Research outputs |
| **Google Dataset Search** | `datasetsearch.research.google.com` | Meta-search across repositories |
| **AWS Open Data** | `registry.opendata.aws` | Cloud-hosted public datasets |
| **Microsoft Planetary Computer** | `planetarycomputer.microsoft.com` | Geospatial data + compute |

### Tier 5: Commercial / Semi-Open

| Provider | Access Model | What You Get |
| ------------------- | --------------------------- | -------------------------------------------------------- |
| **Planet Labs** | Free for students/academics | Daily 3-5m global imagery (Education & Research program) |
| **Maxar Open Data** | Free for disasters | High-res imagery for major disaster events |
| **Airbus OneAtlas** | Free tier available | SPOT, Pleiades sample data |
| **Spire** | Some open data | GNSS radio occultation sample data |

---

## How to Search (Systematic Strategy)

### Step 1: Identify Required Data Types

From the PS description, extract:

| Data Need | Example | Where to Look |
| ----------------------- | ------------------------------------------------------ | ------------------------------------- |
| **Input data (X)** | Satellite imagery, time-series, radar | Major data portals (Tier 1) |
| **Labels / target (Y)** | Ground truth maps, classification labels, measurements | Science archives, specialized repos |
| **Auxiliary data** | DEM, weather, land cover masks | Open government data, cross-reference |

### Step 2: Search Each Portal

**NASA EarthData:**

```bash
# Search by instrument, parameter, or location
# Use CMR (Common Metadata Repository) API
curl "https://cmr.earthdata.nasa.gov/search/collections.json?keyword=[instrument]&page_size=20"
```

**Copernicus:**

```bash
# Sentinel Hub Catalog API
# Search by date range, cloud cover, AOI
# Use the EO Browser GUI first to explore visually
```

**Indian Government Data:**

```bash
# Search for Indian regional data via data.gov.in
# CPCB air quality data: https://cpcb.nic.in
# Check data access policy — some datasets require registration
```

### Step 3: Check Data Quality & Practicality

For each candidate dataset, verify:

1. **Spatial resolution** — Is it fine enough for the task?
2. **Temporal coverage** — Does it cover the required period?
3. **Geographic coverage** — Does it cover the target region?
4. **Format** — Is it GeoTIFF, NetCDF, HDF5, or something weird?
5. **Size** — Can you download a sample in minutes, or is it TB-scale?
6. **License** — Can you use it for this purpose? (Most government data is public domain)
7. **Documentation** — Is there a user guide, or do you need to reverse-engineer?

### Step 4: Assess Label Availability

For supervised ML approaches, labels are often the bottleneck:

| Label Source | Reliability | Effort |
| ------------------------------------------------ | ----------- | ---------------------------- |
| Existing labeled dataset | High | Low — download and use |
| Automatically generated from another data source | Medium | Medium — verify quality |
| Expert annotation (manual) | Very High | Very High — time-consuming |
| Weak supervision from rules/heuristics | Medium-Low | Medium — risk of bias |
| Transfer from pretrained model | Medium | Low-Medium — domain gap risk |

---

## Scoring Guide for D3

### 18–20: Plug-and-Play Data

Multiple high-quality public datasets exist that are directly usable for this PS. Data is well-documented, in standard formats, and fits on a laptop or is accessible via cloud API (no download needed).

**Indicators:**

- 2+ independent datasets specifically for this problem
- Standard format (GeoTIFF, NetCDF) with clear documentation
- Pre-split train/validation/test sets available
- Cloud-accessible (AWS S3, GCS) — no download needed
- Example notebooks showing data loading exist
- License is clear and permissive (CC0, CC BY, public domain)

**Example:** Sentinel-2 data for land cover — Copernicus Data Space provides API access, multiple labeled datasets (BigEarthNet, EuroSAT), standard GeoTIFF format, free and open.

### 14–17: Good Data Available

Primary datasets exist and are accessible, but may require preprocessing, registration, or have some gaps.

**Indicators:**

- One solid dataset covering the core need
- May require free registration (EarthData login, etc.)
- Some preprocessing needed (cloud masking, resampling, reprojection)
- Fits on consumer hardware (<100 GB)
- Clear documentation available

**Example:** Landsat thermal data for urban heat — freely available via USGS, but needs scene selection, cloud masking, and LST calculation before use.

### 10–13: Partial Data Coverage

Some relevant data exists but with significant gaps — temporal, spatial, or in availability of labels.

**Indicators:**

- Data exists but doesn't fully cover the target region/time
- No ground truth labels available — would need to create them
- Requires multi-source fusion (complex preprocessing)
- Large download required (>100 GB)
- Registration or approval process needed (days to weeks)

**Example:** Industrial IoT sensor data — may be available through research datasets or Kaggle, but real-time SCADA data from operational plants is typically proprietary and hard to access.

### 6–9: Very Limited Data

Data is mostly proprietary, heavily restricted, or requires special access.

**Indicators:**

- Primary dataset is not publicly available
- Can only access simulated or synthetic data
- Requires institutional agreement or MOU
- Only a tiny sample is available publicly
- Format is proprietary and undocumented

### 0–5: No Data Available

No usable data can be found. The PS requires data that doesn't exist publicly.

**Indicators:**

- All required data is classified or internal to the proposing organization
- No equivalent open dataset exists
- Would need to generate synthetic data from scratch with high uncertainty
- Even simulated data is hard to produce due to lack of reference

---

## Red Flags

- **"Data will be provided upon selection"** — you can't evaluate feasibility before committing
- **Proprietary format with no reader library** — reverse-engineering file formats is a time sink
- **TB-scale dataset with no cloud access** — infrastructure problem before you start
- **Requires institutional agreement / MOU** — legal friction, unpredictable timeline
- **Data is in a foreign language with no English metadata** — CNSA portals, for example
- **No validation dataset or ground truth** — can't evaluate your solution objectively
- **Dataset was collected once in 2015 and never updated** — stale data for a 2026 PS

## Green Flags 🟢

- **STAC (SpatioTemporal Asset Catalog) compliant** — modern, interoperable standard
- **Cloud-optimized GeoTIFF (COG)** — stream only what you need, no full download
- **Pre-packaged as a Hugging Face Dataset** — one line of Python to load
- **Example notebook in the data portal** — proves the data access pipeline works
- **Multiple independent benchmark datasets** — you can validate on different distributions
- **Data updated regularly (near real-time)** — for forecasting/nowcasting PS
- **Ground truth from a trusted authority** (government, field campaign, certified lab) — reliable labels

---

## Quick Data Assessment Checklist

For each candidate dataset, answer these yes/no:

```
 Can I download it right now without waiting for approval?
 Is the license clear and permissive?
 Is it in a standard format (GeoTIFF, NetCDF, HDF5, CSV, Zarr)?
 Is there a Python library that can read it?
 Does it cover the geographic region I need?
 Does it cover the time period I need?
 Is the spatial resolution sufficient?
 Are ground truth labels available (if supervised)?
 Does it fit on my hardware (<100 GB)?
 Is there a tutorial or example notebook using it?

Score: ____ / 10 yes → map to D3 score:
 9-10 yes → 18-20
 7-8 yes → 14-17
 5-6 yes → 10-13
 3-4 yes → 6-9
 0-2 yes → 0-5
```

---

## Cross-Reference: Common Dataset Patterns by Domain

| PS Domain | Typical Data Need | Best Free Source | Typical Format | Approx Size |
| --------------------------- | ------------------------- | ----------------------- | -------------- | -------------------- |
| Earth Observation (optical) | Multispectral imagery | Sentinel-2, Landsat 8/9 | GeoTIFF (COG) | ~1 GB per 100×100 km |
| Earth Observation (SAR) | Radar backscatter | Sentinel-1 | GeoTIFF | ~2 GB per scene |
| Atmosphere / Trace Gases | Column densities | Sentinel-5P TROPOMI | NetCDF | ~100 MB per orbit |
| Thermal / Temperature | Brightness temperature | Landsat TIRS, MODIS | HDF5, GeoTIFF | ~500 MB per scene |
| Climate Reanalysis | Gridded atmospheric vars | ERA5 (ECMWF) | GRIB, NetCDF | ~100 GB for global |
| Solar Physics | Magnetograms, X-ray flux | SDO/HMI, GOES XRS | FITS | ~100 MB per day |
| Exoplanet Light Curves | Time-series photometry | Kepler, TESS (MAST) | FITS | ~100 KB per star |
| Lunar/Planetary Radar | SAR imagery | LRO Mini-RF (PDS) | PDS IMG | ~500 MB per orbit |
| Space Weather Particles | Particle flux time-series | GOES (NOAA NCEI) | CSV, NetCDF | ~10 MB per day |
