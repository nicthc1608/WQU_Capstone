# 📊 MScFE690 Capstone Project  
## Estimating Value-at-Risk (VaR) and Expected Shortfall (ES) Using Traditional and EVT-Based Methods Across Multi-Asset Portfolios  
WorldQuant University | MSc in Financial Engineering  
**Team:** Nicholas Johnson & Bryan Mutua  
**Advisor:**  

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
This project evaluates **portfolio risk across diverse asset classes** using several Value-at-Risk (VaR) and Expected Shortfall (ES) methodologies. These include:  
- Parametric VaR  
- Historical Simulation  
- Monte Carlo Simulation  
- Extreme Value Theory (EVT)  

The primary goal is to **compare how different risk modeling techniques perform under various market regimes** and to explore how portfolio diversification impacts tail risk.

---

### 📌 Objectives  
- Implement multiple VaR and ES methodologies using real financial time series data.  
- Assess tail risk under calm and stressed conditions (e.g., 2020 COVID crash).  
- Evaluate risk profiles across different asset classes: SPDR ETFs, Bonds, Commodities, Forex, and Cryptocurrencies.  
- Understand the strengths and limitations of each method from both theoretical and practical standpoints.  
- Simulate diversified portfolios and compare their risk-return trade-offs.

---

### 📈 Methodology  
- Retrieve OHLCV data using `yfinance` for selected tickers from 2010–2024 (daily frequency).  
- Calculate log returns and clean for missing data.  
- Construct both individual and blended portfolios.  
- Compute VaR and ES at different confidence levels (95%, 99%).  
- Apply Generalised Pareto Distribution (GPD) for EVT-based VaR.  
- Visualise risk results, rolling windows, and efficient frontiers (in progress).

---

### 📊 Asset Classes Analysed  

| Category       | Assets |
|----------------|--------|
| **SPDR ETFs** | SPY, XLF, XLE, XLK, XLV, XLY, XLP, XLI, XLB, XLU, XLRE, XLC, SDY, XBI, XME |
| **Commodities** | GC=F, SI=F, CL=F, BZ=F, NG=F, HG=F, ZC=F, ZS=F, ZW=F |
| **Bonds (ETFs)** | TLT, IEF, SHY, BND, AGG, HYG, LQD, TIP, EMB, MUB |
| **Forex** | EURUSD=X, USDJPY=X, GBPUSD=X, AUDUSD=X, USDCAD=X, USDCHF=X, NZDUSD=X |
| **Cryptocurrencies** | BTC-USD, ETH-USD, BNB-USD, SOL-USD, XRP-USD, DOGE-USD |

---
### 💻 File Structure  

```bash
📁 WQU_Capstone/
│
├── 01_data_cleaning_and_returns.ipynb        # Data retrieval and return computation
├── 02_var_es_methods.ipynb                   # Parametric, Historical, Monte Carlo VaR & ES
├── 03_evt_model.ipynb                        # EVT tail fitting and GPD-based VaR/ES
├── 04_portfolio_simulation.ipynb             # Portfolio construction and optimisation (in progress)
├── requirements.txt                          # Python package dependencies
├── results/                                  # Figures and output CSVs
└── README.md                                 # Project overview and documentation

`````` 
 
### 📦 Requirements
To install the required libraries:

     pip install -r requirements.txt

### Main dependencies:-pandas, numpy, matplotlib, seaborn, plotly, scipy, statsmodels, finance, arch, scikit-learn

### 📎 Data Sources
-Yahoo Finance via yfinance (OHLCV data)
-FRED (planned, for macro indicators)
-Investopedia, SSRN, JFQA (supporting academic literature)

### 📌 Key Findings (Work In Progress)
-VaR estimates vary significantly across asset classes and techniques.
-EVT captures extreme losses more effectively during high-volatility regimes.
-Cryptocurrencies and commodities show heavier tails and higher ES values.
-Diversified portfolios show lower aggregated VaR due to reduced correlation effects.

### 📌 Detailed results and graphs will be posted in the /results directory.

### 🔗 License & Acknowledgements
This repository is part of the MScFE690 Capstone Project at WorldQuant University.

Data retrieved from Yahoo Finance, academic references from SSRN, JFQA, etc.

Special thanks to WQU faculty and mentors.

