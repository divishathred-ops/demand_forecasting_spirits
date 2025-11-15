# Demand Forecasting for Premium Spirits

Time series forecasting for Pernod Ricard inventory optimization.

## Best Model: LightGBM

### Performance
- **MAE:** 97.8 units
- **RMSE:** 126.0 units
- **MAPE:** 6.8%
- **R²:** 0.3488

### Improvement Over Baseline
- **16.7% better** than 7-day moving average

## Files
- `model_lightgbm.pkl` - Best production model
- `test_predictions_spirits.csv` - All forecasts
- `model_comparison_spirits.csv` - Performance metrics
- `feature_importance_spirits.csv` - Feature rankings

## Technical Details
- **Data:** 2 years daily sales (730 days)
- **Features:** 13 engineered features
- **Models:** LightGBM, ARIMA, Baseline (Moving Average)
- **Train-test:** 80-20 split (temporal order preserved)

## Business Impact
- **16.7% accuracy improvement** vs baseline
- Potential annual savings from reduced waste
- Optimized inventory levels
- Prevented stockouts

## Key Features for Forecasting
1. sales_ma7 (Importance: 559.00)
2. sales_lag1 (Importance: 511.00)
3. sales_lag30 (Importance: 464.00)

## Model Comparison

| Model | MAE | RMSE | MAPE% | R² |
|-------|-----|------|-------|---|
| LightGBM | 97.8 | 126.0 | 6.8 | 0.3488 |
| ARIMA | 119.2 | 160.7 | 8.3 | -0.0599 |
| Baseline (MA7) | 117.4 | 159.0 | 8.2 | -0.0373 |

## Deployment
Ready to deploy in production. Model file can be loaded with:
```python
import pickle
model = pickle.load(open('model_lightgbm.pkl', 'rb'))
forecast = model.predict(new_features)
```
