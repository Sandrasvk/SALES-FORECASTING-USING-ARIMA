#  Champagne Sales Forecasting: SARIMA Pipeline

This project demonstrates a rigorous approach to Time Series Forecasting using **SARIMA** (Seasonal AutoRegressive Integrated Moving Average). By analyzing historical beverage sales data, the model identifies complex seasonal patterns to predict future demand.

##  Key Features
- **Statistical Testing:** Applied the **Augmented Dickey-Fuller (ADF)** test to verify non-stationarity.
- **Automated Optimization:** Leveraged `pmdarima` (`auto_arima`) to find the mathematically optimal parameters without manual trial and error.
- **Multiple Error Metrics:** Validated model performance using **MAE, MSE, MAPE, RMSE** for a 360-degree view of accuracy.
- **Diagnostic Evaluation:** Performed residual analysis to ensure the model captured all signal and left only "white noise."

## 📊 Methodology

### 1. Data Preparation
The dataset was transformed into a time-series format by setting a datetime index. Visual inspection revealed a clear 12-month seasonal cycle with significant spikes every December.

### 2. Stationarity & Model Selection
The ADF test yielded a p-value > 0.05, confirming the data was non-stationary.
- **Best Model:** `ARIMA(0,0,1)(1,1,0)[12]`
- The model automatically applied **Seasonal Differencing (D=1)** to stabilize the variance across years.

### 3. Model Diagnostics
Using plot_diagnostics(), I confirmed the model's validity:
- **Histogram Plus KDE:** Residuals are normally distributed.
- **Correlogram (ACF):** No significant correlations remain in the residuals, indicating the model has extracted all available information.

## 📈 Performance Results
The model demonstrated strong predictive power on the test set:

| Metric | Purpose | Value |
| **MAE** | Average absolute error |301.42314840519936|
| **MSE** | Penalizes large outliers |113951.2435054755|
| **RMSE** | Error in original units |337.5666504639869 |
| **MAPE** | Percentage-based accuracy |6.96595064742676|

## Future Forecast
The final model was trained on the full dataset to forecast the next 12 months. The forecast correctly identifies the upcoming end-of-year peaks, providing actionable insights for inventory planning.

## Run and libraries
1. pip install pmdarima
2. Run Champagne_Sales_Forecasting.ipynb in Jupyter.
3. Libraries - Numpy,Pandas,matplotlib,scikit- learn,statsmodels,pmdarima
4. Language - Python
