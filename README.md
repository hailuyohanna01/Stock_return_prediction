# Stock Return Prediction Using Machine Learning

## Project Overview

Developed a Python-based machine-learning pipeline to investigate whether historical market information can predict next-day SPY ETF returns.

The project uses linear regression with momentum, volatility, and trend-based features, evaluates predictions on a chronologically separated 2025 test dataset, and compares model performance against simple forecasting baselines.

## Technologies

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib
- yfinance
- Google Colab

## Methodology

**Historical Data:** SPY adjusted daily closing prices from January 2020 through December 2025.

**Feature Engineering:**
- Previous one-day return
- Previous five-day return
- Five-day rolling volatility
- Price relative to the 20-day moving average

**Prediction Target:** Next-trading-day SPY percentage return.

**Machine Learning Model:** Ordinary least squares linear regression.

**Data Splitting:**
- Training: 2020–2024
- Testing: 2025
- Chronological separation to avoid training on future-period targets

**Evaluation Metrics:**
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R-squared
- Directional accuracy

## Results

| Metric | Linear Regression | Baseline |
|---|---:|---:|
| MAE | 0.7400% | 0.7486% |
| RMSE | 1.2161% | 1.2296% |
| R-squared | 0.0183 | N/A |
| Directional Accuracy | 56.22% | 57.43% |

MAE and RMSE use a zero-return prediction baseline. Directional accuracy uses an always-positive prediction baseline.

## Key Findings

- Linear regression achieved a lower MAE and RMSE than the zero-return baseline.
- Relative MAE improved by approximately 1.15%.
- Relative RMSE improved by approximately 1.10%.
- The out-of-sample R-squared was 0.0183, indicating limited predictive power.
- Directional accuracy reached 56.22%, below the 57.43% always-positive baseline.
- The results demonstrate that modest improvements in return prediction error do not necessarily translate into better directional forecasts.

## Model Validation

Six implementation checks passed:

1. Chronological training/testing separation
2. No missing model features
3. Finite prediction values
4. Prediction length consistency
5. Feature/target index alignment
6. Training target boundary separation

## Limitations

- Daily stock returns are inherently difficult to predict.
- Linear regression assumes a linear relationship between features and target returns.
- The model was evaluated on one historical test period.
- No transaction costs, slippage, or trading strategy profitability were evaluated.
- Predictive improvements may not persist across different market conditions.
- Additional walk-forward testing would be necessary to assess robustness.

## Future Improvements

- Compare against regularized regression models such as Ridge and Lasso.
- Evaluate alternative market indicators and features.
- Implement walk-forward validation.
- Test performance across different market regimes.
- Assess whether predictions provide economically meaningful trading signals.

## Conclusion

This project demonstrates an end-to-end financial machine-learning workflow, including market-data preparation, feature engineering, chronological train/test separation, model training, performance benchmarking, and validation.

Linear regression modestly improved return-prediction errors compared with a zero-return baseline, but did not outperform an always-positive directional benchmark.

The findings highlight both the potential and limitations of machine learning in financial return prediction.
