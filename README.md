# Income Trajectories and Self-Employment

## Overview
This project studies longitudinal income trajectories using National Longitudinal Survey of Youth data. The analysis compares salaried and self-employed workers over age, cleans person-year records, visualizes income patterns, and fits weighted mixed-effects models to explain log income over time.

## Problem Statement
Estimate how income changes with age and employment type while accounting for repeated observations within individuals, survey weights, demographics, education, ability measures, hours worked, race, sex, and cohort membership.

## Key Features
- Cleans and reshapes longitudinal person-year data from an NLSY `.dta` file.
- Handles missing values with within-person interpolation and forward/backward filling where appropriate.
- Creates centered and scaled predictors for weighted mixed-effects models.
- Visualizes raw income distributions, age patterns, hours worked, and smoothed income trajectories by race and sex.
- Compares a sequence of WeMix models using log likelihood, AIC, BIC, delta AIC, and Akaike weights.
- Produces subject-level actual-vs-predicted log-income diagnostics.

## Data Source
The analysis uses an NLSY Stata file named `NLSY.dta`, originally loaded from a local path. The dataset itself is not committed. Add the data file under `data/` or set the `NLSY_DTA` path in `.Renviron` after copying `.Renviron.example`.

## Methods and Tools
- Quarto
- R, haven, janitor, dplyr, tidyr, ggplot2, lme4, emmeans, performance, broom.mixed, WeMix, splines, tibble, purrr, knitr, kableExtra
- Weighted mixed-effects modeling, longitudinal EDA, model comparison, prediction diagnostics

## How to Run Locally
1. Install R and Quarto.
2. Copy `.Renviron.example` to `.Renviron` and update `NLSY_DTA`.
3. Place `NLSY.dta` in `data/` or update the environment variable to your local file.
4. If using cached WeMix model objects, place `wm1.rds` through `wm5.rds` in the model cache directory.
5. Render the report:

```bash
quarto render scr.qmd
```

Install R packages:

```r
install.packages(c(
  "haven", "janitor", "dplyr", "tidyr", "ggplot2", "lme4",
  "emmeans", "performance", "broom.mixed", "WeMix", "tibble",
  "purrr", "knitr", "kableExtra"
))
```

## Required Packages
- `haven`
- `janitor`
- `dplyr`
- `tidyr`
- `ggplot2`
- `lme4`
- `emmeans`
- `performance`
- `broom.mixed`
- `WeMix`
- `splines`
- `tibble`
- `purrr`
- `knitr`
- `kableExtra`

## Main Files to Review
- `scr.qmd`: source analysis and modeling workflow.
- `Report.html`: rendered report output.
- `Presentation.pptx`: project presentation deck.
- `.Renviron.example`: placeholder data and model-cache paths.

## Screenshots
Screenshots are not committed yet. Suggested additions:

- `screenshots/income-density-by-employment.png`
- `screenshots/income-trajectories-by-race-sex.png`
- `screenshots/model-comparison-table.png`
- `screenshots/actual-vs-predicted-log-income.png`

## Limitations
- The raw NLSY `.dta` file is not committed.
- Cached `wm1.rds` through `wm5.rds` model files are referenced by the report but are not committed.
- A fresh run requires recreating the cached WeMix models or pointing `MODEL_CACHE_DIR` to existing model files.
- Complete-case filtering after imputation may affect representativeness.

## Future Improvements
- Add a data dictionary for all modeled NLSY variables.
- Include the model-cache creation step or remove cache dependence.
- Add screenshots from the rendered report and a concise headline-results table.

