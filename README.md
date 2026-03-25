# Structural Breaks in the Harm Profile of NYC Motor Vehicle Collisions (2016–2026)

A data-driven research project analysing 2.25 million police-reported motor vehicle
collisions in New York City using structural break detection, contributing factor
analysis, and logistic regression.

**Dataset:** NYC Open Data — Motor Vehicle Collisions – Crashes ([h9gi-nx95](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95)), updated March 2026.

---

## Research Overview

This project applies PELT multiple change-point detection to nine weekly crash-harm
time series (March 2016–March 2026) to identify structural breaks in NYC crash
patterns, classify them as policy-coincident or data-detected "hidden" breaks, and
compare break timing across road-user subgroups and contributing-factor categories.

### Core contributions
1. First multiple structural-break analysis of the full post-FORMS NYC crash record
2. Taxonomy of policy-coincident vs. hidden breaks across pedestrian, cyclist, and motorist injury shares
3. Borough-level spatial analysis of crash density and harm profiles
4. Logistic regression of vulnerable-user involvement by policy era, contributing factor, and borough

---

## Repository Structure

```
.
├── research.ipynb              # Main research notebook (all phases)
├── paper_outline.md            # Paper skeleton with placeholder text
├── requirements.txt            # Python dependencies
│
├── figures/                    # All publication figures (PNG 300dpi + PDF)
│   ├── fig1_annual_volume      # Monthly crash volume & injury burden
│   ├── fig2_hourly_profiles    # Hourly profiles by road-user type
│   ├── fig3_factor_composition # Quarterly contributing factor composition
│   ├── fig4_factor_by_user_type# Factor profiles by harm type
│   ├── fig5_borough_heatmap    # Borough × factor heatmap
│   ├── fig6_borough_choropleth # Borough choropleth maps (4-panel)
│   └── fig_phase4_all_series   # All 9 weekly series with PELT breakpoints
│
├── audit_report.txt            # Phase 1 data audit output
├── phase4_breakpoints.csv      # Detected break dates and classifications
├── table1_user_breaks.csv      # Break comparison — road-user series
├── table2_factor_breaks.csv    # Break comparison — factor-share series
├── regression_PEDESTRIAN_INVOLVED.csv
├── regression_CYCLIST_INVOLVED.csv
└── regression_FATAL.csv
```

> `crashes_clean.parquet` and `Motor_Vehicle_Collisions_-_Crashes.csv` are excluded
> from version control (large files — see `.gitignore`).

---

## Notebook Structure

| Phase | Content |
|-------|---------|
| **0** | Environment setup — package version check |
| **1** | Data audit — shape, missingness, value distributions, pre/post-2016 reporting quality |
| **2** | Cleaning & feature engineering — datetime parsing, policy eras, injury flags, borough spatial imputation, broad contributing factor taxonomy |
| **3** | Descriptive figures — Figures 1–6 |
| **4** | PELT change-point detection on 9 weekly series (S1–S9) |
| **5** | Comparative break analysis — synchrony vs. divergence across user types and factor shares |
| **6** | Logistic regression — pedestrian involvement, cyclist involvement, fatal crash |
| **7** | Paper skeleton generation (`paper_outline.md`) |

---

## Setup

```bash
# Clone
git clone https://github.com/yourusername/NYC_MV_Collisions_Crashes.git
cd NYC_MV_Collisions_Crashes

# Create virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Launch notebook
jupyter notebook research.ipynb
```

> Download the dataset from [NYC Open Data (h9gi-nx95)](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95)
> and place it in the project root as `Motor_Vehicle_Collisions_-_Crashes.csv` before running.

---

## Key Findings (preliminary)

- PELT detected structural breaks including **COVID-coincident breaks** in crash count (S1), cyclist share (S4), fatal share (S6), and speed factor share (S9)
- **Two hidden breaks** in the Distraction factor share (S7) at Oct 2018 and Jan 2021 — not attributable to any known policy event
- **Pedestrian share (S3) shows no structural break** — unlike cyclist and motorist shares — suggesting pedestrian involvement is structurally stable relative to other harm types
- **Borough spatial divergence**: Manhattan has the highest crash density (2,586/km²) but the lowest fatal share (0.14%); the Bronx has the highest fatal share (0.19%) at moderate density
- Logistic models (AUC 0.76–0.81): Speed factor carries OR = 7.1 for fatality; Pedestrian/Bike error factor carries OR = 9.6 for fatality relative to Distraction

---

All Rights Reserved ©
