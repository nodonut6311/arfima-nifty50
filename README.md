# ARFIMA vs GARCH: Volatility Modeling for NIFTY 50

[Read Full Report on GitHub Pages](https://nodonut6311.github.io/arfima-nifty50/)

A comprehensive comparative study of ARFIMA and GARCH(1,1) models for estimating and forecasting volatility in the NIFTY 50 equity index.

---

## Project Overview

This research analyzes 7 years of NIFTY 50 data (May 2019 - May 2026) to:
- Estimate conditional volatility using two competing frameworks
- Demonstrate ARFIMA's superiority in capturing long-memory persistence
- Develop practical hedging strategies for portfolio managers
- Provide actionable risk management recommendations

Key Finding: ARFIMA(3, 0.1, 0) outperforms GARCH(1,1) across 4 independent metrics, with 24% better out-of-sample forecasting accuracy.

---

## Quick Results

| Metric | ARFIMA | GARCH | Winner |
|--------|--------|-------|--------|
| AIC | -20,337 | -781 | ARFIMA |
| BIC | -20,310 | -759 | ARFIMA |
| Log-Likelihood | 10,173.6 | 394.3 | ARFIMA |
| MAE (Forecast) | 0.00420 | 0.00555 | ARFIMA (24% better) |
| RMSE (Forecast) | 0.00448 | 0.00610 | ARFIMA (27% better) |

---

## Key Visualizations

### Return Distribution and Non-Normality

![NIFTY 50 Returns with KDE overlay showing fat tails](images/g1.png)

### ACF/PACF: Evidence of Long-Memory

![ACF and PACF plots showing 60/60 significant lags](images/g3.png)

### Hurst Exponent Analysis

![Log-log R/S analysis showing H approximately 0.60](images/g4.png)

### Static Forecasting (Problem)

![Static split forecasts missing volatility spike](images/g6.png)

### Rolling Window Forecasting (Solution)

![Rolling window forecasts capturing spike, ARFIMA superior](images/g5.png)

---

## Full Report

[Read the Complete Research Report on GitHub Pages](https://YOUR_USERNAME.github.io/arfima-nifty50/)

The full report includes:
- Executive Summary and Key Findings
- Data Description and Volatility Estimation (EWMA)
- Stationarity and Long-Memory Testing (ADF, ACF, Hurst)
- ARFIMA Model Specification and Lag Selection
- GARCH Specification and Comparison
- Out-of-Sample Forecasting Results
- Value at Risk (VaR) Analysis
- Hedging Recommendations and Risk Management Strategy
- Conclusions and Implementation Guidance

---

## Methodology

### Data

- Source: NIFTY 50 Index (yfinance, ticker: ^NSEI)
- Period: May 30, 2019 - May 30, 2026
- Observations: 1,727 daily closing prices, 1,726 log returns
- Volatility Measure: EWMA with lambda=0.94 (RiskMetrics standard)

### ARFIMA Specification

Model: ARFIMA(3, 0.1, 0)

σ_t = 0.0048 + 0.9753*σ_(t-1) + 0.1146*σ_(t-2) - 0.1049*σ_(t-3) + ε_t

Long-Memory Parameter: d = 0.10 (derived from Hurst exponent H approximately 0.60)

### GARCH Specification

Model: GARCH(1,1)

σ_t^2 = ω + α*r_(t-1)^2 + β*σ_(t-1)^2

Issue: α + β = 1.0 (unit root, contradicting stationarity)

---

## Key Insights

### Why ARFIMA Wins

1. Long-Memory Capture: Fractional integration (d=0.10) captures volatility persistence; GARCH's exponential decay is insufficient
2. Stationarity: ARFIMA maintains mean-reversion; GARCH degenerates to unit root
3. Empirical Validation: ACF shows hyperbolic (not exponential) decay, ARFIMA appropriate
4. Forecast Accuracy: 24-27% better out-of-sample predictions during volatility spikes

### When to Use Each Model

| Use Case | Recommended |
|----------|-------------|
| Intra-day trading (less than 1 day) | GARCH |
| Medium-term forecasting (3-10 days) | ARFIMA |
| Risk management and hedging | ARFIMA |
| Tail risk estimation (VaR) | ARFIMA |

---

## Practical Recommendations

### For Risk Managers

1. Daily Risk Limit: Use ARFIMA 99% VaR (2.30 crores for 100 crore portfolio)
2. Hedging: Buy 1-month protective puts (costs 1.5%, protects 2.3% loss)
3. Rebalancing: Weekly (not daily) based on volatility thresholds
4. Monitoring: Re-estimate ARFIMA quarterly to verify d stability

### For Traders

1. Short-term: Use GARCH for intra-day spikes
2. Medium-term: Use ARFIMA for 3-10 day forecasts
3. Long-term: Use ARFIMA with caution (d may shift in regime changes)

---

## Technical Stack

- Language: Python 3.12
- Data: yfinance
- Analysis: pandas, numpy, scipy, statsmodels
- Visualization: matplotlib, seaborn
- GARCH: arch library
- GitHub Pages: Jekyll with MathJax for LaTeX rendering

---

## Repository Structure
