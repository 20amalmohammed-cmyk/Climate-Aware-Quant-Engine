# Climate-Aware Quantitative Trading & Risk Engine

> A quantitative trading engine that integrates **real NOAA climate data** with **financial risk modeling** to quantify the impact of extreme weather events on portfolio performance.

---

##  Overview

Climate change poses a **material risk** to financial markets, yet most quantitative models ignore environmental factors. This project bridges that gap by:

-  Extracting latent **"Climate Shock"** features from raw NOAA precipitation data
-  Modeling the **sensitivity of stock returns** to extreme weather events
- Performing **portfolio stress-testing** against worst-case climate scenarios
- Providing **actionable risk management recommendations**

---

##  Key Features

| Feature | Description |
|---------|-------------|
| **Climate Data Ingestion** | Downloads & processes NOAA CPC daily precipitation (NetCDF format) |
| **Multi-Year Aggregation** | Combines 2011–2014 datasets using `xarray.open_mfdataset` |
| **Feature Engineering** | Standardization (Z-score), temporal lags, binary climate shock flags |
| **Regression Modeling** | OLS regression via `statsmodels` to estimate climate sensitivity (β) |
| **Portfolio Stress Testing** | Simulates $1M portfolio losses under consecutive climate shocks |
| **Risk Recommendations** | Suggests hedging strategies (derivatives, diversification, exposure cuts) |

---

##  Tech Stack

- **Python 3.11**
- **Data Analysis:** `pandas`, `numpy`, `xarray`, `netCDF4`
- **Statistical Modeling:** `statsmodels` (OLS Regression)
- **Visualization:** `matplotlib`
- **Environment:** Jupyter Notebook

---

### 2. Feature Engineering
| Feature | Formula / Logic |
|---------|-----------------|
| `precip_standardized` | (x − μ) / σ |
| `precip_lag1` | Standardized precipitation shifted by 1 month |
| `climate_shock` | 1 if standardized precip > 1.5 σ, else 0 |

### 3. Statistical Model
Ordinary Least Squares (OLS) regression
