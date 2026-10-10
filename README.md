# Stock Returns Analyser

Quantitative return analysis across a diversified 8-asset basket spanning US equities, UK-listed stocks, and broad market indices — implemented in Python.

# Project Overview

This project pulls daily adjusted closing prices for 8 tickers over a 4-year window (2021–2024) and computes key return and risk metrics for each asset. The goal is to demonstrate how different asset classes perform on a risk-adjusted basis and to visualise the relationship between volatility and return across geographies and sectors.

Assets covered: US mega-cap tech (AAPL, META), speculative growth (PLTR, TSLA), UK-listed equities (LLOY.L, BP.L), and broad market indices (SPY, ^FTSE).

# Metrics Calculated
Daily log returns — ln(Pᵢ / Pᵢ₋₁) using the 252 trading day convention
Annualised return — mean daily log return × 252
Annualised volatility — standard deviation of daily returns × √252
Sharpe ratio — annualised return ÷ annualised volatility (no risk-free rate adjustment)
# Summary Statistics (2021–2024)
Ticker	Annualised Return	Annualised Volatility	Sharpe Ratio
AAPL	21.60%	26.61%	0.81
BP.L	9.78%	28.08%	0.35
LLOY.L	7.76%	26.95%	0.29
META	15.94%	45.99%	0.35
PLTR	35.05%	66.06%	0.53
SPY	15.59%	16.63%	0.94
TSLA	11.24%	59.66%	0.19
^FTSE	5.29%	12.67%	0.42
# Visualisations

The notebook produces four charts using Plotly:

1. Daily log returns — time series of all 8 tickers with y-axis locked to [-0.3, 0.3], showing periods of elevated volatility across assets

<img width="523" height="333" alt="Screenshot 2026-10-11 at 00 06 46" src="https://github.com/user-attachments/assets/eab2ce53-3fcc-431b-ba42-03c653b1426c" />


2. Return distributions — overlapping histograms of daily log returns per ticker, illustrating the difference in spread (risk) between assets

<img width="523" height="333" alt="Screenshot 2026-10-11 at 00 07 08" src="https://github.com/user-attachments/assets/84df26fa-856a-4d51-8ac6-c376804c6627" />

3. Risk vs return scatter — each asset plotted by annualised volatility (x) against annualised return (y), with bubble size encoding the Sharpe ratio — assets in the top-left with large bubbles are the best risk-adjusted performers

<img width="523" height="333" alt="Screenshot 2026-10-11 at 00 08 05" src="https://github.com/user-attachments/assets/e5252f5d-6c27-49af-a226-ad7db0edb6fc" />

4. Cumulative £1 performance — shows the growth of £1 invested in each asset from January 2021, making the real-world outcome of each risk profile tangible

<img width="517" height="333" alt="Screenshot 2026-10-11 at 00 08 30" src="https://github.com/user-attachments/assets/273e2c7c-96b2-4fef-82fb-780352bac585" />

# Key Findings

SPY achieved the highest Sharpe ratio (0.94) — the diversified S&P 500 index outperformed every individual stock on a risk-adjusted basis over this period, consistent with the efficient markets hypothesis.

TSLA had the lowest Sharpe ratio (0.19) — despite extreme volatility of 59.7% annualised, it returned only 11.2% annually — the worst risk-reward trade-off in the basket.

PLTR delivered the highest raw return (35%) driven almost entirely by its AI-driven rally in late 2024, but with 66% annualised volatility the ride was extremely turbulent.

The UK cluster (LLOY.L, BP.L, ^FTSE) sits bottom-left of the scatter plot — low volatility but near-zero real returns over the period, illustrating the underperformance of UK equities relative to US markets.

META's 2022 crash is visible in both the distribution (wide spread) and cumulative chart (dip to ~£0.50 before a full recovery), explaining its high volatility despite a reasonable 4-year return.

# Requirements
yfinance
pandas
numpy
plotly
bash
pip install yfinance pandas numpy plotly
# Usage

Open stock_return_analyser.ipynb in Jupyter Notebook or JupyterLab and run all cells top to bottom. Data is pulled live from Yahoo Finance — no manual download needed.

Note: Always run cells in order from the top. Variables are lost on kernel restart and must be re-computed by running each cell sequentially.

# Reflections

This project was built as a learning exercise in my first year of university to apply Python to real financial data across multiple asset classes. It demonstrates:

Pulling and manipulating multi-asset financial time series with pandas and yfinance
Computing log returns, annualised risk/return metrics, and Sharpe ratios using numpy
Building a four-chart analytical suite using plotly.express and plotly.graph_objects
Interpreting results across geographies (US vs UK) and asset types (growth, value, index)

The Sharpe ratio used here is a simplified version with no risk-free rate adjustment. Currency differences between USD-denominated and GBP-denominated assets are not normalised — returns are computed on percentage changes, so currency of pricing does not affect the calculation.

# Author

Ryan James Forrester — BSc Economics and Finance, Leeds Beckett University
LinkedIn
