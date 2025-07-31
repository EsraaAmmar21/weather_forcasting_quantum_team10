# Cairo Weather Forecasting Project

## Project Title: Rainfall Classification and Temperature Forecasting in Cairo

## Team Members

| Name        | Role                                      |
|-------------|-------------------------------------------|
| Esraa Omar  | Developed Kaggle Notebook and ML Pipeline |
| Shahd Tamer | README Documentation and GitHub Setup     |

---

## Notebook Overview

This project uses historical weather data from Cairo to build two machine learning models:

1. **Rainfall Classification** – Predicts whether it will rain or not
2. **Temperature Regression** – Predicts the daily mean temperature

The project was implemented and explored in a Kaggle Notebook:  
[View it on Kaggle](https://www.kaggle.com/code/esraaammar/weather-forcasting)

---

## Data Summary

- **Source**: Cairo weather dataset from Kaggle
- **Rows**: 5845 daily records
- **Initial Features**: 35
- **Target Variables**:
  - `rain_flag` (binary classification)
  - `temperature_2m_mean` (regression)

---

##  Feature Engineering

- Parsed timestamps: month, day, season, dayofyear
- Added lag and rolling features:
  - `rain_prev_1d`, `avg_temp_past_7d`
- Wind direction encoded using sine/cosine
- Removed redundant or low-value features
- Created `rain_flag` binary target from rainfall column

---

##  Models Used

### Stage 1: Rainfall Classification
- **Model**: `XGBoostClassifier`
- **Technique**: SMOTE to balance classes
- **Metric**: Accuracy (~93%)

### Stage 2: Temperature Regression
- **Model**: `XGBoostRegressor`
- **Input**: Weather features + predicted `rain_flag`
- **Metrics**:
  - MAE ≈ 1.5°C
  - RMSE ≈ 2.3°C
  - R² ≈ 0.92

---

##  Files in This Repo

- `Cairo_Weather_Forecasting.ipynb`: Main notebook exported from Kaggle
- `README.md`: Project documentation
- `requirements.txt`: Python packages list 

---

## How to Use

1. Clone the repo or download the notebook
2. Open `Cairo_Weather_Forecasting.ipynb` in Jupyter or Google Colab
3. Run the notebook to view results and experiment

---

## Future Enhancements

- Try deep learning models (LSTM) for time-series prediction
- Add data from other cities
- Deploy the model via Streamlit or Flask
- Automate using Airflow or Prefect

---

## 🛠️ Requirements

```bash
pip install pandas numpy seaborn matplotlib scikit-learn xgboost imbalanced-learn
