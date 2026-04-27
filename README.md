# New York City Taxi Fare Prediction

## 🚀 Overview
This project focuses on predicting the fare amount for taxi rides in New York City based on pickup and dropoff coordinates, passenger counts, and datetime information. It downloads and utilizes the dataset from the Kaggle "New York City Taxi Fare Prediction" competition.

## 🛠️ Features & Data Processing
* **Data Loading**: To ensure efficient processing, the notebook samples 500,000 rows from the training dataset.
* **Data Cleaning**: Rows with missing dropoff coordinates are removed. Outliers are also filtered out by restricting fare amounts to a $1–$500 range, keeping passenger counts between 1 and 6, and restricting coordinates to the approximate geographical bounds of NYC (Latitudes 40 to 42, Longitudes -75 to -72).
* **Feature Engineering**: 
  * Splits the `pickup_datetime` column to extract `year`, `month`, `day`, `weekday`, and `hour` features.
  * Calculates the exact trip distance between the pickup and dropoff points using the Haversine formula.
  * Computes the Haversine distance from pickup locations to major NYC landmarks: JFK Airport, LaGuardia (LGA) Airport, Newark (EWR) Airport, the Metropolitan Museum of Art, and the World Trade Center.

## 🧠 Models Trained
The notebook frames this as a regression problem and evaluates the models using Root Mean Squared Error (RMSE) on an 80/20 train-validation split. The following models are trained:
* **Mean Regressor** (A hardcoded baseline model)
* **Linear Regression**
* **Ridge Regression**
* **Random Forest Regressor**
* **XGBoost Regressor**

## 📦 Dependencies
To run this notebook, ensure you have the following Python libraries installed in your environment:
* `opendatasets` (Used for directly downloading the Kaggle dataset)
* `pandas`
* `numpy`
* `scikit-learn`
* `xgboost`
* `matplotlib` & `seaborn` (For Exploratory Data Analysis)

## 💡 Usage
1. Run the initial cells to install the necessary packages and download the data.
2. Execute the EDA, cleaning, and feature engineering cells. The script will save the processed training, validation, and testing sets into compressed `.parquet` formats (`train.parquet`, `val.parquet`, `test.parquet`).
3. Run the model cells to view their respective RMSE scores. The code includes a helper function to automatically map test predictions to Kaggle's expected format and output them as CSV files (e.g., `submission1.csv`, `ridgeModel.csv`, `RandomForestModel.csv`, `XGBModel.csv`).
