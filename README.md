# 📊 MScFE690 Capstone Project  
## Estimating Value-at-Risk (VaR) and Expected Shortfall (ES) Using Traditional, Simulation, and EVT-Based Methods Across Multi-Asset Portfolios  
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
- [📌 Key Findings (Work In Progress)](#-key-findings-work-in-progress)  
- [🧠 Future Enhancements](#-future-enhancements)  
- [🔗 License & Acknowledgements](#-license--acknowledgements)

---

### 🔍 Project Overview  
This project evaluates **portfolio risk across multiple asset classes** using several Value-at-Risk (VaR) and Expected Shortfall (ES) methodologies. The study compares:  
- Parametric (Variance–Covariance)  
- Historical Simulation  
- Monte Carlo Simulation (parametric & bootstrap)  
- Filtered Historical Simulation (FHS) with GARCH volatility modeling  
- Extreme Value Theory (EVT) using Peaks-Over-Threshold and Generalized Pareto Distribution  

The primary goal is to **compare how different risk models behave under normal and stressed market conditions**, and to test whether portfolio diversification reduces tail risk.

---

### 📌 Objectives  
- Implement multiple VaR and ES methodologies using real financial time series data.  
- Assess risk under calm vs. stressed regimes (e.g., COVID-19 crash).  
- Compare asset-class behaviors: equities, commodities, bonds, crypto, forex.  
- Evaluate the consistency and biases of traditional vs. EVT-based tail risk estimates.  
- Explore multi-asset portfolio diversification and risk-return trade-offs.  

---

### 📈 Methodology  
- Retrieve OHLCV data (2010–2024) from Yahoo Finance using `yfinance`.  
- Audit, align, and clean datasets across asset classes.  
- Calculate log returns, distributions, correlations, and rolling volatility.  
- Compute **VaR and ES at 95% confidence** using all methods.  
- Apply GARCH(1,1) for FHS and GPD for EVT tails.  
- Visualize results: distributions, rolling correlations, volatility clusters, VaR/ES comparisons.  

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

```bash
📁 WQU_Capstone/
│
├── 01_data_cleaning_and_returns.ipynb   # Data retrieval, cleaning & returns
├── 02_var_es_methods.ipynb              # Parametric, Historical, Monte Carlo VaR & ES
├── 03_evt_model.ipynb                   # EVT diagnostics & GPD-based VaR/ES
├── 04_portfolio_simulation.ipynb        # Portfolio construction & optimization (in progress)
├── requirements.txt                     # Python dependencies
├── results/                             # Figures, tables & CSV outputs
└── README.md                            # Project overview (this file)
````

---

### 📦 Requirements

Install dependencies:

```bash
pip install -r requirements.txt
```

**Main libraries:** pandas, numpy, matplotlib, seaborn, plotly, scipy, statsmodels, arch, scikit-learn, yfinance

---

### 📎 Data Sources

* Yahoo Finance (`yfinance`) – OHLCV daily data (2010–2024)
* FRED (planned, for macro indicators)
* Supporting academic literature: SSRN, JFQA, Investopedia

---

### 📌 Key Findings (Work In Progress)

* **Risk hierarchy across assets:**

  * Cryptocurrencies (ETH, BTC) show the highest daily risk (VaR ≈ 6–9%, ES ≈ 9–12%).
  * Commodities (e.g., Brent, Gold) exhibit heavier tails than equities.
  * Bonds and FX pairs remain least risky (VaR < 1%).
* **Methodology consistency:**

  * Parametric VaR ≈ Monte Carlo (parametric).
  * Historical VaR ≈ Monte Carlo (bootstrap).
  * EVT VaR is slightly more conservative in high-volatility assets.
* **Diversification effects:**

  * Equities became highly correlated during COVID-19, reducing diversification.
  * Multi-asset portfolios (equities + bonds + commodities) maintain lower aggregated VaR.
* **Volatility clustering:**

  * FHS with GARCH captures volatility spikes (e.g., 2020 pandemic shock).

📌 Full tables, plots, and rolling analyses are stored in `/results/`.

---

### 📊 Results Summary (Selected Assets, 1-Day @ 95% Confidence)

| Asset       | Parametric VaR | Historical VaR | MC (Parametric) | MC (Bootstrap) | EVT VaR | Parametric ES |
| ----------- | -------------- | -------------- | --------------- | -------------- | ------- | ------------- |
| **SPY**     | 2.01%          | 1.86%          | 1.96%           | 1.86%          | 1.87%   | 2.52%         |
| **BTC-USD** | 7.27%          | 6.45%          | 7.18%           | 6.46%          | 6.58%   | 9.11%         |
| **ETH-USD** | 9.27%          | 8.07%          | 9.12%           | 8.08%          | 8.36%   | 11.63%        |
| **TLT**     | 1.68%          | 1.62%          | 1.69%           | 1.63%          | 1.59%   | 2.10%         |

📌 Notes:

* VaR estimates are consistent across methods.
* EVT and ES capture heavier tails for high-volatility assets (crypto).
* Bonds (TLT) remain the most stable with lowest tail risk.

---

### 📊 Portfolio-Level Results Summary (1-Day @ 95% Confidence)

| Portfolio Type                                                             | Parametric VaR | Historical VaR | MC (Parametric) | MC (Bootstrap) | EVT VaR | Parametric ES |
| -------------------------------------------------------------------------- | -------------- | -------------- | --------------- | -------------- | ------- | ------------- |
| **Equities Only (SPY + Sectors)**                                          | \~2.5%         | \~2.3%         | \~2.4%          | \~2.3%         | \~2.4%  | \~3.0%        |
| **Diversified Multi-Asset** (Equities + Bonds + Commodities + FX + Crypto) | \~1.8%         | \~1.7%         | \~1.8%          | \~1.7%         | \~1.8%  | \~2.3%        |

📌 Notes:

* Diversification reduces overall tail risk compared to equities-only portfolios.
* During stressed periods (e.g., COVID-19), correlations spike, limiting diversification.
* EVT-based VaR is more conservative in multi-asset settings.

---

### 🧠 Future Enhancements

* Extend analysis to **multi-period (10-day) VaR** for Basel alignment.
* Incorporate **time-varying correlation models (DCC-GARCH)**.
* Stress-testing with **non-Gaussian distributions** (t-copula, skew-t).
* Add **portfolio optimization & efficient frontier analysis** using downside risk.

---

### 🔗 License & Acknowledgements

This repository is part of the MScFE690 Capstone Project at WorldQuant University.

Data retrieved from Yahoo Finance.
Special thanks to WQU faculty, mentors, and peer reviewers.





