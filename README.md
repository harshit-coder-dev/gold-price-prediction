# 🪙 Gold Price Prediction Using Machine Learning & LSTM

## 📌 Project Overview

This project focuses on predicting gold prices using historical market data and time-series modeling techniques. The objective is to build a reliable and leakage-free prediction system by applying traditional machine learning models as well as a deep learning–based LSTM model. The project also compares model performance and forecasts future gold prices for short-term horizons.

---

## 📂 Dataset

* **Source:** Kaggle
* **Data Type:** Historical daily gold price data
* **Key Columns:**

  * Date
  * Price (Close)
  * Open
  * High
  * Low
  * Volume
  * Change %

---

## 🧹 Data Preprocessing

The raw dataset required significant cleaning before modeling:

* Converted date column to datetime format
* Removed commas, percentage signs, and text symbols from numerical columns
* Converted volume values (e.g., `K`) into numeric format
* Handled missing values using forward fill
* Sorted data chronologically to preserve time order

This ensured the dataset was clean, numeric, and suitable for time-series analysis.

---

## 🧠 Feature Engineering (for ML Models)

To enable traditional machine learning models to capture temporal patterns, the following features were engineered:

* Lag features (`price_lag_1`, `price_lag_2`, `price_lag_3`)
* Rolling statistics (rolling mean and rolling standard deviation)
* Past volume (`volume_lag_1`)
* Daily returns
* Calendar features (day, month, day of week)

Only **past information** was used to avoid data leakage.

---

## 🤖 Machine Learning Models

The following regression models were trained and evaluated:

* Linear Regression
* Decision Tree Regressor
* Random Forest Regressor
* Gradient Boosting Regressor
* XGBoost Regressor

### Model Evaluation

* Time-based train–test split was used instead of random splitting
* Walk-forward validation was implemented to simulate real-world forecasting
* Evaluation metrics:

  * Mean Absolute Error (MAE)
  * Root Mean Squared Error (RMSE)
  * R² Score

---

## 🔁 Walk-Forward Validation

Walk-forward validation was applied to ensure realistic performance measurement.
In this approach, models were retrained sequentially using historical data to predict the next time step, closely simulating live market prediction scenarios.

---

## 🧬 LSTM (Deep Learning Model)

An LSTM (Long Short-Term Memory) neural network was implemented to model gold prices as a sequence.

### Why LSTM?

* Gold prices exhibit strong temporal dependency
* LSTM can learn long-term and short-term patterns automatically
* Reduces the need for manual lag feature engineering

### LSTM Characteristics

* Univariate LSTM using only historical prices
* Data normalization using MinMaxScaler
* Sliding window approach (last 30 days → next day prediction)
* Performance comparable to ensemble ML models

---

## 🔮 Forecasting

The trained models were used to generate:

* **Next-day gold price prediction**
* **7-day forecast**
* **30-day forecast**

Recursive forecasting was applied, where each predicted value is used as input for the next time step.

---

## 📊 Model Comparison Summary

| Aspect              | ML Models | LSTM       |
| ------------------- | --------- | ---------- |
| Feature Engineering | Required  | Optional   |
| Sequence Learning   | ❌         | ✅          |
| Interpretability    | High      | Low        |
| Training Speed      | Fast      | Slower     |
| Data Requirement    | Low       | Higher     |
| Performance         | Strong    | Comparable |

---

## 🖥️ Streamlit Dashboard

An interactive Streamlit dashboard was developed to:

* Visualize historical gold prices
* Display short-term forecasts
* Compare predictions across models

During development, Google Colab was used along with tunneling, and the application can be deployed on Streamlit Community Cloud for public access.

---

## 📌 Key Learnings

* Importance of avoiding data leakage in time-series modeling
* Effectiveness of feature engineering for traditional ML models
* Practical application of walk-forward validation
* Understanding when deep learning models like LSTM are beneficial
* Trade-offs between interpretability and model complexity

---

## 🚀 Conclusion

This project demonstrates a complete end-to-end pipeline for time-series forecasting using both machine learning and deep learning approaches. By combining proper data preprocessing, feature engineering, robust validation techniques, and model comparison, the system provides realistic and reliable gold price predictions suitable for academic and real-world applications.

---
