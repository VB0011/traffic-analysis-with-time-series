# traffic-analysis-with-time-series



# 🚦 NYC Traffic Volume Forecasting using Time Series & ML

This project forecasts NYC daily traffic volume using classical time series and machine learning models. It emphasizes interpretability, robustness, and real-world applicability, especially post-COVID. We explored multiple models to identify the most suitable approach for predicting historical and future traffic volumes.

---

## 📂 Dataset

* **Time Frame**: 2009-01-01 to 2024-04-28
* **Filtered**: Excluded 2020 entirely to avoid COVID-era anomalies
* **Resampled**: Daily frequency
* **Interpolated**: Missing dates were filled using time-based interpolation

---

## 🔍 Exploratory Data Analysis (EDA)

* Visualized original vs interpolated data
* Decomposed time series into **Trend**, **Seasonality**, and **Residuals**
* Conducted **ADF (Augmented Dickey-Fuller)** tests to ensure stationarity
* Applied **log transformation**, **second-order**, and **seasonal differencing**
* Generated **ACF & PACF plots** to determine ARIMA parameters

---

## 🧠 Models Trained

### 1. ARIMA (1,1,1)

* Simple and interpretable
* Best performing model

### 2. SARIMA (1,1,1)(1,1,1,365)

* Accounted for yearly seasonality
* Slight overfitting observed

### 3. XGBoost Regressor

* Trained on `lag_1` to `lag_7` features
* Hyperparameters tuned using GridSearchCV with TimeSeriesSplit

### 4. LSTM Neural Network

* Sequence-based deep learning
* Used past 10 days as input
* Tuned using Keras Tuner (RandomSearch)

---

## 📊 Evaluation (2012 Prediction Performance)

| Model   | RMSE       |
| ------- | ---------- |
| ARIMA   | **124.42** |
| SARIMA  | 124.55     |
| XGBoost | 129.98     |
| LSTM    | 136.79     |

### 🏆 Best Model: **ARIMA**

* ARIMA performed best due to:

  * Stationary nature of the data
  * Simplicity and lower overfitting risk

---

## 📊 Visuals

* Plots for: Original vs Interpolated Data, Seasonal Decomposition, ACF & PACF
* Year 2012 predictions: ARIMA, SARIMA, LSTM, and XGBoost vs Actual
* RMSE Comparison Bar Chart

---

## 🚀 Forecasting Readiness

* Final model-ready dataset stored as `model_training.csv`
* Future 30-day prediction pipeline easily extendable

---

## 🛠️ Tech Stack

* **Python**, **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**
* **Statsmodels**, **Scikit-learn**, **XGBoost**, **TensorFlow/Keras**

---

## 📄 Future Scope

* Add external features (weather, holidays, events)
* Use multi-variate LSTM or Transformer models
* Deploy as a real-time forecasting dashboard

---

## 👨‍💼 Author

> This project was part of an academic term project focused on time series modeling and intelligent forecasting. The pipeline from raw data processing to deep learning modeling reflects a real-world data science workflow.

---

## 📦 File Structure

```
|- model_training.csv
|- EDA_and_Preprocessing.ipynb
|- ARIMA_SARIMA_Model.ipynb
|- LSTM_Model.ipynb
|- XGBoost_Model.ipynb
|- model_comparison_plot.png
|- README.md
```

---

## 🚀 Final Verdict

Classical methods like ARIMA still hold significant value, especially when:

* Data is univariate
* Trend & seasonality are not highly complex
* Simpler models generalize better

> "Sometimes, simplicity wins."
