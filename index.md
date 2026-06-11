---
layout: default
title: ARFIMA vs GARCH Volatility Modeling
---

# ARFIMA vs GARCH: Volatility Modeling for NIFTY 50

**Research Project on Long-Memory Volatility Dynamics**

---

## Executive Summary

This research compares ARFIMA(3, 0.1, 0) and GARCH(1,1) models for 
forecasting NIFTY 50 index volatility over 7 years (May 2019 - May 2026).

### Key Findings

- **ARFIMA is superior**: Better AIC (-20337 vs -781), BIC (-20310 vs -759)
- **Out-of-sample performance**: 15% lower MAE, 20% lower RMSE
- **Volatility persistence**: d = 0.10 captures long-memory; GARCH at unit root
- **Risk management**: ARFIMA gives 18% higher VaR (more conservative)

### Quick Links

📊 [Read Methodology & Formulas](methodology.html)
📈 [View Results & Recommendations](results.html)
💾 [View Code on GitHub](https://github.com/YOUR_USERNAME/arfima-nifty50)

---

## Key Results at a Glance

| Metric | ARFIMA | GARCH | Winner |
|--------|--------|-------|--------|
| AIC | -20,337 | -781 | ✓ ARFIMA |
| BIC | -20,310 | -759 | ✓ ARFIMA |
| MAE (forecast) | 0.0041 | 0.0048 | ✓ ARFIMA |
| RMSE (forecast) | 0.0044 | 0.0055 | ✓ ARFIMA |

---

## About This Research

NIFTY 50 volatility exhibits **long-memory persistence** (d = 0.10) that 
standard GARCH models miss. ARFIMA's fractional integration better captures 
this structure, leading to superior risk forecasts.

**Practical Impact:**
- Better hedging strategies
- More accurate tail risk (VaR) estimation
- Improved portfolio rebalancing frequency

---

*Last updated: June 2026*
