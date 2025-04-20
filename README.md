

# MSFT_Stock_Price_Prediction

This repository contains a Jupyter Notebook (`Stock_Price_Prediction.ipynb`) for analyzing and predicting stock prices for Microsoft (MSFT), with a focus on financial forecasting and risk assessment. The project uses an LSTM model with feature engineering and regularization to predict stock prices, followed by a Monte Carlo simulation using Geometric Brownian Motion (GBM) to forecast future prices and quantify uncertainty. The notebook retrieves historical stock data using the `yfinance` library, saves it for analysis, and includes visualizations of the Train, Validation, and Test data splits, model predictions, and Monte Carlo simulation results.

## Table of Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Output](#output)
- [Data Visualization](#data-visualization)
- [Model Predictions vs. Observations](#model-predictions-vs-observations)
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Final Model Performance](#final-model-performance)
- [Future Work](#future-work)
- [License](#license)

## Overview
The notebook downloads historical stock data for Microsoft (MSFT) from Yahoo Finance, covering the period from March 13, 1986, to April 17, 2025. It saves the data to a CSV file (`MSFT_stock_data_max.csv`) for analysis. The project features an LSTM model with financial indicators like moving averages, RSI, volatility, and S&P 500 Index data to predict stock prices. A Monte Carlo simulation with GBM forecasts future prices over a 30-day horizon, providing probabilistic outcomes and risk metrics like Value at Risk (VaR). This project is tailored for quant and finance analyst roles, emphasizing predictive modeling, uncertainty quantification, and risk assessment.

## Prerequisites
- Python 3.9 or higher
- Jupyter Notebook or JupyterLab
- Required Python libraries:
  - `numpy`
  - `pandas`
  - `yfinance`
  - `matplotlib`
  - `scikit-learn`
  - `tensorflow`

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/stock-price-prediction.git
   cd stock-price-prediction
   ```
2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install the required libraries:
   ```bash
   pip install numpy pandas yfinance matplotlib scikit-learn tensorflow
   ```
4. Install Jupyter Notebook:
   ```bash
   pip install jupyter
   ```

## Usage
1. Start Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
2. Open `Stock_Price_Prediction.ipynb` in the Jupyter interface.
3. Run the cells sequentially to:
   - Import necessary libraries.
   - Download MSFT stock data.
   - Save the data to a CSV file.
   - Train the LSTM model and generate predictions.
   - Run the Monte Carlo simulation and visualize the results.

The output includes a preview of the stock data, a saved CSV file, visualizations of the data splits, model predictions, and Monte Carlo simulation results with financial metrics.

## Output
- **Console Output**: The first five rows of the MSFT stock data, showing `Close`, `High`, `Low`, `Open`, and `Volume` from March 13, 1986, onwards.
- **CSV File**: `MSFT_stock_data_max.csv` containing the full historical dataset.
- **DataFrame**: A Pandas DataFrame with 9,854 rows, which may require cleaning due to header formatting issues.
- **Metrics**: Training, Validation, and Testing MSE and MAE, along with Monte Carlo simulation results (mean, median, 90% confidence interval, expected return, and VaR).

## Data Visualization
The following graph visualizes the MSFT stock price data, split into Train, Validation, and Test sets, from 1985 to 2025:

![Train, Validation, and Test Split](train_validation_test_split.png)

### Analysis
- **Train Set (Blue)**: Covers 1985 to approximately 2015, with prices showing a gradual increase.
- **Validation Set (Orange)**: Spans 2015 to 2019, capturing a period of steady growth.
- **Test Set (Green)**: Covers 2019 to 2025, showing a sharp upward trend followed by volatility.
- **Trends**: The stock price remains relatively flat until 2010, then grows steadily, with a significant increase after 2019.

## Model Predictions vs. Observations
The following graph compares the LSTM model's predictions against actual observations for the Training, Validation, and Testing datasets:

![Model Predictions vs Observations](model_predictions_vs_observations_updated.png)

### Analysis
- **Training (Blue Predictions, Orange Observations)**: 1985 to 2015. Predictions closely follow the observations, with an MSE of 6.31 and MAE of 1.64.
- **Validation (Green Predictions, Red Observations)**: 2015 to 2019. Predictions diverge significantly, underestimating the stock price, with an MSE of 1667.03 and MAE of 33.00.
- **Testing (Purple Predictions, Pink Observations)**: 2019 to 2025. Predictions fail to capture the sharp upward trend, remaining flat around 50-100 while the actual price exceeds 400, resulting in an MSE of 68807.82 and MAE of 246.05.

## Monte Carlo Simulation
The project includes a Monte Carlo simulation to forecast future stock prices over a 30-day horizon, starting from the last actual price in the test set ($367.78). The simulation uses Geometric Brownian Motion (GBM) to model price dynamics, running 1,000 iterations to generate a range of possible outcomes. Financial metrics such as expected return and Value at Risk (VaR) are calculated to support risk assessment.

![Monte Carlo Simulation](monte_carlo_simulation_updated.png)

### Analysis
- **Test Observations**: The last 100 days (late November 2024 to early March 2025) show a downward trend, with the price dropping from $450 to $367.78.
- **Simulated Paths**: The 1,000 simulated paths fan out from the starting price of $367.78, covering early March to early April 2025.
- **Mean Forecast**: The mean forecast path trends upward to $379.67, indicating an expected return of 3.23%.
- **90% Confidence Interval**: The interval spans $311.05 to $454.61 by the end of the 30 days, reflecting uncertainty in price movements.

![Distribution of Final Prices](distribution_of_final_prices.png)

### Distribution Analysis
- The histogram shows the distribution of final prices after 30 days, with a peak around $380, close to the mean ($379.67).
- The distribution is slightly right-skewed, typical for stock prices modeled with GBM.
- The 90% confidence interval ($311.05 - $454.61) provides a range of likely outcomes, with a VaR of $56.73 at the 95% confidence level.

### Financial Metrics
- **Mean Forecasted Price**: $379.67
- **Median Forecasted Price**: $377.43
- **90% Confidence Interval**: $311.05 - $454.61
- **Expected Return over 30 Days**: 3.23%
- **Value at Risk (VaR) at 95% Confidence Level**: $56.73

These metrics provide actionable insights for quant and finance analysts, supporting risk assessment and portfolio management.

## Final Model Performance
The final model performance is evaluated using the following metrics:
- **Mean Squared Error (MSE)**:
  - Training MSE: 6.31
  - Validation MSE: 1667.03
  - Testing MSE: 68807.82
- **Mean Absolute Error (MAE)**:
  - Training MAE: 1.64
  - Validation MAE: 33.00
  - Testing MAE: 246.05

### Analysis
- **Training**: Good performance (MSE: 6.31, MAE: 1.64), with reduced overfitting.
- **Validation**: Poor performance (MSE: 1667.03, MAE: 33.00), indicating failure to generalize.
- **Testing**: Extremely poor performance (MSE: 68807.82, MAE: 246.05) due to the model's inability to capture the sharp upward trend.
- **Monte Carlo Simulation**: Provides a realistic probabilistic forecast starting from the last actual price, offering valuable insights for financial analysis despite the LSTM model's limitations.

## Future Work
- Improve the LSTM model with early stopping, additional features (e.g., macroeconomic indicators), and a hybrid approach (e.g., LSTM + ARIMA) to better capture trends.
- Enhance the Monte Carlo simulation with adjusted GBM parameters, longer forecast horizons, and additional risk metrics like CVaR.
- Add visualizations for cumulative returns or drawdowns to provide deeper financial insights.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

### Notes
- **Direct Pasting**: This README is ready to be copied and pasted directly into your GitHub repository's README text editor.
- **Image Links**: Ensure the referenced images (`train_validation_test_split.png`, `model_predictions_vs_observations_updated.png`, `monte_carlo_simulation_updated.png`, `distribution_of_final_prices.png`) are saved in your repository with the correct file names for the links to work.
- **Title**: The title `# MSFT_Stock_Price_Prediction` is now included at the top, matching your request.
