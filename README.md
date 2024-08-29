# Electric Vehicle Lithium-ion Battery Ageing Analysis Under Dynamic Conditions: A Machine Learning Approach

## Project Overview

This project investigates the health monitoring and prediction of lithium-ion batteries, focusing on their performance in electric vehicles. The study is based on the research by Swarnkar et al., which highlights the challenges of battery degradation influenced by factors such as charge/discharge rates and temperature. The approach involves applying machine learning techniques like Multiple Linear Regression, M-SVM, and LSTM-GPR to predict the battery’s state of health (SOH).

## Data Description

The dataset consists of measurements from four lithium-ion batteries (B0005, B0006, B0007, B0018) subjected to three different operational profiles: charge, discharge, and impedance. Charging was performed in constant current (CC) and constant voltage (CV) modes, while discharging was conducted at specific current levels until the batteries reached end-of-life (EOL) criteria. Impedance measurements were taken through electrochemical impedance spectroscopy (EIS). The dataset allows for the prediction of remaining charge and remaining useful life (RUL) of the batteries.

## Data Processing

The data was extracted from `.mat` files and organized into DataFrames for charge, discharge, and impedance cycles. The datasets were structured to include key variables such as voltage, current, temperature, and capacity for charge and discharge cycles, and impedance parameters for impedance tests. This organization facilitates efficient analysis and modeling.

## Exploratory Data Analysis (EDA)

Several EDA techniques were applied to understand battery degradation patterns:
- **Battery Health Over Cycles**: Analysis of battery capacity and state of health (SOH) across different cycles to visualize degradation trends.
- **Voltage and Current Trends**: 3D plots of voltage and current during charge and discharge processes to assess stability and performance over time.
- **Capacity Analysis**: Visualization of capacity changes during discharge to illustrate the gradual reduction in battery performance.
- **Impedance Comparison**: Analysis of electrolyte and charge transfer resistances to understand changes in battery impedance with aging.

## Key Findings

- **Degradation Patterns**: Capacity decreases with cycle number, indicating typical battery aging. The SOH color gradient from high to low reflects reduced battery health over time.
- **Voltage and Current Stability**: Voltage and current during charging and discharging show stable trends initially, with degradation evident in later cycles.
- **Impedance Increase**: Higher impedance values in later tests suggest increased resistance due to aging, affecting battery performance.

## Modeling and Results

### Battery 5 Modeling

- **Initial Attempt**: Applied Support Vector Regression (SVR) to predict SOH using discharge data from Battery B0005. The base SVR model showed poor performance with a significant disparity between actual and predicted SOH values.
- **Improvement**: After tuning hyperparameters with GridSearchCV, the model’s performance still didn’t meet expectations. Linear Regression showed better alignment between actual and predicted values.
- **Final Evaluation**: Evaluated various models including LinearSVR, Linear Regression, SGD Regressor, and XGBoost. The XGBoost Regressor outperformed all others in terms of prediction accuracy.

### Combined Charge and Discharge Data

- **Data Integration**: Combined charge and discharge data from multiple batteries and filled in missing values. Standardized and processed the data to prepare for modeling.
- **Model Evaluation**: Applied LinearSVR, Linear Regression, SGD Regressor, and XGBoost to the combined dataset. XGBoost consistently delivered the best performance metrics, showing lower RMSE, MAE, and higher R2 scores compared to other models.

### Evaluation Metrics

- **XGBoost**: Demonstrated superior performance with the lowest RMSE and highest R2 score, indicating a robust model for predicting battery capacity and SOH.
- **SGD Regressor**: Achieved good results with minimal error and strong R2 score, but XGBoost remained the top performer.

## Visualizations

- **Performance Comparison**: Visualized model performance across different metrics to highlight the effectiveness of the XGBoost Regressor.
- **Actual vs Predicted SOH**: Plotted graphs comparing actual and predicted SOH values for various models to illustrate the prediction accuracy.

## Conclusion

This project provides insights into battery ageing dynamics and demonstrates how machine learning and data analysis can enhance battery management systems in electric vehicles. The XGBoost Regressor was identified as the most effective model for predicting battery health, outperforming other techniques in terms of accuracy and reliability.
