# 📊 MScFE690 Capstone Project  
## Estimating Value-at-Risk (VaR) and Expected Shortfall (ES) Across Multi-Asset Portfolios  
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
- [🧠 Future Enhancements](#-future-enhancements)  
- [🔗 License & Acknowledgements](#-license--acknowledgements)  

---

### 🔍 Project Overview  
This project evaluates **portfolio risk across multiple asset classes** using several Value-at-Risk (VaR) and Expected Shortfall (ES) methodologies.  
The study compares:  
- Parametric (Variance–Covariance)  
- Historical Simulation  
- Monte Carlo Simulation (parametric & bootstrap)  
- Extreme Value Theory (EVT) using Generalized Pareto Distribution  

We test how models perform under **normal vs. stressed market regimes** and whether portfolio diversification reduces **tail risk exposure**.  

---

### 📌 Objectives  
- Implement multiple VaR and ES methodologies using real financial time series (2010–2024).  
- Assess risk under calm vs. stressed regimes (VIX > 30).  
- Compare equities, commodities, bonds, forex, and crypto behavior.  
- Evaluate the consistency and biases of traditional vs. EVT-based risk estimates.  
- Explore portfolio optimization and ranking by VaR, ES, and Sortino ratio.  

---

### 📈 Methodology  
1. **Data Collection** – Yahoo Finance (`yfinance`) OHLCV data for 25+ assets.  
2. **Exploratory Analysis** – Returns, volatility, correlations, tail distributions.  
3. **Risk Modelling** – Parametric, Historical, Monte Carlo, EVT-based VaR/ES.  
4. **Backtesting** – Kupiec test, Christoffersen independence test, Lopez Loss.  
5. **Portfolio Construction** – 1,000 random multi-asset portfolios optimized by Sharpe, Sortino, and Jensen’s Alpha.  
6. **Ranking & Stress Testing** – Top 10% portfolios re-evaluated under stress and volatility regimes.  
7. **Regime Segmentation** – Normal vs. high-volatility regimes (VIX proxy).  

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

