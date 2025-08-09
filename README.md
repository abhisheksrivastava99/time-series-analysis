## Time Series Analysis of the Straits Times Index (STI)
### Project Overview 
This repository contains a Jupyter notebook (EDA-STI.ipynb) that performs an exploratory data analysis (EDA) and time series analysis on the Straits Times Index (^STI). The goal is to understand the characteristics of the STI's daily price movements over a five-year period and to lay the groundwork for building a forecasting model. The analysis follows a standard workflow for financial time series data, including data preparation, stationarity testing, and model parameter selection using ACF and PACF plots.

### Analysis Steps & Key Findings 
#### 1. Data Acquisition and Preparation
The analysis begins by downloading 5 years of daily historical data for the STI using the yfinance library. The data is then checked for any missing values to ensure a clean dataset for accurate analysis. The data was found to be complete with no missing values.

#### 2. Visualizing the Time Series
The raw STI close price and its daily returns (first difference) were plotted.

The raw price series shows a clear upward trend, indicating it is non-stationary.

The daily returns series fluctuates around a constant mean of zero, suggesting it is stationary.

#### 3. Stationarity Testing
To confirm the stationarity of the daily returns, the Augmented Dickey-Fuller (ADF) test was performed.

Result: The p-value was extremely small (1.89×10 
−22
 ), leading to the rejection of the null hypothesis of non-stationarity. This confirms that the daily returns series is stationary and suitable for time series modeling.

#### 4. Seasonal Decomposition
A seasonal decomposition was performed on the raw price data to separate the trend, seasonal, and residual components.

Trend: The plot clearly shows the long-term upward movement of the index.

Seasonal: A weekly seasonality (period=5) was checked, but the plot showed no significant or consistent seasonal pattern.

Residuals: The residuals appeared to increase during periods of high volatility, suggesting that a multiplicative model is a better fit for the data.

#### 5. ACF and PACF Analysis
The Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF) plots were generated for the stationary daily returns series. These plots are essential for identifying the parameters (p and q) for an ARIMA model.

ACF: A significant spike was observed at lag 1, with all other lags falling within the confidence interval. This suggests a potential Moving Average (MA) component of order 1.

PACF: A significant spike was also observed at lag 1, with all other lags being insignificant. This indicates a potential Autoregressive (AR) component of order 1.

### Conclusion: 
Based on the analysis of the ACF and PACF plots, a suitable starting point for a model to forecast the STI's daily returns would be an ARIMA(1, 0, 1) model.

### How to Use the Notebook
Clone this repository.

Install the required libraries: pandas, yfinance, matplotlib, and statsmodels.

Open the EDA-STI.ipynb notebook in Jupyter.

Run all the cells to reproduce the analysis.
