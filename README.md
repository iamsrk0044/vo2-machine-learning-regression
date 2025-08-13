# VO₂ Oxygen Uptake Regression

This project investigates the prediction of oxygen uptake (VO₂, L/min) from wearable sensor data using various regression models. The goal is to estimate VO₂ during running based on physiological and performance metrics, enabling **non-invasive, real-time monitoring**.

## Data Collection
The dataset was recorded from **12 participants** .  
Data was collected at millisecond intervals and includes:
- Heart rate (HR)
- Running speed
- Acceleration
- Power output (Pmet)
- Simulated oxygen uptake (L/min)
- Measured oxygen uptake (L/min, gold standard)

VO₂ measurements were obtained using a **metabolic measurement system** (gold standard for oxygen uptake analysis).

## Analysis Approach
We applied **time-series regression** using models both:
1. **With and without feature engineering** (lags, rolling means, differences, etc.)
2. **With and without simulated VO₂** as an additional predictor

Training was performed with **Leave-One-Subject-Out Cross-Validation** to ensure generalization to unseen participants.

## Models Implemented
- Support Vector Regression (RBF kernel)
- Random Forest Regression
- Gated Recurrent Unit (GRU)
- Long Short-Term Memory (LSTM)

## Best Results
- **Random Forest** -> **R² = 0.84** | **RMSE = 0.39 l/min** | **MSE = 0.15 (l/min)²**  
- **GRU** (simulated VO₂ + FE) -> **R² = 0.83** | **RMSE = 0.41 l/min** | **MSE = 0.17 (l/min)²**  
- **LSTM** (simulated VO₂, no FE) -> **R² = 0.82** | **RMSE = 0.42 l/min** | **MSE = 0.18 (l/min)²**  
- **SVR** (30% reduced dataset) -> **R² = 0.78** | **RMSE = 0.46 l/min** | **MSE = 0.21 (l/min)²**  
