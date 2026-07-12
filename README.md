# Project 1: Data Collection and Initial Analysis of Stock Market Data

Exploratory data analysis of the **Daily Historical Stock Prices (1970–2018)** dataset,
completed for the Diploma in Data Analysis and Artificial Intelligence at Willis College.

## Overview

This project cleans, segments, and analyzes ~21 million daily stock price records
(1970–2018) across 6,460 tickers, joined with sector/industry reference data, to surface
decade-over-decade trends in price levels, trading volume, volatility, and sector
composition.

## Repository Contents

| File | Description |
|---|---|
| `Project1_Stock_Market_EDA.ipynb` | Full, executed Jupyter notebook — data loading, cleaning, decade segmentation, summary statistics, and all visualizations. |
| `Project1_Technical_Report.pdf` | Technical report summarizing methodology, findings, and hypotheses for further analysis. |
| `figures/` | Exported PNG charts (monthly close, volume histograms, High/Low boxplots, sector composition). |
| `outputs/decade_summary_statistics.csv` | Decade-level summary statistics (mean, median, std) for Open, High, Low, Close, and Volume. |

## Data Sources

- `historical_stocks.csv` — 6,460 tickers with exchange, company name, sector, and industry.
- `historical_stock_prices.csv` — ~21.0 million daily price records (Open, High, Low,
  Close, Adjusted Close, Volume), 1970-01-02 to 2018-08-24.

Both files are provided by the course and are not included in this repository due to size
(~2 GB); place them in the project root before running the notebook.

## Methodology Summary

1. **Load** both CSVs with memory-efficient dtypes (`float32`, `category`) to keep the
   ~21-million-row price file comfortably within memory.
2. **Clean**: checked for missing values, duplicate `(ticker, date)` records, and
   logically invalid rows (48 rows with High < Low were removed). Missing
   sector/industry values were labeled `'UNKNOWN'` rather than dropped.
3. **Segment**: merged sector/industry onto the price data, derived a `decade` column,
   and split the dataset into five per-decade DataFrames (1970s–2010s).
4. **Analyze**: computed summary statistics and produced time series, histogram, boxplot,
   and sector-composition visualizations for each decade.
5. **Compare & hypothesize**: documented cross-decade trends and proposed hypotheses
   (survivorship bias, crisis-driven volatility, sector effects, market microstructure
   changes) for follow-up analysis in later projects.

## Key Findings

- Ticker coverage grows from 93 (1970s) to 5,685 (2010s) tickers.
- Median Close price rises from $2.79 (1970s) to $20.01 (2010s).
- Average intraday volatility ((High − Low) / Close) peaks at 3.90% in the 2000s,
  consistent with the dot-com crash and 2008 financial crisis.
- Median daily volume dips through the 1980s–1990s before recovering by the 2010s, even
  as mean volume rises throughout — evidence of a changing mix of large vs. small,
  liquid vs. illiquid listings over time.

See `Project1_Technical_Report.pdf` for full methodology, figures, and discussion.

## How to Run

```bash
pip install pandas numpy matplotlib jupyter
jupyter nbconvert --to notebook --execute --inplace Project1_Stock_Market_EDA.ipynb
```

## Author

Jean Billa — Diploma in Data Analysis and Artificial Intelligence, Willis College
