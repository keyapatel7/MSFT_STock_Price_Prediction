
# MSFT Stock Price Prediction with Monte Carlo Simulation and LSTM

This repository contains a Jupyter Notebook (`Stock_Price_Prediction.ipynb`) for analyzing and predicting stock prices for Microsoft (MSFT), focusing on financial forecasting and risk assessment.  
The project uses an **LSTM model** with feature engineering and regularization to predict stock prices, followed by a **Monte Carlo simulation** using Geometric Brownian Motion (GBM) to forecast future prices and quantify uncertainty.

The notebook retrieves historical stock data using the `yfinance` library, saves it for analysis, and includes visualizations of the Train, Validation, and Test splits, model predictions, and Monte Carlo simulation results.

---

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Data Visualization](#data-visualization)
- [Model Predictions vs Observations](#model-predictions-vs-observations)
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Final Model Performance](#final-model-performance)
- [Future Work](#future-work)
- [License](#license)

---

## Overview

The notebook downloads historical stock data for **Microsoft (MSFT)** from Yahoo Finance, covering the period from **March 13, 1986, to April 17, 2025**.  
It saves the data to a CSV file (`MSFT_stock_data_max.csv`) for analysis.

Key features:
- **LSTM model** trained with financial indicators (moving averages, RSI, volatility, S&P 500 Index).
- **Monte Carlo simulation** using GBM to forecast future stock prices over a **30-day horizon**.
- **Risk metrics** including Expected Return and Value at Risk (VaR).

This project is tailored for **Quantitative Analyst** and **Finance Analyst** roles, emphasizing predictive modeling, uncertainty quantification, and risk assessment.

---

## Prerequisites

- Python 3.9 or higher
- Jupyter Notebook or JupyterLab
- Required Python libraries:
  - numpy
  - pandas
  - yfinance
  - matplotlib
  - scikit-learn
  - tensorflow

---

## Installation

Clone the repository:
```bash
git clone https://github.com/your-username/stock-price-prediction.git
cd stock-price-prediction
---


## Usage
Start Jupyter Notebook
jupyter notebook
---

## Open Stock_Price_Prediction.ipynb in the Jupyter interface.
Run the cells sequentially to:
Import necessary libraries.
Download MSFT stock data.
Save the data to a CSV file.
Train the LSTM model and generate predictions.
Run the Monte Carlo simulation and visualize the results.



Output
Console Output

Displays the first five rows of MSFT stock data, including Close, High, Low, Open, and Volume from March 13, 1986.

CSV File

MSFT_stock_data_max.csv: Contains the full historical dataset.

DataFrame

9,854 rows (may require cleaning due to header formatting issues).

Metrics

Training, Validation, and Testing MSE and MAE.
Monte Carlo simulation results:
Mean, median, 90% confidence interval, expected return, and VaR.



Data Visualization
MSFT Stock Price Data

The graph visualizes the MSFT stock price data, split into Train, Validation, and Test sets:
Train Set (Blue): 1985 to ~2015, gradual increase.
Validation Set (Orange): 2015 to 2019, steady growth.
Test Set (Green): 2019 to 2025, sharp upward trend with volatility.


Trends:
Relatively flat until 2010, steady growth afterward.
Significant increase post-2019.



Model Predictions vs. Observations
Training (Blue Predictions, Orange Observations)

Period: 1985 to 2015
MSE: 6.31
MAE: 1.64
Performance: Good, with predictions closely following observations.

Validation (Green Predictions, Red Observations)

Period: 2015 to 2019
MSE: 1667.03
MAE: 33.00
Performance: Predictions underestimate stock price.

Testing (Purple Predictions, Pink Observations)

Period: 2019 to 2025
MSE: 68807.82
MAE: 246.05
Performance: Predictions fail to capture the sharp upward trend.

Monte Carlo Simulation

Purpose: Forecasts future stock prices over a 30-day horizon using Geometric Brownian Motion (GBM), starting from the last actual price ($367.78).
Test Observations:
Downward trend from $450 to $367.78 (late November 2024 to early March 2025).


Simulated Paths:
1,000 paths starting from $367.78.
Forecast period: early March to early April 2025.

Mean Forecast:
Trends upward to $379.67.
Expected return: 3.23%.


90% Confidence Interval:
$311.05 to $454.61.



Distribution Analysis

Histogram: Shows a right-skewed distribution peaking around $380.
VaR (Value at Risk) at 95% confidence: $56.73.

Financial Metrics

Mean Forecasted Price: $379.67
Median Forecasted Price: $377.43
90% Confidence Interval: $311.05 - $454.61
Expected Return over 30 Days: 3.23%
Value at Risk (VaR): $56.73

Final Model Performance
Mean Squared Error (MSE)

Training MSE: 6.31
Validation MSE: 1667.03
Testing MSE: 68807.82

Mean Absolute Error (MAE)

Training MAE: 1.64
Validation MAE: 33.00
Testing MAE: 246.05

Analysis

Training: Good fit, reduced overfitting.
Validation: Poor generalization.
Testing: Extremely poor performance on unseen data.
Monte Carlo Simulation: Despite LSTM limitations, provides realistic probabilistic forecasts.

