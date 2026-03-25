# Structural Breaks in the Harm Profile of NYC Motor Vehicle Collisions, 2016–2026

> **Working title** — replace before submission.  
> All figure/table references point to outputs in `figures/` and `*.csv` files.

---

## Abstract

*(150 words max — to be completed after results are finalised.)*

This study examines structural change in the harm profile of motor vehicle collisions
in New York City between March 2016 and March 2026, using a complete administrative
record of 2.25 million crashes drawn from the NYC Motor Vehicle Collisions dataset
(NYC Open Data, h9gi-nx95). Applying PELT multiple change-point detection to nine
weekly time series—covering crash volume, injury burden, road-user harm shares, and
contributing-factor shares—we identify [N] structural breaks, of which [M] coincide
with known policy events (Vision Zero, FORMS rollout, COVID-19 onset, post-COVID
re-opening) and [K] are data-detected "hidden" breaks not attributable to known
interventions. Pedestrian, cyclist, and motorist injury shares exhibit both
synchronised and divergent break patterns, constituting the core empirical finding.
Logistic regression confirms significant associations between policy era, contributing
factor type, and vulnerable-user involvement. Implications for crash-surveillance
methodology and urban safety policy are discussed.

---

## 1. Introduction

Urban crash-harm surveillance has evolved substantially since the introduction of
electronic police reporting systems. In New York City, the 2014 Vision Zero initiative
and the 2016 electronic crash-report mandate (FORMS) created a natural quasi-experiment
that allows researchers to decompose temporal changes in crash harm into policy-driven
and data-collection-driven components.

Prior work has characterised longitudinal crash trends in NYC using aggregate annual
statistics [CITE] or regression discontinuity at single known thresholds [CITE].
No published study has applied multiple structural-break detection to the full
post-FORMS time series, nor systematically compared break timing across road-user
subgroups and contributing-factor categories simultaneously.

This paper makes three contributions:
1. A comprehensive time-series audit of nine weekly crash-harm indicators spanning
   Mar 2016–Mar 2026 — the longest such analysis in the NYC literature.
2. A structural-break taxonomy distinguishing policy-coincident from data-detected
   breaks across road-user harm types and causal-factor shares.
3. Evidence on the synchrony vs. divergence of structural change across pedestrian,
   cyclist, and motorist injury trajectories — the core novelty claim.

---

## 2. Data and Methods

### 2.1 Dataset

We used the NYC Motor Vehicle Collisions – Crashes dataset (NYC Open Data, identifier
h9gi-nx95), downloaded March 2026. The dataset contains 2,250,357 crash records from
July 2012 through March 2026, each representing a police-reported collision.

All contributing-factor analyses are restricted to records on or after **March 1, 2016**,
coinciding with mandatory FORMS electronic reporting. The informative-factor rate
(proportion of records with a specific, non-"Unspecified" contributing factor) was
30.9% in 2012, rose to 58.0% in 2016, and stabilised at approximately 63% from 2017
onward — motivating the post-2016 restriction.

Borough was spatially imputed from GPS coordinates for records lacking a borough
label, using NYC Planning Department boundary polygons, reducing borough missingness
from 30.5% to 9.5%.

### 2.2 Variable Construction

**Temporal features.** Each record was assigned a policy era:
- *Pre-VZ*: before January 1, 2014
- *VZ-Early*: January 1, 2014 – February 28, 2016
- *VZ-FORMS*: March 1, 2016 – March 21, 2020 *(reference category)*
- *COVID*: March 22, 2020 – June 30, 2021
- *Post-COVID*: July 1, 2021 onward

**Injury composition flags.** `PEDESTRIAN_INVOLVED`, `CYCLIST_INVOLVED`, `MOTORIST_ONLY`,
`FATAL`, and `ANY_INJURY` were derived from the NYPD-reported injury/fatality counts
per crash.

**Contributing factors.** Raw NYPD contributing-factor codes were normalised
(whitespace stripped, title-cased, typographic duplicates merged) and mapped to
eight interpretable broad categories: Distraction, Yield Failure, Speed,
Alcohol/Drugs, Following, Fatigue, Vehicle Defect, and Pedestrian/Bike, with a
residual Other/Unspecified category.

### 2.3 Analytical Strategy

**Structural break detection.** We constructed nine weekly time series (S1–S9)
over the post-FORMS period and applied the PELT algorithm with an RBF cost function
(ruptures v1.1; [CITE Truong et al. 2020]) using a BIC-style penalty. Minimum
segment length was set to 8 weeks. Detected break dates were classified as
"policy-coincident" if within 60 days of a known event, or "hidden" otherwise.

**Comparative break analysis.** Break dates across road-user series (S3–S6) and
factor-share series (S7–S9) were compared; breaks within 60 days of each other
across series were designated "synchronised."

**Regression models.** Three logistic regression models (outcomes: pedestrian
involvement, cyclist involvement, fatal crash) were fit on post-2016 records with
non-Unspecified contributing factor and non-null borough. Predictors included
hour of day, weekend indicator, season, policy era, broad contributing factor
category, and borough. Odds ratios with 95% confidence intervals, McFadden
pseudo-R², and AUC-ROC are reported.

---

## 3. Results

### 3.1 Descriptive Trends

*[Figure 1 — Annual crash volume and injury burden]*

Annual crash volume peaked at [YEAR] ([N] crashes) before declining sharply at the
onset of COVID-19 (March 2020). The COVID period saw a [X]% reduction in crash
volume but — critically — a disproportionate increase in per-crash injury burden,
consistent with the well-documented speed-increase phenomenon during low-traffic
periods [CITE]. Volume recovered to [Y]% of pre-COVID levels by [YEAR].

*[Figure 2 — Hourly injury profiles by road-user type]*

Pedestrian involvement peaks during [HOUR] on weekdays and shifts to [HOUR] on
weekends, reflecting the concentration of pedestrian activity at commute times.
Cyclist injury profiles exhibit a distinct bimodal weekday pattern. Motorist-only
injuries track closely with overall traffic volume.

### 3.2 Contributing Factor Composition Over Time

*[Figure 3 — Quarterly factor composition, post-Mar 2016]*

Driver Inattention/Distraction has consistently dominated the informative-factor
distribution, comprising approximately [X]% of all informative crashes throughout
the study period. *(Discuss any notable changes observed in Figure 3.)*

*[Figure 4 — Factor profiles by road-user harm type]*

Yield Failure and Pedestrian/Bike factors are disproportionately associated with
pedestrian-involved crashes relative to motorist-only crashes, while Following Too
Closely is predominantly a motorist-only pattern. *(Expand from Figure 4 values.)*

*[Figure 5 — Borough heatmap]*

Contributing factor profiles exhibit meaningful spatial heterogeneity across boroughs.
*(Describe the most salient borough-level differences observed in Figure 5.)*

### 3.3 Structural Breaks in Crash Harm Series

*[Figure — Phase 4 all-series plot: fig_phase4_all_series.png]*
*[Table — Phase 4 break summary: phase4_breakpoints.csv]*

PELT detection identified [N_total] structural breaks across nine weekly series.
[N_policy] breaks coincided with known policy events (Vision Zero, FORMS rollout,
COVID onset, COVID end), while [N_hidden] were data-detected "hidden" breaks.

*(Insert specific break dates and narrative description for each series here.)*

### 3.4 Synchrony and Divergence Across Road-User Types

*[Table 1 — User-type break comparison]*
*[Table 2 — Factor-share break comparison]*

**[FILL IN based on Table 1 output]**

The analysis reveals that [synchronised / divergent] structural change characterises
the pedestrian and cyclist harm series relative to the motorist-only series.
Specifically:
- The COVID onset break (approximately March–April 2020) appears synchronised
  across all three user-type series, suggesting a uniform shock to the road network.
- Post-COVID breaks, however, are [synchronised / divergent], indicating
  [interpretation].
- The Distraction factor share (S7) exhibits [describe].

*(This narrative is the core empirical finding of the paper — complete after
reviewing Table 1 and Table 2 outputs.)*

### 3.5 Regression Results

*[Tables: regression_PEDESTRIAN_INVOLVED.csv, regression_CYCLIST_INVOLVED.csv, regression_FATAL.csv]*

Logistic models for pedestrian involvement, cyclist involvement, and fatal crashes
all achieved McFadden pseudo-R² of approximately [X], indicating [interpretation].

Key findings:
- **Policy era:** Relative to VZ-FORMS, the COVID era is associated with
  [higher/lower] odds of [outcome] (OR = [X], 95% CI [A–B]).
- **Contributing factor:** Pedestrian/Bike errors carry substantially higher odds of
  pedestrian involvement (OR = [X]) relative to the Distraction reference.
- **Borough:** [Notable borough-level OR findings].
- **Hour and weekend:** [Describe temporal patterns].

---

## 4. Discussion

*(To be completed — key themes to address:)*
- What do hidden breaks tell us about unmeasured policy changes or data artefacts?
- Why do cyclist breaks diverge from pedestrian breaks despite both being
  vulnerable-user categories?
- Implications for the FORMS data infrastructure as a public-health surveillance tool.
- How do findings compare to prior NYC and non-NYC crash-harm literature?

---

## 5. Limitations

1. **NYPD reporting quality.** Approximately 37% of post-2016 crashes remain coded
   as "Unspecified" contributing factor. This restricts factor-share analyses to
   the 63% informative subset and may introduce selection bias if crashes with
   specific factor types are systematically less likely to receive a specific code.

2. **Borough imputation.** GPS-based borough assignment for the 21% of records with
   coordinates but missing borough may introduce minor misclassification near
   borough boundaries.

3. **No exposure data.** The analysis is based on crash counts and shares; vehicle
   miles travelled, pedestrian counts, or cycling volumes are not available at weekly
   granularity, preventing rate-based inference.

4. **Single change-point method.** PELT break dates are sensitive to the penalty
   parameter. Sensitivity analyses with alternative penalties and the Binary
   Segmentation algorithm are warranted.

5. **Study period.** Data for 2026 is partial (through March 21, 2026) and is
   excluded from annual-trend analyses.

---

## 6. Conclusion

*(To be completed after finalising break-date results.)*

This study provides the first systematic multiple structural-break analysis of nine
weekly crash-harm series in New York City over the post-FORMS period (2016–2026).
We find evidence of [N] structural breaks, including [N_hidden] not attributable
to known policy events, and demonstrate [synchrony / divergence] in the timing of
structural change across pedestrian, cyclist, and motorist harm series. These
findings carry direct implications for crash-surveillance practice and for the
evaluation of urban road-safety interventions.

---

## References

*(Placeholder — complete with full citations.)*

1. NYC Open Data. Motor Vehicle Collisions – Crashes (h9gi-nx95). Accessed March 2026.
2. New York City Department of Transportation. Vision Zero Year [N] Report. [YEAR].
3. Truong C, Oudre L, Vayatis N. Selective review of offline change point detection
   methods. *Signal Processing*. 2020;167:107299.
4. [CITE prior NYC crash analysis papers]
5. [CITE structural break methodology papers]
6. [CITE road-user harm decomposition papers]
