# 📈 Cross-Sector Statistical Arbitrage: GS vs META

[![Python 3.9+](https://img.shields.io/badge/python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)

> **A Cointegration-Based Mean Reversion Strategy applied to U.S. Mega-Caps.**

This repository contains the research, backtesting framework, and production-ready object-oriented engine for a market-neutral statistical arbitrage strategy. The model exploits structural mean-reversion between Financials (Goldman Sachs) and Tech (Meta Platforms) using the Engle-Granger cointegration framework.

📖 **Read the full Quantitative Whitepaper:** [Link to your Notion/PDF here]

---

## 📊 Institutional Tear Sheet (Out-of-Sample Results)

The strategy was tested using a rigorous Out-of-Sample approach, incorporating a realistic **$0.10 per trade** transaction cost (slippage and commissions) to prevent theoretical over-performance.

| Metric | Value | Note |
| :--- | :--- | :--- |
| **Net Annualized Return** | `11.96%` | *Post-transaction costs* |
| **Annualized Volatility** | `11.31%` | *Daily frequency* |
| **Sharpe Ratio (Rf=4%)** | `0.70` | *Conservative risk-adjusted return* |
| **Maximum Drawdown** | `-5.59%` | *Highly asymmetric risk profile* |
| **Win Rate** | `48.53%` | *Compensated by high risk-reward ratio* |

*Note: The exceptionally low Maximum Drawdown (<6%) makes this strategy highly suitable for institutional leverage.*

---

## 🧠 Alpha Thesis & Core Logic

1. **Cointegration over Correlation:** Replaces unstable linear correlation with long-term stationary equilibrium ($I(0)$ residuals via ADF test).
2. **Dynamic Hedge Ratio ($\beta$):** Calculated via rolling Ordinary Least Squares (OLS) to ensure strict market-neutrality against broader S&P 500 directional moves.
3. **Z-Score Trigger:** Adaptive entry signals ($Z > 2.25$ and $Z < -2.25$) filtered through a 50-day rolling window to prevent look-ahead bias and adjust to market regime shifts.

---

## 📂 Repository Structure

To facilitate both code review and production integration, the repository is structured as follows:

```text
├── src/                  # Production-Ready OOP Engine
│   ├── engine.py         # PairsTradingEngine class definition
│   ├── data_loader.py    # Data ingestion and preprocessing scripts
│   └── risk_manager.py   # Position sizing and transaction cost logic
├── research/             # Jupyter Notebooks for R&D
│   ├── 01_cointegration_screening.ipynb
│   ├── 02_hedge_ratio_and_zscore.ipynb
│   └── 03_stress_test_and_heatmap.ipynb
├── docs/                 # Documentation and Whitepaper
│   └── Quant_Whitepaper_GS_META.pdf
├── requirements.txt      # Python dependencies
└── README.md
