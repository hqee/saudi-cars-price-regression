# 🚗 Saudi Used Car Price Prediction

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![CatBoost](https://img.shields.io/badge/Model-CatBoost-green)](https://catboost.ai/)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen)]()

## 📌 Project Overview

The used car market in Saudi Arabia is dynamic and often inconsistent. A common issue is **price uncertainty**, especially when sellers leave prices listed as "0" or "Negotiable". This creates inefficiencies and makes it difficult for buyers and sellers to identify a fair market price.

This project builds a **Machine Learning Regression Model** to estimate the fair value of used cars based on attributes like Make, Model, Year, Mileage, Transmission, Region, and Engine Size.

**Business Impact:**

- **For Sellers:** Set competitive and accurate listing prices.
- **For Buyers:** Detect overpriced listings and negotiate with data.
- **For Marketplaces:** Filter low-quality or zero-price listings automatically.

---

## 📂 Repository Structure

```text
saudi-used-car-prediction/
│
├── data/
│   └── data_saudi_used_cars.csv
│
├── models/
│   └── saudi_car_price_model.sav
│
├── notebooks/
│   └── Saudi_Car_Price_Analysis.ipynb
│
├── images/
│   ├── actual_vs_pred.png
│   └── feature_importance.png
│
├── README.md
└── requirements.txt
```

---

## 🛠️ Methodology

### 1. Data Cleaning

Key domain-driven cleaning steps:

- Removed rows where `Price = 0` or marked as `Negotiable`.
- Removed duplicate listings.
- Imputed missing categorical values using mode.
- Standardized inconsistent fields like Year and Mileage.

### 2. Advanced Preprocessing Pipeline

A full Scikit-Learn Pipeline with ColumnTransformer was used.

| Feature Type                                 | Method          | Reason                                                   |
| -------------------------------------------- | --------------- | -------------------------------------------------------- |
| High-Cardinality Categoricals (Make, Region) | Binary Encoding | Reduces dimensionality while preserving category meaning |
| Low-Cardinality Categoricals (Gear, Origin)  | OneHot Encoding | Best for small category sets                             |
| Numerical (Mileage, Engine, Year)            | Robust Scaler   | Handles heavy outliers better than StandardScaler        |

### 3. Model Benchmarking

Five algorithms were compared with 5-Fold Cross-Validation:

- Ridge Regression
- Random Forest
- XGBoost
- LightGBM
- **CatBoost (Best Model)**

CatBoost was then optimized using hyperparameter tuning to achieve the best RMSE.

---

## 📊 Model Performance

Evaluated on a separate 20 percent test set.

| Metric   | Score          | Meaning                                       |
| -------- | -------------- | --------------------------------------------- |
| **R²**   | **0.8754**     | Model explains 87.5 percent of price variance |
| **MAE**  | **14,306 SAR** | Average deviation from actual prices          |
| **RMSE** | **26,544 SAR** | Captures impact of high-outlier prices        |

### Actual vs Predicted

Upload this plot inside `images/actual_vs_pred.png`.

### Feature Importance

Top predictors:

1. Year
2. Engine Size
3. Make
4. Mileage

Upload bar chart image to `images/feature_importance.png`.

---

## 🚀 How to Run This Project

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/saudi-used-car-prediction.git
cd saudi-used-car-prediction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run Notebook

Open:

```
notebooks/Saudi_Car_Price_Analysis.ipynb
```

---

## 🔮 Future Improvements

- Deployment using Streamlit.
- Separate models for Economy vs Luxury segments.
- Integrate external data like accident history.

---
