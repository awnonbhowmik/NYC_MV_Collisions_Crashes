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
contributing-factor shares—we identify 9 structural breaks, of which 5 coincide
with known policy events (COVID-19 onset, post-COVID re-opening) and 4 are
data-detected "hidden" breaks not attributable to known interventions. Pedestrian,
cyclist, and motorist injury shares exhibit both synchronised and divergent break
patterns, constituting the core empirical finding. Implications for crash-surveillance
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
   Mar 2016–Mar 2026, to our knowledge the most granular multi-series structural-break
   analysis of the post-FORMS NYC collision record to date.
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

---

## 3. Results

### 3.1 Descriptive Trends

*[Table 1 — Descriptive statistics: table1_descriptive_stats.csv]*
*[Figure 1 — Annual crash volume and injury burden]*

Annual crash volume peaked in 2018 (231,564 crashes) before declining steadily and
then sharply at the onset of COVID-19 in March 2020. The COVID period (March 2020–
June 2021) saw a 37.3% reduction in weekly crash volume relative to the equivalent
pre-pandemic period — but, critically, a 49.3% increase in mean per-crash injury
burden (0.298 → 0.445 persons injured per crash), consistent with the well-documented
speed-increase phenomenon during low-traffic periods [CITE]. Annual volume continued
declining post-pandemic, reaching 45% of the 2018 peak by 2022, suggesting a
structural downward shift rather than full recovery.

*[Figure 2 — Hourly injury profiles by road-user type]*

Pedestrian involvement peaks at 17:00 on weekdays and shifts to 18:00 on weekends,
reflecting the concentration of pedestrian activity at commute times. Cyclist injury
profiles exhibit a distinct bimodal weekday pattern, with a morning peak at 08:00 and
an afternoon peak at 17:00 consistent with commuter cycling patterns. Motorist-only
injuries track closely with overall traffic volume.

### 3.2 Contributing Factor Composition Over Time

*[Figure 3 — Quarterly factor composition, post-Mar 2016]*

Driver Inattention/Distraction has consistently dominated the informative-factor
distribution, comprising approximately 39.9% of all informative crashes throughout
the study period. Following Too Closely is the second largest category (30.7%),
together accounting for over 70% of informative-factor crashes. *(Discuss any
notable changes observed in Figure 3.)*

*[Figure 4 — Factor profiles by road-user harm type]*

Yield Failure and Pedestrian/Bike factors are disproportionately associated with
pedestrian-involved crashes relative to motorist-only crashes, while Following Too
Closely is predominantly a motorist-only pattern. *(Expand from Figure 4 values.)*

*[Figure 5 — Borough heatmap]*

Contributing factor profiles exhibit meaningful spatial heterogeneity across boroughs.
Manhattan has the highest crash density (2,586/km²) but the lowest fatal share
(0.14%); the Bronx has the highest fatal share (0.19%) at moderate density.
*(Describe the most salient borough-level differences observed in Figure 5.)*

### 3.3 Structural Breaks in Crash Harm Series

*[Figure — Phase 4 all-series plot: fig_phase4_all_series.png]*
*[Table 2 — Break summary: table2_breakpoints.csv]*

PELT detection identified **9 structural breaks** across nine weekly series.
**5 breaks** coincided with known policy events (all COVID-related), while **4**
were data-detected "hidden" breaks not attributable to any known intervention.
Notably, two series — S3 (pedestrian injury share) and S8 (Yield Failure factor
share) — yielded no detectable structural break.

Series-level findings:

- **S1 — Weekly crash count:** Single break at **2020-03-09** (COVID onset). Weekly
  volumes fell sharply as pandemic restrictions took hold, consistent with reduced
  vehicle miles travelled.
- **S2 — Weekly persons injured:** Single break at **2019-12-16** (hidden). This
  pre-pandemic break precedes any known policy change and may reflect a gradual
  shift in crash severity composition in late 2019.
- **S3 — Pedestrian injury share:** No structural break detected across the full
  post-FORMS period. Pedestrian involvement as a share of all injured persons
  appears structurally stable relative to the other road-user series.
- **S4 — Cyclist injury share:** Two breaks: **2020-04-20** (COVID onset, synchronised
  with S6) and **2020-11-09** (hidden). The second break suggests a cyclist-specific
  compositional shift during the autumn 2020 pandemic period, not shared by other
  road-user series.
- **S5 — Motorist injury share:** Single break at **2021-08-23** (COVID end). The
  delayed timing relative to the June 2021 policy reopening boundary suggests
  motorist-injury composition adjusted gradually.
- **S6 — Fatal crash share:** Single break at **2020-03-23** (COVID onset, synchronised
  with S1 and S4). Fatal share rose sharply during the low-volume, high-speed
  pandemic period.
- **S7 — Distraction factor share:** Two hidden breaks at **2018-10-08** and
  **2021-01-11**, neither attributable to known policy events. These may reflect
  gradual changes in officer reporting behaviour or the real-world adoption of
  hands-free device mandates.
- **S8 — Yield Failure factor share:** No structural break detected.
- **S9 — Speed factor share:** Single break at **2020-03-16** (COVID onset),
  consistent with anecdotal and empirical evidence of increased speeding during
  low-traffic pandemic conditions.

### 3.4 Synchrony and Divergence Across Road-User Types

*[Table 3 — User-type break comparison: table3_user_breaks.csv]*
*[Table 4 — Factor-share break comparison: table4_factor_breaks.csv]*

The analysis reveals a pattern of partial synchrony at COVID onset and divergence
thereafter. Specifically:

- **COVID onset synchrony (March–April 2020):** Breaks in S1 (crash count,
  2020-03-09), S4 (cyclist share, 2020-04-20), S6 (fatal share, 2020-03-23),
  and S9 (speed factor share, 2020-03-16) are all within 60 days of each other,
  indicating a uniform exogenous shock to the road network. This synchrony spans
  both road-user and contributing-factor dimensions.

- **Pedestrian share (S3) shows no break** — unlike cyclist (S4) and motorist (S5)
  shares — suggesting pedestrian involvement as a proportion of harm is structurally
  stable and does not respond to the same shocks that altered cyclist and motorist
  composition.

- **Post-COVID divergence:** The cyclist series (S4) exhibits a hidden break in
  November 2020, while the motorist series (S5) breaks in August 2021. These
  divergent timings indicate that cyclist and motorist harm compositions recovered
  from, or were transformed by, the pandemic shock along different trajectories —
  contrary to the null hypothesis of uniform post-pandemic adjustment.

- **Distraction factor share (S7)** exhibits two hidden breaks (October 2018 and
  January 2021), with no synchrony to either road-user breaks or known policy
  events. The January 2021 break occurs in the same quarter as S5's post-COVID
  adjustment, but the gap (>60 days) precludes formal synchrony designation.

- **Yield Failure (S8)** and **Speed (S9)** share no common break timing,
  suggesting factor-share structural change is not driven by a single common cause
  across contributing-factor categories.

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

This study presents a systematic multiple structural-break analysis of nine weekly
crash-harm series in New York City over the post-FORMS period (2016–2026).
We find evidence of 9 structural breaks across nine weekly series, of which 4 are
"hidden" breaks not attributable to known policy events. The COVID-19 onset of March
2020 emerges as the dominant structural event, producing synchronised breaks across
crash count, cyclist share, fatal share, and speed-factor share within a six-week
window. Importantly, pedestrian injury share (S3) exhibits no structural break across
the full decade, while cyclist and motorist shares diverge in their post-pandemic
adjustment trajectories — a finding with direct implications for vulnerable road-user
policy. The two hidden breaks in the Distraction factor share (October 2018, January
2021) raise questions about the stability of officer reporting behaviour independent
of real-world crash-cause changes, with implications for crash-surveillance practice
and the interpretation of FORMS-based administrative data.

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
