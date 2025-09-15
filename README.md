
# 📊 MScFE690 Capstone Project  
## Estimating Value-at-Risk (VaR) and Expected Shortfall (ES) Across Multi-Asset Portfolios  

![Python](https://img.shields.io/badge/python-3.10%2B-blue)  
![License](https://img.shields.io/badge/license-MIT-green)  
![Status](https://img.shields.io/badge/status-Completed-success)  
![Platform](https://img.shields.io/badge/platform-Jupyter%20Notebook-orange)  

WorldQuant University | MSc in Financial Engineering  
**Team:** Nicholas Johnson & Bryan Mutua  
**Advisor:** Kenneth Abbott  

---

### 📁 Table of Contents  
- [🔍 Project Overview](#-project-overview)  
- [📌 Objectives](#-objectives)  
- [📈 Methodology](#-methodology)  
- [📊 Asset Classes Analyzed](#-asset-classes-analyzed)  
- [💻 File Structure](#-file-structure)  
- [📦 Requirements](#-requirements)  
- [📎 Data Sources](#-data-sources)  
- [📌 Results Snapshot](#-results-snapshot)  
- [📊 Insights](#-insights)  
- [🧠 Future Enhancements](#-future-enhancements)  
- [🔗 License & Acknowledgements](#-license--acknowledgements)  

---

### 🔍 Project Overview  
This project evaluates **portfolio risk across multiple asset classes** using several Value-at-Risk (VaR) and Expected Shortfall (ES) methodologies:  

- Parametric (Variance–Covariance)  
- Historical Simulation  
- Monte Carlo Simulation (parametric & bootstrap)  
- Extreme Value Theory (EVT) using Generalised Pareto Distribution  

We test how models perform under **normal vs. stressed market regimes** and whether portfolio diversification reduces **tail risk exposure**.  

---

### 📌 Objectives  
- Implement multiple VaR and ES methodologies using financial time series (2010–2024).  
- Assess model performance under calm vs. stressed volatility regimes (VIX > 30).  
- Compare risk/return profiles across equities, commodities, bonds, crypto, and forex.  
- Backtest models with Kupiec, Christoffersen, and Lopez tests.  
- Construct, optimise, and rank multi-asset portfolios by risk-adjusted performance.  

---

### 📈 Methodology  
1. **Data Collection** – Yahoo Finance (`yfinance`) OHLCV data (2010–2024).  
2. **Exploratory Analysis** – Returns, volatility, correlations, tail behaviour.  
3. **Risk Modelling** – Parametric, Historical, Monte Carlo, and EVT-based VaR/ES.  
4. **Backtesting** – Kupiec test, Christoffersen conditional coverage, Lopez Loss.  
5. **Portfolio Construction** – 1,000 random multi-asset portfolios optimised by Sharpe, Sortino, and Jensen’s Alpha.  
6. **Ranking & Stress Testing** – Top 10% portfolios re-evaluated under stress.  
7. **Regime Segmentation** – Compare model reliability in normal vs. high-volatility regimes.  

---

### 📊 Asset Classes Analyzed  

| Category       | Assets |
|----------------|--------|
| **Equities (SPDR ETFs)** | SPY, XLF, XLE, XLK, XLV, XLY, XLP, XLRE |
| **Commodities** | GC=F (Gold), BZ=F (Brent Crude), HG=F (Copper), ZC=F (Corn) |
| **Bonds (ETFs)** | TLT, SHY, BND, LQD, EMB |
| **Cryptocurrencies** | BTC-USD, ETH-USD |
| **Forex** | EURUSD=X, USDJPY=X, AUDUSD=X, USDCAD=X |  

---

### 💻 File Structure  

```

├── data/                     # Raw and cleaned datasets
├── notebooks/                # Jupyter notebooks for analysis
│   ├── VaR\_ES\_Analysis.ipynb # Main notebook (CL=99, ES=97.5)
├── results/                  # Charts, tables, and summaries
├── requirements.txt          # Python dependencies
├── README.md                 # Project documentation

````

---

### 📦 Requirements  

Install dependencies with:  

```bash
pip install -r requirements.txt
````

---

### 📎 Data Sources

* **Yahoo Finance (`yfinance`)** – OHLCV price data.
* **CBOE VIX Index** – Regime classification (normal vs. high volatility).

---

### 📌 Results Snapshot

| Method                  | Avg. Exception Rate | Kupiec p | Christoffersen p | Lopez Loss | Notes                           |
| ----------------------- | ------------------- | -------- | ---------------- | ---------- | ------------------------------- |
| Parametric (Normal)     | \~4.8%              | 0.07     | 0.03             | Medium     | Slight underestimation          |
| Historical Simulation   | \~5.2%              | 0.09     | 0.04             | Low        | Best in calm periods            |
| Monte Carlo (Normal)    | \~4.6%              | 0.06     | 0.02             | Medium     | Similar to Parametric           |
| Monte Carlo (Bootstrap) | \~5.3%              | 0.08     | 0.04             | Medium     | More noise under stress         |
| EVT (GPD)               | \~0%                | 0.00     | 1.00             | High       | Very conservative (no breaches) |

---

### 📊 Insights

* **Normal Regimes** – Historical and Bootstrap MC methods perform best.
* **High-Volatility Regimes** – Traditional models underestimate risk; EVT avoids breaches but is overly conservative.
* **Portfolios** – Equities + crypto portfolios showed clustered drawdowns (e.g., COVID-19 shock), reducing diversification benefits.

---

### 🧠 Future Enhancements

* Add **Filtered Historical Simulation (FHS)** with GARCH volatility.
* Use **dynamic EVT thresholds** to improve tail fitting.
* Implement **ensemble model ranking** across multiple backtest metrics.
* Extend analysis into a **real-time risk monitoring dashboard**.

---

### 🔗 License & Acknowledgements

This project was developed as part of the **WorldQuant University MScFE Capstone (2025)**.
We thank our advisor **Kenneth Abbott** for his guidance and feedback.

---

## ✅ requirements.txt

```txt
pandas
numpy
scipy
matplotlib
seaborn
yfinance
pandas-datareader
copulas
statsmodels
tqdm
joblib
```

