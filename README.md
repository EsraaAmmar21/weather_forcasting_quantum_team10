# Weather Forecasting Project

## Project Title: Rainfall Classification and Temperature Forecasting in Cairo

## Team Members

| Name        | Role                                       |
|-------------|--------------------------------------------|
| Esraa Omar  | Weather Forecasting Notebook               |
| Shahd Tamer | README Documentation and GitHub Submission |

---

## Project Overview

This project aims to build a robust weather prediction system using historical weather data from Cairo. It involves:

- Rainfall classification (rain/no rain)  
- Temperature prediction using classical machine learning models

### Key Highlights:

- Time-series feature engineering  
- Handling imbalanced data with SMOTE  
- Two-stage modeling:  
  - Stage 1: Rain prediction (classification)  
  - Stage 2: Temperature estimation (regression)  
- Evaluation using accuracy, MAE, RMSE, and R²  

---

## Folder Structure

```
weather-forecasting/
├── data/
│   ├── raw/               # Original CSV data
│   └── processed/         # Train/test datasets
├── notebooks/
│   ├── eda.ipynb          # Exploratory Data Analysis and Feature Engineering
│   ├── classification.ipynb # Rain prediction using XGBoostClassifier
│   └── regression.ipynb   # Temperature prediction using XGBoostRegressor
├── models/
│   ├── xgb_rain.pkl
│   └── xgb_temp.pkl
├── outputs/
│   ├── plots/
│   └── metrics/
├── requirements.txt
└── README.md
```

---

## Data Preprocessing

- Parsed timestamps (datetime64[ns])  
- Engineered features:
  - Temporal: month, day, season, dayofyear  
  - Lag: rain_prev_1d  
  - Rolling: avg_temp_past_7d  
  - Directional encoding: wind_dir_sin, wind_dir_cos  
- Removed redundant or highly correlated columns  
- Cleaned missing and zero-variance features  
- Targets:
  - `rain_flag` (classification)  
  - `temperature_2m_mean` (°C) (regression)  

---

## Classical Model Development

### Rainfall Classification

- **Model**: XGBoostClassifier  
- **Features**: Wind speed, radiation, humidity, cloud cover, etc.  
- **Imbalance Handling**: SMOTE  
- **Evaluation**: Classification report, accuracy, feature importance  

### Temperature Regression

- **Model**: XGBoostRegressor  
- **Features**: Includes predicted `rain_flag` from classification stage  
- **Evaluation**: MAE, RMSE, R²  
- **Visualization**: Actual vs Predicted temperature plot  

---

## Results Summary

| Task                    | Model              | Accuracy / MAE | RMSE / R²           |
|-------------------------|--------------------|----------------|---------------------|
| Rainfall Classification | XGBoostClassifier  | Accuracy: ~93% | -                   |
| Temperature Prediction  | XGBoostRegressor   | MAE: ~1.5°C    | RMSE: ~2.3°C / R²: ~0.92 |

---

## Required Libraries

- pandas  
- numpy  
- seaborn  
- matplotlib  
- scikit-learn  
- xgboost  
- imbalanced-learn  

To install all dependencies:

```bash
pip install -r requirements.txt
```

---

## How to Run

- Run `notebooks/eda.ipynb` for data preprocessing  
- Run `notebooks/classification.ipynb` to train the rainfall classifier  
- Run `notebooks/regression.ipynb` to train the temperature regressor  
- Visualizations and outputs will be stored in the `outputs/` folder  

---

## Future Work

- Explore deep learning models (e.g., LSTM) for temporal forecasting  
- Expand with external features (e.g., pressure, pollution)  
- Evaluate with data from multiple cities  
- Automate the pipeline using workflow tools  
