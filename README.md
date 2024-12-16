# Modeling Non-Stationarity and Finding an Equilibrium

## Overview
For a fully analysis, please [read here](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/Modeling%20non-stationarity%20and%20finding%20an%20equilibrium_report.pdf)

This project explores the concepts of non-stationarity and equilibrium in time series data, focusing on methods to test and model such data. Using Apple stock price data from 2013 to 2023 as an example, the report demonstrates key tests and visualization techniques to identify non-stationarity and suggests modeling approaches.

---

## Key Concepts

### 1. **Non-Stationarity**
Non-stationary time series data exhibit changing statistical properties (e.g., mean, variance) over time. Identifying and addressing non-stationarity is critical for accurate modeling and forecasting.

### 2. **Equilibrium**
Equilibrium refers to the long-term stable relationship in time series data. Techniques like co-integration help identify equilibrium, enabling better decision-making and model selection.

---

## Tests for Non-Stationarity

### 1. **Augmented Dickey-Fuller (ADF) Test**
The ADF test checks for the presence of a unit root in a time series. A high p-value indicates non-stationarity. The ADF equation is defined as:

$$ \[
\Delta Y_t = \alpha + \beta t + \gamma Y_{t-1} + \sum_{i=1}^{p} \delta_i \Delta Y_{t-i} + \varepsilon_t
\] $$

Where:
- $$\( \Delta Y_t \)$$: Change in the series at time $$\( t \)$$.
- $$\( \alpha \)$$: Constant term.
- $$\( \beta t \)$$: Coefficient for a time trend.
- $$\( \gamma \)$$: Coefficient for the lagged level of the series.
- $$\( \delta_i \)$$: Coefficients for the lagged changes of the series.
- $$\( \varepsilon_t \)$$: Error term at time $$\( t \)$$.
- $$\( p \)$$: Number of lagged changes included.

- **Result**:
  - ADF Statistic: `0.4887`
  - p-value: `0.9845`
  - **Conclusion**: Fail to reject the null hypothesis; the series is non-stationary.

### 2. **Kwiatkowski-Phillips-Schmidt-Shin (KPSS) Test**
The KPSS test checks for stationarity around a deterministic trend. The KPSS equation is given by:

$$ \[
Y_t = \rho Y_{t-1} + \varepsilon_t, \text{ where } \varepsilon_t = \mu + \tau t + \sum_{i=1}^{t} u_i
\] $$

Where:
- $$\( Y_t \)$$: Time series at time $$\( t \)$$.
- $$\( \rho \)$$: Coefficient indicating the autoregressive nature.
- $$\( \mu \)$$: Constant term.
- $$\( \tau \)$$: Coefficient for a deterministic trend.
- $$\( u_i \)$$: Stationary random error terms.

- **Result**:
  - KPSS Statistic: `7.406`
  - p-value: `0.01`
  - **Conclusion**: Reject the null hypothesis; the series is non-stationary.

---

## Data Analysis and Visualization

### 1. **Time Series Plot**
The plot indicates an upward trend in Apple stock prices, confirming non-stationarity.

![Time Series Plot](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/Time%20Series%20Plot.png)

### 2. **Rolling Statistics Plot**
The rolling mean shows an increasing trend, reinforcing non-stationarity.

![Rolling Statistics Plot](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/Rolling%20Statistics%20Plot.png)

### 3. **Decomposition Plot**
- **Trend**: Clear upward trajectory.
- **Seasonality**: No significant pattern detected.
- **Residual**: High volatility remains.

![Decomposition](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/Decomposition.png)

### 4. **ACF and PACF Plots**
- **ACF**: Gradual decline indicates strong autocorrelation and non-stationarity.

![ACF](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/ACF.png)

- **PACF**: Significant spike at lag 1 suggests an AR(1) process.

![PACF](https://github.com/milieureka/Modeling-non-stationarity-and-finding-an-equilibrium/blob/main/PACF.png)

---

## Recommended Modeling Approach

1. **Model Selection**: Use an ARIMA model. Based on ACF and PACF:
   - Suggested Model: ARIMA(1,1,0)
     - AR(1): One autoregressive term.
     - I(1): First-order differencing.
     - MA(0): No moving average terms.

2. **Model Validation**:
   - Ensure residuals are white noise to confirm a good fit.

---

## Next Steps
- Fit the ARIMA model to the data.
- Perform residual diagnostics to validate the model.
- Address any outliers or leverage points.

---

## References
1. Enders, W. (2014). "Applied Econometric Time Series." Wiley.

---
