# 🌨️ Sentinel Node Initiative

### A Longitudinal Analysis of Climatological Severance and Sentinel Node ROI (2021–2026)

> *Quantifying the invisible barriers of climate and geography in frontier medicine — North Dakota's Great Plains.*

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Concepts](#key-concepts)
- [Methodology](#methodology)
- [Findings](#findings)
- [Intervention Strategy](#intervention-strategy)
- [ROI Analysis](#roi-analysis)
- [Data Sources](#data-sources)
- [Repository Structure](#repository-structure)
- [Usage](#usage)
- [Citation](#citation)
- [License](#license)

---

## Overview

This repository contains the research data, simulation models, and findings from a **5-year longitudinal study (2021–2026)** investigating how climatological and infrastructural conditions in the Great Plains effectively isolate frontier populations from healthcare access.

The study introduces **Climatological Severance** — a novel framework in Digital Epidemiology — and proposes the **Sentinel Node Initiative** as a decentralized, climate-resilient healthcare infrastructure solution.

---

## Key Concepts

### Climatological Severance
A state in which atmospheric and infrastructural conditions (blizzards, road closures) effectively **decouple** a population from its healthcare infrastructure. Unlike static distance metrics used in traditional geographic medicine, Climatological Severance treats distance as a *dynamic variable* influenced by environmental turbulence.

### The Friction Index ($FI$)
The primary quantitative innovation of this study. The $FI$ is a composite metric that models real-time healthcare resistance:

$$FI = f\left(SVI,\ R_p,\ \frac{|W_c|}{V},\ D_h\right)$$

| Variable | Description |
|----------|-------------|
| $SVI$ | **Structural Vulnerability Index** — baseline socio-economic resilience of the community |
| $R_p$ | **Infrastructure Elasticity** — binary status of primary transit arteries |
| $\frac{\|W_c\|}{V}$ | **Environmental Intensity** — ratio of wind-chill severity to atmospheric visibility |
| $D_h$ | **Distance Decay** — geometric distance to nearest Level 1 or 2 Trauma Hub |

### Annual Paralysis Day (APD)
Any 24-hour period where **$FI > 85$**, defined as a complete healthcare isolation event.

### Average Healthcare Isolation Score (AHIS)
A ranking index applied to all **53 North Dakota counties** based on longitudinal APD frequency data.

---

## Methodology

### Longitudinal Simulation
- **Duration:** 1,825 days (5 years)
- **Datasets:** NOAA historical weather records + NDDOT road closure data
- **Model:** Dynamic $FI$ recalculation at 6-hour intervals
- **Output:** Per-county AHIS rankings and Isolation Gradient mapping

### Isolation Gradient
Frontier counties demonstrate a **700% higher frequency of APDs** compared to urban centers — a statistically significant Isolation Gradient that forms the empirical basis for Sentinel Node placement.

```
APD Frequency (Frontier) ÷ APD Frequency (Urban) ≈ 7.0×
```

---

## Findings

| Metric | Value |
|--------|-------|
| Study Period | 2021 – 2026 |
| Counties Analyzed | 53 (all North Dakota) |
| Isolation Gradient Multiplier | 7.0× |
| Peak APD Counties | Burke, Slope, Sioux, Adams, Grant |
| Average Annual APDs (Frontier) | 34.2 days |
| Average Annual APDs (Urban) | 4.8 days |

### Key Takeaway
> *"The frontier is not simply far — it is intermittently unreachable."*

The data reveals that geographic distance alone is an insufficient metric. Environmental and infrastructural variables can raise effective healthcare inaccessibility by an order of magnitude during winter months.

---

## Intervention Strategy

### The Sentinel Node
A **decentralized clinical hub** engineered for Frontier Resilience. Key design principles:

- 📍 **Location:** Strategically placed at high-redundancy transit points (e.g., fuel stations with auxiliary power)
- 🛰️ **Connectivity:** Low Earth Orbit (LEO) satellite arrays ensuring 24/7 medical-grade uptime
- ⚡ **Resilience:** Designed to remain operational when terrestrial grids fail
- 🏥 **Function:** Triage, teleconsultation, and stabilization during "Paralysis Events"

Unlike traditional rural clinics, Sentinel Nodes are optimized for **temporal accessibility** — remaining online precisely when conventional infrastructure fails.

---

## ROI Analysis

This study applies an **Avoided-Cost Model** to reframe public health expenditure as a fiscal asset rather than a sunk cost.

```
Prevented escalation rate:         1.5% of acute complications
Average ER admission cost:         $18,500 / incident
Projected Net-Positive ROI:        Year 3.5 – 4.5
```

By preventing just **1.5%** of acute complications from escalating to emergency admissions, each Sentinel Node achieves positive return within **3.5 to 4.5 years** — transforming a social good into a measurable fiscal asset.

---

## Data Sources

| Source | Usage |
|--------|-------|
| [NOAA Climate Data Online](https://www.ncdc.noaa.gov/cdo-web/) | Historical weather, wind-chill, and visibility records |
| [NDDOT Road Condition Reports](https://www.dot.nd.gov/) | Infrastructure elasticity and road closure events |
| [CDC Social Vulnerability Index](https://www.atsdr.cdc.gov/placeandhealth/svi/) | Baseline SVI per census tract |
| [CMS Rural Health Data](https://www.cms.gov/) | Trauma Hub locations and emergency admission costs |

---

## Repository Structure

```
sentinel-node-initiative/
│
├── README.md                   ← You are here
├── DESCRIPTION.md              ← Repository description & abstract
├── index.html                  ← Interactive research website
├── LICENSE                     ← MIT License
│
├── data/
│   ├── raw/
│   │   ├── noaa_weather_2021_2026.csv
│   │   └── nddot_road_closures.csv
│   ├── processed/
│   │   ├── friction_index_daily.csv
│   │   └── county_ahis_rankings.csv
│   └── shapefiles/
│       └── nd_counties.geojson
│
├── models/
│   ├── friction_index.py       ← Core FI calculation engine
│   ├── apd_classifier.py       ← Annual Paralysis Day detection
│   └── roi_model.py            ← Avoided-Cost ROI projections
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_fi_simulation.ipynb
│   ├── 03_isolation_gradient.ipynb
│   └── 04_roi_analysis.ipynb
│
├── figures/
│   ├── isolation_gradient_map.png
│   ├── fi_distribution_by_county.png
│   └── roi_projection_curve.png
│
└── docs/
    ├── full_paper.pdf
    └── supplementary_methods.pdf
```

---

## Usage

### Requirements
```bash
Python >= 3.9
numpy >= 1.24
pandas >= 2.0
geopandas >= 0.13
matplotlib >= 3.7
scipy >= 1.11
```

### Installation
```bash
git clone https://github.com/your-org/sentinel-node-initiative.git
cd sentinel-node-initiative
pip install -r requirements.txt
```

### Run the Friction Index Simulation
```python
from models.friction_index import FrictionIndex

fi = FrictionIndex(
    svi=0.72,          # Social Vulnerability Index (0–1)
    road_open=False,   # Primary artery status
    wind_chill=-38,    # °F
    visibility=0.25,   # Miles
    distance_hub=87    # Miles to nearest Trauma Hub
)

print(fi.score())  # Returns float; >85 = Paralysis Event
```

### Reproduce AHIS County Rankings
```bash
python models/apd_classifier.py --input data/processed/friction_index_daily.csv --output results/ahis_rankings.csv
```

---

## Citation

If you use this research or codebase, please cite:

```bibtex
@article{sentinel_node_2026,
  title   = {Climatological Severance and Sentinel Node ROI: A Longitudinal Analysis of Healthcare Friction in North Dakota's Great Plains (2021–2026)},
  author  = {[Authors]},
  journal = {Journal of Digital Epidemiology and Rural Health},
  year    = {2026},
  note    = {Preprint available at: https://github.com/your-org/sentinel-node-initiative}
}
```

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

Data sourced from NOAA and NDDOT is subject to respective federal open-data terms.

---

<div align="center">

*"Flattening the friction curve — ensuring health equity in the face of environmental extremes."*

**Sentinel Node Initiative · Digital Epidemiology Lab · 2021–2026**

</div>
