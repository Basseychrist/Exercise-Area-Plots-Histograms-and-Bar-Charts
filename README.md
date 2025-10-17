# Area Plots, Histograms, and Bar Charts — Exploring Immigration to Canada (1980–2013)

## Project purpose

This project is a concise, hands-on exploration of foundational data visualization techniques in Python (Matplotlib + Pandas) using a real dataset: Immigration to Canada from 1980 to 2013. The notebook demonstrates how to choose and tune common plot types to answer concrete questions about patterns, distributions, and rankings in the data.

At a glance, you will:

- Load a cleaned dataset of annual immigrant counts by country.
- Build area plots (stacked and unstacked) to compare trends over time.
- Use histograms to understand distributions and variability.
- Create bar charts (vertical and horizontal) to compare totals and annotate events.

The goal is not only to produce charts, but to show why each type of analysis is appropriate and what decisions it informs.

## Data

- Source: United Nations — International migration flows (cleaned dataset provided in the lab)
- File: Loaded directly in the notebook from a hosted CSV (no local download required)
- Scope: Annual immigrant counts to Canada by country, 1980–2013

Key data preparation in the notebook:

- Set the country names as the DataFrame index for easier `.loc` selection.
- Maintain a `years` list of string columns from 1980 to 2013 for consistent slicing/plotting.
- Sort by `Total` when deriving “top” or “least” contributing countries.

## Why each analysis and visualization was needed

### 1) Area plots (trends over time)

Area plots are line plots with filled areas; they’re ideal for seeing how magnitudes evolve year-over-year and, when stacked, how components contribute to a cumulative total.

- Top 5 countries — unstacked area plot

  - Why: Compare the trend shape and magnitude for the largest contributors without the stacked fill obscuring individual series.
  - Insight: Highlights whether leading countries grow steadily, accelerate, or plateau over time.

- Top 5 countries — area plot with transparency (`alpha`)

  - Why: Transparency reduces visual clutter where series overlap, making multi-series comparisons clearer.

- Least 5 countries — stacked area plot (scripting layer)
  - Why: Stacking emphasizes the cumulative contribution of the long tail and shows how even small contributors add up.
  - Insight: Reveals whether the long tail is stable or varies, and how its total changes year-to-year.

When to use area plots:

- You care about trajectories (time series) and relative magnitudes across groups.
- You want to highlight cumulative contributions (stacked) or preserve individual shapes (unstacked).

### 2) Histograms (distribution and variability)

Histograms answer “how are values distributed?” by binning counts. They surface skew, modality, and outliers.

- 2013 immigration counts — single histogram

  - Why: Understand the overall distribution across all countries in a single year.
  - Insight: Shows long-tail behavior (many small contributors, few large), helps pick sensible scales or thresholds.

- Denmark, Norway, Sweden — overlapping histograms

  - Why: Compare the distribution of annual counts for multiple countries across 1980–2013.
  - Insight: Which country tends to have higher/lower typical counts and how spread/volatile their yearly values are.

- Greece, Albania, Bulgaria — overlapping histograms with bins and transparency
  - Why: Control bin granularity (`bins=15`) for better resolution; transparency (`alpha`) keeps overlaps readable.

When to use histograms:

- You need to see value frequency, detect skew/outliers, or compare spread across groups.

### 3) Bar charts (rankings and event-focused comparisons)

Bar charts excel at categorical comparisons and ranking.

- Iceland (1980–2013) — vertical bar chart with annotation

  - Why: Year-by-year bars make it easy to annotate and visually connect changes to real-world events (e.g., the 2008–2011 financial crisis).
  - Insight: A clear before/after pattern around the crisis, supporting a causal narrative.

- Top 15 countries by total — horizontal bar chart with labels
  - Why: Horizontal layout improves readability for long labels (country names). Labeling each bar with totals makes precise comparison immediate.
  - Insight: A ranked view of contributors exposes concentration (which countries dominate) and the long tail.

When to use bar charts:

- You’re ranking categories, comparing totals, or highlighting specific years/events with annotations.

## What decisions these visuals support

- Resource planning: Understand which source countries drive the majority of arrivals and how that has changed.
- Policy focus: Identify patterns (growth, decline, volatility) that may warrant country-specific engagement.
- Communication: Annotated charts tie data to events, helping stakeholders grasp context quickly.

## Repository contents

- `DV0101EN-Exercise-Area-Plots-Histograms-and-Bar-Charts--v2.ipynb` — The notebook with all code and plots.
- `README.md` — This document.

## How to run (quick start)

1. Open the notebook in VS Code or Jupyter and run cells top-to-bottom. The first cell installs NumPy, Pandas, and Matplotlib and sets the plotting style.

Optional (PowerShell) — create an isolated environment and install dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install numpy pandas matplotlib
```

Then open the notebook and execute all cells.

## Notes and assumptions

- Years are treated as strings (`"1980"` … `"2013"`) to match CSV column labels; indices are cast to `int` for plotting when needed.
- `mpl.style.use('ggplot')` is applied for readability; adjust to your preferred style if desired.
- The dataset is fetched from a public URL at runtime; make sure you have an internet connection.

## Acknowledgments

This exercise is adapted from IBM Skills Network materials on data visualization. Data originates from the United Nations’ migration flows datasets. The notebook demonstrates educational patterns and techniques for exploratory analysis.

---

## Executive summary

This repository demonstrates how to use area plots, histograms, and bar charts to extract insight from Canada’s immigration data (1980–2013). You will learn how different charts answer different questions: trends over time (area), distributions across countries or years (histograms), and categorical rankings or event-focused comparisons (bar charts). The notebook is a teaching artifact: it favors clarity and explicit steps over compact code.

## Background and guiding questions

Immigration flows are long-tailed and time-varying. Typical questions include:

- Which countries contribute the most/least immigrants over the full period?
- How do contributions evolve over time—steady growth, surges, or plateaus?
- What does the distribution of annual contributions look like within a year and across years?
- How do real-world events (e.g., the 2008–2011 Icelandic financial crisis) show up in the data?

The notebook is structured to answer these with small, progressively refined visuals.

## Methodology and notebook map

The notebook is organized into the following sections (run from top to bottom):

1. Import Libraries — install/import packages, set `%matplotlib inline`, and a readable style.
2. Fetching Data — load CSV, set country index, prepare the `years` list.
3. Area Plots — sort/select groups, transpose to plot time series, tweak stacking and transparency.
4. Histograms — examine distributions in one year and across years; control bins and ticks.
5. Bar Charts — annotate events (Iceland) and rank top contributors with labels.

## Design choices and alternatives

- Stacked vs unstacked area charts: use stacked to emphasize cumulative totals; unstacked to compare shapes.
- Transparency (`alpha`): reduce overlap clutter (typical values 0.25–0.6).
- Histogram bins: trade off smoothness vs. detail; align `xticks` with `bin_edges` for truthful axes.
- Color and figsize: muted, readable palettes; large figures for multi-series clarity.
- Types: keep `years` as strings to match columns; cast to `int` only for plotting axes when useful.

## Interpreting the visuals

- Long tail: many small contributors and few large ones (2013 histogram, top-15 bars).
- Trend dynamics: unstacked areas reveal growth patterns and inflection points among leaders.
- Tail behavior: stacked areas for least 5 show whether the tail meaningfully varies over time.
- Event context: annotated Iceland bars tie data to 2008–2011 crisis, aiding stakeholder communication.

## Reproducibility and environment

- Minimal dependencies (NumPy, Pandas, Matplotlib); internet needed for CSV.
- The final cell prints Python and kernel versions for traceability.
- Optional isolation: use a virtual environment to avoid dependency conflicts.

## Troubleshooting

- If plots don’t render, ensure `%matplotlib inline` ran and a Python kernel is active.
- If labels overlap, increase `figsize`, rotate ticks, or limit the number of series shown.

## Limitations and future work

- Descriptive exploration only; causal claims need more context and variables.
- Totals are not normalized per capita; consider population scaling.
- Possible extensions: regional aggregation, interactive Plotly charts, forecasting, changepoint analysis.

## References

- Pandas plotting: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.plot.html
- Matplotlib annotate: https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.annotate.html
- UN migration data portal: https://www.un.org/development/desa/pd/data/international-migration-flows
