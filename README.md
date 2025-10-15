# Capstone-Project-Group-11192
Hierarchical Risk Parity with Autoencoder-based Covariance Estimation and Deep Neural Network Sector Rotation in the Johannesburg Stock Exchange

Hierarchical Risk Parity with Autoencoder-based Covariance Estimation and Deep Neural Network Sector Rotation (JSE)

 ## Overview

This repository contains the source code, data workflow, and report for the capstone project titled:

Hierarchical Risk Parity with Autoencoder-based Covariance Estimation and Deep Neural Network Sector Rotation in the Johannesburg Stock Exchange

The project integrates Autoencoder-based covariance estimation, Hierarchical Risk Parity (HRP) allocation, and Deep Neural Network (DNN)-driven sector rotation to improve portfolio diversification and adaptive performance in emerging markets such as South Africa’s Johannesburg Stock Exchange (JSE).

Developed as part of the Master of Science in Financial Engineering at WorldQuant University under the supervision of Prof. Ivan Blanco.

## Authors

Mphikeleli Mbongiseni Mathonsi
mphikelelimm@gmail.com

Humbelani Khuli
humbelanikhuli240@gmail.com


## Methodology Summary
1. Data Collection

Historical adjusted closing prices of JSE-listed Satrix ETFs (2008–2025) retrieved using the yfinance API.

Macroeconomic indicators (CPI, GDP, interest rate, gold, USD/ZAR) from FRED and SARB.

2. Preprocessing

Missing values handled by forward-fill and winsorization for outlier removal.

Data aligned to monthly frequency and standardized using StandardScaler.

3. Covariance Estimation

Implemented three estimators:

Sample Covariance

Ledoit–Wolf Shrinkage

Autoencoder-based Covariance

Autoencoder denoises returns and extracts latent structures to improve risk representation.

4. Portfolio Allocation – HRP

Hierarchical Risk Parity (Lopez de Prado, 2016) allocates weights based on clustering of correlations rather than matrix inversion.

Reduces estimation errors and concentration risk.

5. Sector Rotation – DNN

Feedforward Deep Neural Network trained on macroeconomic indicators to predict sector outperformance.

Rotation overlay applied to HRP weights dynamically.

6. Backtesting and Evaluation

Rolling-window backtesting (12 quarters) with quarterly rebalancing.

Evaluation metrics:
Sharpe Ratio, Sortino Ratio, Volatility, Max Drawdown, Turnover, and Hit Ratio.
