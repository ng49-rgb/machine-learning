# 🗽 NYC Taxi Trip Duration Prediction 🚕

A machine learning capstone project focused on predicting taxi trip durations in New York City using historical trip data, regression models, and hyperparameter tuning.

---

## 📌 Problem Statement

The objective is to predict the **trip duration** of NYC taxi rides using a combination of temporal, spatial, and vendor-related features. Accurate predictions help:
- Improve ETA predictions for users
- Optimize dispatch systems
- Reduce wait time, operational cost, and customer dissatisfaction

---

## 📊 Dataset

Data Source: [Kaggle - NYC Taxi Trip Duration](https://www.kaggle.com/competitions/nyc-taxi-trip-duration)

- Rows: ~55 million
- Features:
  - Pickup/Dropoff timestamps and locations
  - Passenger count
  - Distance (Haversine)
  - Vendor ID
  - Day of the week, hour, month
  - Store-and-forward flag

---

## 🔧 Feature Engineering

- ✅ Extracted `pickup_hour`, `pickup_month`, `pickup_day` from datetime  
- ✅ Calculated `distance_km` using the Haversine formula  
- ✅ Applied **encoding** to categorical features  
- ✅ Created binary features (e.g. `store_and_fwd_flag_Y`)  
- ✅ Transformed `trip_duration` using log for some models

---

## 🤖 Models Trained

| Model             | Regularization | Notes                              |
|------------------|----------------|-------------------------------------|
| Linear Regression| ❌             | Baseline                           |
| Ridge Regression | ✅ L2          | With cross-validation              |
| Lasso Regression | ✅ L1          | With `GridSearchCV`                |
| Random Forest    | ❌             | Ensemble trees                     |
| XGBoost          | ✅             | Tuned with **Optuna**, best model  |
| KNN Regressor    | ❌             | For neighborhood comparison        |

---

## 🧪 Evaluation Metrics

Metrics selected for business impact and interpretability:
- **MAE**: Lower values reduce ETA errors
- **RMSE**: Penalizes large errors (good for long trips)
- **R² Score**: Measures variance explained
- **Adjusted R²**: Controls for feature count
- **MAPE**: Scaled % error (business friendly)
- **Bias**: Mean % error, shows under/overestimation

---

## 🔍 Hyperparameter Optimization

- `Lasso` & `Ridge`: `GridSearchCV`
- `XGBoost`: Tuned using **Optuna**

**Best XGBoost Parameters:**
- `n_estimators`: 222
- `max_depth`: 6
- `learning_rate`: 0.146
- `subsample`: 0.962
- `colsample_bytree`: 0.937

---

## 📈 Final Results

| Model        | MAE  | RMSE | R²    |
|--------------|------|------|-------|
| Ridge        | 4.21 | 5.89 | 0.58  |
| RandomForest | 3.91 | 5.23 | 0.65  |
| **XGBoost**  | 3.35 | 4.63 | 0.72  |

---

### ✅ Final XGBoost Model Performance:

Training R² : 0.8173
Test R² : 0.8035
MAE (Test) : 0.2272
RMSE (Test) : 0.3226
Adjusted R² (Test) : 0.8035
Mean Absolute % Error : 3.73%
Mean % Error (Bias) : -0.34%

---


---

## 📊 Visualizations

- ✅ Actual vs Predicted Line Plot  
- ✅ Feature Importance using SHAP  
- ✅ Trip Duration Histogram  
- ✅ Distance vs Duration correlation  
- ✅ Model Score Comparison Chart  

---
