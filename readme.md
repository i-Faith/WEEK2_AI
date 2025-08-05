# Disease Outbreak Prediction Using Machine Learning

This project focuses on **predicting disease outbreaks** using **environmental and climatic data** as part of a machine learning assignment aligned with **SDG 3 – Good Health and Well-being**.

## 📌 Objective

To build a supervised machine learning model that predicts the number of disease cases (e.g., dengue fever) based on features such as vegetation indices (NDVI), temperature, precipitation, and humidity.

## 🧠 Machine Learning Approach

- **Type**: Supervised Learning
- **Model**: Random Forest Regressor
- **Target Variable**: `total_cases`

## 📊 Dataset

The dataset includes weekly observations from a specific city (e.g., San Juan 'sj') and contains the following features:

- Climate: `precipitation_amt_mm`, `reanalysis_air_temp_k`, `station_avg_temp_c`, etc.
- Environmental: `ndvi_ne`, `ndvi_nw`, `ndvi_sw`, `ndvi_se`
- Time: `year`, `weekofyear`
- Target: `total_cases` (number of reported cases per week)

> Note: The `week_start_date` column was dropped, and missing values were forward filled.

## ⚙️ Preprocessing Steps

- Dropped non-numeric or irrelevant columns
- Forward-filled missing values
- Converted data to numerical format
- Split into training and test sets using `train_test_split`

## 🛠️ Model Training

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.model_selection import train_test_split

X = data.drop(columns=['total_cases', 'city'])
y = data['total_cases']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
