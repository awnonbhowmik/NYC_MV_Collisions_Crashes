# Structural Breaks in the Harm Profile of NYC Motor Vehicle Collisions (2016–2026)

Structural break analysis of 2.25 million police-reported NYC motor vehicle collisions,
focusing on hidden versus policy-coincident regime shifts across pedestrian, cyclist,
and motorist harm series.

**Dataset:** NYC Open Data — Motor Vehicle Collisions – Crashes
([h9gi-nx95](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95)),
downloaded March 2026 (records: July 2012 – March 21, 2026). Analysis restricted to
**March 1, 2016 – March 2026** (post-FORMS electronic reporting mandate).

---

## Central Question

Do pedestrian, cyclist, and motorist injury shares in NYC exhibit synchronised or
divergent structural breaks over the post-FORMS period, and are those breaks
attributable to known policy events or to unmeasured data/behavioural shifts?

---

## Method

PELT multiple change-point detection (RBF cost, BIC-style penalty, min segment 8 weeks)
applied to **nine weekly time series** (S1–S9):

| Series | Variable |
|--------|----------|
| S1 | Weekly crash count |
| S2 | Weekly persons injured |
| S3 | Pedestrian injury share |
| S4 | Cyclist injury share |
| S5 | Motorist injury share |
| S6 | Fatal crash share |
| S7 | Distraction contributing-factor share |
| S8 | Yield Failure contributing-factor share |
| S9 | Speed contributing-factor share |

Detected breaks are classified as **policy-coincident** (within 60 days of a known
event) or **hidden**. Breaks within 60 days of each other across series are
designated **synchronised**.

---

## Key Findings

- **9 structural breaks** detected across 9 series; **5 policy-coincident** (all
  COVID-related), **4 hidden**
- **COVID onset (March 2020)** produced synchronised breaks in crash count (S1),
  cyclist share (S4), fatal share (S6), and speed factor share (S9) within a
  six-week window — the dominant structural event in the decade
- **Pedestrian share (S3) shows no structural break** across the full period —
  structurally stable while cyclist and motorist shares both shift
- **Cyclist and motorist shares diverge post-pandemic**: cyclist hidden break
  Nov 2020; motorist break Aug 2021 — different recovery trajectories
- **Two hidden breaks in Distraction share (S7)** at Oct 2018 and Jan 2021,
  unattributable to any known policy event — potential reporting-behaviour artefacts

---

## Repository Structure

```
.
├── research.ipynb              # Main research notebook (all phases)
├── paper_outline.md            # Full paper skeleton with results narrative
├── requirements.txt            # Python dependencies
│
├── figures/                    # Publication figures (PNG, 300 dpi)
│   ├── fig_phase4_all_series   # PRIMARY: all 9 weekly series with PELT breakpoints
│   ├── fig1_annual_volume      # Annual crash volume & injury burden
│   ├── fig2_hourly_profiles    # Hourly profiles by road-user type
│   ├── fig3_factor_composition # Quarterly contributing factor composition (supporting)
│   ├── fig4_factor_by_user_type# Factor profiles by harm type (supporting)
│   ├── fig5_borough_heatmap    # Borough × factor heatmap (supporting)
│   └── fig6_borough_choropleth # Borough choropleth maps (supporting)
│
├── audit_report.txt            # Phase 1 data audit output
├── table1_descriptive_stats.csv# Sample overview and descriptive statistics
├── table2_breakpoints.csv      # PELT break dates and classifications (primary result)
├── table3_user_breaks.csv      # Break synchrony — road-user series
└── table4_factor_breaks.csv    # Break synchrony — factor-share series
```

> `crashes_clean.parquet` and `Motor_Vehicle_Collisions_-_Crashes.csv` are excluded
> from version control (large files — see `.gitignore`).

---

## Notebook Structure

| Phase | Content |
|-------|---------|
| **0** | Environment setup |
| **1** | Data audit — shape, missingness, pre/post-2016 reporting quality |
| **2** | Cleaning & feature engineering — datetime parsing, policy eras, injury flags, borough spatial imputation, contributing factor taxonomy |
| **3** | Descriptive figures (Figures 1–6) |
| **4** | PELT change-point detection on S1–S9 |
| **5** | Comparative break analysis — synchrony vs. divergence |
| **6** | Paper skeleton generation (`paper_outline.md`) |

---

## Setup

```bash
git clone https://github.com/awnonbhowmik/NYC_MV_Collisions_Crashes.git
cd NYC_MV_Collisions_Crashes
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook research.ipynb
```

> Download the dataset from [NYC Open Data (h9gi-nx95)](https://data.cityofnewyork.us/Public-Safety/Motor-Vehicle-Collisions-Crashes/h9gi-nx95)
> and place it in the project root as `Motor_Vehicle_Collisions_-_Crashes.csv` before running.

---

All Rights Reserved ©
