# NBA × WNBA Player Efficiency Rating Dashboard

**R-Ladies Atlanta × Atlanta Hawks · 2019**

> Interactive R Shiny dashboard comparing Player Efficiency Ratings across NBA and WNBA athletes — built and presented at the Atlanta Hawks facility, then used to teach R Shiny to CDC scientists and the Emory Sports Analytics team.

**Live Demo:** [skhan22.shinyapps.io/RLadies_Hawks](https://skhan22.shinyapps.io/RLadies_Hawks/)

---

## Background

As president of the CDC R Users Group and an adjunct instructor at Emory's Rollins School of Public Health, I was regularly training data scientists on how to use R. When I was invited to speak at R-Ladies Atlanta — hosted at the Atlanta Hawks facility in May 2019 — I had one goal: **make R compelling to a sports analytics audience**.

The challenge was real: sports people care about sports data, not public health epidemiology. So I built something new.

---

## The Data Problem

Surprisingly little comparative data on WNBA exists publicly. No cross-league PER comparison was available online. I:

1. **Hand-scraped** WNBA player biographical data (dates of birth, career years) from Wikipedia — because no structured source existed
2. Supplemented with automated scraping from **Basketball-Reference.com** (`3-scrape_dob.R`)
3. Merged NBA data from **Kaggle**
4. Filtered to players with careers beginning ≥1997 and standardized career timelines

---

## Key Questions

1. How do NBA and WNBA PERs compare across standardized career years?
2. Does career length (long vs. short) affect PER trajectories differently by league?
3. How does player age correlate with PER across leagues when controlling for career longevity?

---

## Dashboard Features

| Tab | What It Shows |
|-----|--------------|
| **Compare 2 Players** | PER trajectories for any two players overlaid on standardized career years (default: Diana Taurasi vs. Michael Jordan) |
| **Time Series** | Median PERs across career years for both leagues — aggregate comparison |
| **Age Analysis** | Median PER by player age, faceted by league and career length (5+ seasons = long career) |

---

## Technical Approach

| Step | What I Did |
|------|-----------|
| **Data Collection** | Basketball-Reference.com, Kaggle (NBA), Wikipedia (WNBA — hand-scraped + scripted) |
| **Processing** | `1-process.R` pipeline; age calculated in `4-age.R`; career standardization to normalize timelines |
| **Visualization** | `ggplot2` + `ggrepel` for PER curves with labeled calendar years |
| **App** | R Shiny (`app.R`) with reactive dropdowns; custom CSS (`styles.css`) |
| **Deployment** | shinyapps.io |

---

## Results & Impact

- Delivered live at **R-Ladies Atlanta × Atlanta Hawks** (May 2019)
- Invited by the **Emory Sports Analytics** team to present the methodology and dashboard
- Used as a teaching tool to demonstrate R Shiny to CDC scientists and Emory students
- Opened the conversation on the **data equity gap** in WNBA analytics — players exist, data doesn't

---

## Run Locally

```r
# Clone the repo
git clone https://github.com/skhan890/RLadies_Hawks.git
cd RLadies_Hawks

# Install dependencies
install.packages(c("shiny", "tidyverse", "ggplot2", "ggrepel"))

# Run
shiny::runApp("app.R")
```

---

## Tools & Technologies

`R` · `R Shiny` · `ggplot2` · `ggrepel` · `tidyverse` · `CSS` · `shinyapps.io` · `Basketball-Reference.com` · `Wikipedia (scraped)`

---

## Repository Structure

```
RLadies_Hawks/
├── app.R               # Main Shiny application
├── reference_app.R     # Reference implementation
├── styles.css          # Custom app styling
├── 1-process.R         # Data processing pipeline
├── 2-time_series.R     # Time series analysis
├── 3-scrape_dob.R      # Web scraping for dates of birth
├── 4-age.R             # Age calculations
├── pers_year.RDS        # Processed data file
├── data/               # Raw data directory
└── docs/               # Documentation
```

---

## Author

**Sara Khan** — CDC R Users Group President · Emory Adjunct Instructor · Sr. Data Analyst

Slides from the original presentation: [R-Ladies Atlanta Talk (Nov 2019)](https://skhan890.github.io/Info550Final)
