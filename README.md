# Capstone-Project-Group-11192  
## Hierarchical Risk Parity with Autoencoder-based Covariance Estimation and Deep Neural Network Sector Rotation in the Johannesburg Stock Exchange

---

## Overview

This repository contains the complete implementation of the capstone project titled:

**Hierarchical Risk Parity with Autoencoder-based Covariance Estimation and Deep Neural Network Sector Rotation in the JSE (South Africa).**

The project integrates three main components:

- Autoencoder-based covariance estimation  
- Hierarchical Risk Parity (HRP) portfolio allocation  
- Deep Neural Network (DNN) sector rotation  

The objective is to enhance diversification and improve predictive sector rotation within an emerging market environment.

This work was completed as part of the **Master of Science in Financial Engineering** at **WorldQuant University**, under the supervision of **Prof. Ivan Blanco**.

---

## Authors

| Name | Email |
|------|--------|
| **Mphikeleli Mbongiseni Mathonsi** | mphikelelimm@gmail.com |
| **Humbelani Khuli** | humbelanikhuli240@gmail.com |

---

## Methodology Summary

### 1. Data Collection
- Historical adjusted-close prices of JSE-listed Satrix sector ETFs (2008–2025) retrieved using the `yfinance` API:  
  STX40, STXFIN, STXIND, STXRES, STXDIV  
- Macroeconomic data sourced from FRED, SARB, and Yahoo Finance:  
  CPI, GDP, Repo Rate, USD/ZAR, Gold Price, 10-year Government Bond Yield (ZAGB10y)

### 2. Preprocessing
- Forward-filled missing values  
- Winsorised outliers  
- Converted to quarterly log returns  
- Standardised macroeconomic features using `StandardScaler`  
- Aligned all datasets to a unified quarterly date index  

### 3. Covariance Estimation
Three covariance models were implemented:
1. Sample covariance  
2. Ledoit–Wolf shrinkage covariance  
3. Autoencoder-based covariance  
   - Autoencoder compresses return data into latent features  
   - Reconstructs denoised returns  
   - Produces more stable covariance estimates in small samples  

### 4. Portfolio Allocation – HRP
Hierarchical Risk Parity (HRP), based on López de Prado (2016), was applied to each covariance matrix:

- Computes correlation-based distance matrices  
- Performs hierarchical clustering  
- Allocates risk recursively across clusters  

HRP is robust to covariance estimation errors and performs well in markets with high inter-sector correlations.

### 5. Sector Rotation – Deep Neural Network (DNN)
- A feedforward multi-label neural network predicts next-quarter sector outperformance  
- Binary labels were created using the cross-sectional median rule  
- Sigmoid outputs produce probabilities for each sector  
- Predictions are used to tilt HRP weights toward expected outperformers  
- Strategy rebalances quarterly  

### 6. Backtesting and Evaluation
- Rolling 12-quarter training window  
- One-quarter-ahead predictions  
- Quarterly rebalancing  

Strategies evaluated:
- Equal-Weight  
- Markowitz  
- HRP (Sample, LW, AE)  
- HRP with DNN overlay  
- DNN-Only  
- Benchmarks:
  - Top40 buy-and-hold  
  - Oracle (perfect foresight of winner sector)  

Performance metrics:
- Sharpe Ratio  
- Sortino Ratio  
- Annualised Volatility  
- Maximum Drawdown  
- Turnover  
- Hit Ratio  

---
