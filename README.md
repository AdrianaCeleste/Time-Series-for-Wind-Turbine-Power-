# Wind Turbine Power Prediction

## Executive Summary
This project analyzes wind turbine operational data to identify the key factors influencing power generation and evaluate machine learning models for predicting Active Power output.

Two modeling approaches were tested: one using WindSpeed, a key physical driver of turbine energy production, and another using time-based features derived from the timestamp. Results show that models including WindSpeed significantly outperform time-based models, highlighting the importance of environmental variables in energy forecasting.

The findings demonstrate how machine learning can support renewable energy optimization, forecasting, and operational planning.

---

# Business Problem
Wind energy companies must accurately forecast electricity production to optimize grid integration, maintenance planning, and energy trading strategies. However, predicting turbine output can be challenging due to the variability of environmental conditions.

This project addresses the problem of predicting wind turbine power generation using operational and environmental data. By identifying the variables that most strongly influence turbine output, energy operators can improve forecast accuracy, operational efficiency, and decision-making.

---

# Project Overview
This project analyzes wind turbine operational data to predict Active Power generation using machine learning techniques. The analysis explores the relationship between turbine operational variables and power output and compares different modeling approaches to evaluate their predictive performance.

The objective is to determine which variables best explain turbine power generation and how accurately machine learning models can predict energy production.

---

# Dataset
The dataset contains time-series operational data from a wind turbine, including environmental measurements and turbine component temperatures.

Examples of variables include:

- ActivePower  
- WindSpeed  
- RotorRPM  
- GeneratorRPM  
- Gearbox temperatures  
- Ambient temperature  
- Turbine operational status  

The data is recorded at 10-minute intervals, enabling detailed time-series analysis.

---

# Data Cleaning
Several preprocessing steps were applied to prepare the dataset:

- Removed duplicate records  
- Removed columns with constant values  
- Filtered invalid values where ActivePower < 0 (energy production cannot be negative)  
- Checked and handled missing values  
- Standardized the time index  

These steps ensured data consistency and reliability for modeling.

---

# Exploratory Data Analysis
Exploratory analysis focused on identifying relationships between turbine variables and power generation.

Techniques used:

- Time-series visualization  
- Feature normalization  
- Correlation analysis  
- Heatmap visualization  

The correlation analysis revealed that WindSpeed has the strongest relationship with ActivePower.

Top correlations with ActivePower:

| Variable | Correlation |
|--------|--------|
| WindSpeed | 0.937 |
| RotorRPM | 0.935 |
| GeneratorRPM | 0.934 |

Because WindSpeed is physically responsible for turbine energy production, it was selected as the main predictor for the first model.

---

# Models

## Model 1 — WindSpeed-Based Model
The first model predicts ActivePower using WindSpeed as the input variable.

Model used:

- XGBoost Regressor

Results:

| Metric | Value |
|------|------|
| R² | 0.970 |
| MAE | 63.05 |
| RMSE | 88.66 |
| MAPE | 0.475 |

This model performed very well, confirming the strong physical relationship between wind speed and turbine power output.

---

## Model 2 — Time Feature Model
The second model predicts power using time-based features only.

Features used:

- Hour  
- Minute  
- Day  
- Month  
- Year  
- Day of Week  
- Day of Year  

Results:

| Metric | Value |
|------|------|
| R² | 0.100 |
| MAE | 387.22 |
| RMSE | 503.61 |
| MAPE | 2.154 |

This model performed significantly worse, demonstrating that time variables alone cannot explain turbine power production.

---

# Future Power Forecast
Using the time-based model, future timestamps were generated from April 2020 to June 2020.

Predictions were generated using the trained model. While the model captures temporal patterns, the predictions are smoother and less accurate because they do not include key environmental variables such as WindSpeed.

---

# Key Insights
Important conclusions from the analysis:

- WindSpeed is the most important predictor of turbine power output  
- Turbine power generation shows strong nonlinear relationships  
- Time-based features alone are insufficient for accurate predictions  
- Including environmental variables significantly improves model performance  

---

# Technologies Used

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- XGBoost  
- Scikit-learn  

---

# Project Structure

Wind-Turbine-Power-Prediction  
│  
├── data  
│   └── Turbine_Data.csv  
│  
├── notebooks  
│   └── turbine_analysis.ipynb  
│  
├── images  
│   └── visualizations  
│  
└── README.md  

---

# Future Improvements
Possible improvements for this project:

- Include WindDirection and additional weather variables  
- Apply advanced time-series models (LSTM, Prophet)  
- Perform hyperparameter tuning  
- Implement feature importance analysis  
- Build a real-time prediction dashboard  

---

# Author
Adriana Celeste
