# US Inflation Forecasting: Econometric Models (ARIMA) vs. Machine Learning (XGBoost)

An empirical comparison of classical time-series econometrics and gradient boosting models in forecasting US Year-over-Year CPI inflation using Federal Reserve Economic Data (FRED).

## Methodology & Experiments
1. **Static vs. Rolling ARIMA:** Demonstrated mean-reversion limitations in static 24-month forecasts (RMSE: `0.69`) and improved accuracy via 1-step-ahead rolling window estimation (`ARIMA(0,1,3)`, RMSE: `0.302`).
2. **Baseline vs. Feature-Engineered XGBoost:** Reduced RMSE from `0.412` to `0.308` by introducing lag structures, rolling means, momentum features, and regularization (`max_depth=3`, `learning_rate=0.05`).
3. **Multivariate Macro XGBoost:** Incorporated lagged Unemployment (`UNRATE`) and Federal Funds Rate (`FEDFUNDS`) without data leakage, achieving `0.303` RMSE and capturing directional turning points better than univariate ARIMA.

## Key Economic Findings
* **Inflation Persistence:** `lag_1` dominates short-term inflation dynamics.
* **Monetary Policy Lag:** 3-month lagged interest rates (`fed_lag3`) carry significantly higher predictive gain than 1-month lagged rates (`fed_lag1`), aligning with monetary transmission theory.
