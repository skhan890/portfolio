# Global Polio Surveillance Analytics Pipeline

**CDC Global Immunization Division · WHO / Independent Monitoring Board · 2016–2019**

> Production-grade data pipeline transforming fragmented global AFP surveillance data into a standardized, decision-ready asset. Methodology published in *Vaccine X* (2020) and the 15th IMB Report (2017).

---

## The Problem: The "Raw Numbers" Trap

Polio surveillance was failing because of a data quality problem hiding in plain sight: applying the same KPIs to a province of 5 million people as one of 50,000. This accidentally obscured virus circulation in small areas while overstating success in large ones — **compromising data integrity and stalling eradication efforts**.

---

## Solution: Spatial Binning as a Common Currency

I developed a **Spatial Binning method** to standardize surveillance comparisons across geographies of wildly different sizes.

- **Method:** Aggregated districts into units of **200,000 children under 15**, starting from the district level up — creating comparable units regardless of administrative boundaries
- **Governance:** Implemented four automated **Surveillance Flags** (Timeliness, Notification, Specimen, Age) to identify where data itself was implausible
- **Quality Assurance:** Flags caught unreliable data before it reached decision-makers, establishing a clean foundation for global prioritization

---

## Data Engineering Lifecycle

| Phase | What I Did |
|-------|-----------|
| **Extract** | Integrated AFP case data from WHO POLIS database (79 countries) + WorldPop population estimates via SQL into R |
| **Transform** | Developed custom spatial binning functions in R to aggregate districts into 200,000-person units; programmed 4 automated surveillance flags |
| **Load** | Produced high-impact Blind Spot Maps for the IMB; maintained the production codebase on GitLab for two years — any GPEI partner could download and reproduce the analysis with updated data |

---

## Surveillance Flags

| Flag | What It Detects |
|------|----------------|
| **Timeliness** | Stool samples not collected within protocol windows (1st ≤13 days, 2nd ≤14 days post-onset) |
| **Specimen** | Cases missing stool samples entirely |
| **Notification** | Cases notified >14 or >60 days after onset |
| **Age Distribution** | Implausible ratios of cases under 5 vs. 5–14 years old |

---

## Impact

- **Published** in the [15th IMB Report (2017)](https://polioeradication.org/) — Blind Spot Identification Map, pages 32–33 & 39–40
- **Published** in *Vaccine X* (2020) — [PMC7090369](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7090369/) — wrote the methods section and generated all figures and tables
- Moved global health leaders from guesswork to **evidence-based prioritization** for supplemental immunization activities and resource deployment
- Methodology became a **peer-reviewed standard** for global health surveillance analytics

---

## Governance & Project Management

| Area | Approach |
|------|---------|
| **Data Dictionary** | Worked within standardized definitions shared across all WHO polio partners for case status and notification timelines |
| **Version Control** | Managed full R codebase on GitLab — all pipeline changes tracked for reproducibility and audit trail |
| **Stakeholder Communication** | Translated technical methodology into actionable visualizations for non-technical decision-makers at IMB and CDC leadership |
| **Quality Assurance** | Defined thresholds for each flag to systematically identify untrustworthy data, moving beyond simple performance measurement |

---

## Tools & Technologies

`R` · `SQL` · `GitHub / GitLab` · `WHO POLIS Database` · `WorldPop` · `tidyverse` · `lubridate` · `ggplot2` · `rgdal` · `geojsonio` · `readxl`

---

## Reproducibility

This analysis is **fully reproducible** given appropriate data access credentials to WHO POLIS. All scripts, custom functions, and flag logic are available in this repository.

---

## Role & Stakeholders

| | |
|-|---|
| **Role** | Sr. Data Analyst — CDC Global Immunization Division (2016–2019) |
| **Primary Stakeholders** | World Health Organization (WHO), Independent Monitoring Board (IMB) |
| **Collaborators** | GPEI partner organizations across 79 countries |

---

## References

- **Blind Spot Maps:** 15th IMB Report 2017, pages 32–33 & 39–40
- **Published Methods:** [PMC7090369 — Methods for surveillance performance](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7090369/) (*Vaccine X*, 2020)
- **Codebase:** [github.com/skhan890/surv_manuscript](https://github.com/skhan890/surv_manuscript)
