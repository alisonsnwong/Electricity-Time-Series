# Electricity Sales in California: A Time Series Analysis Approach

This time series analysis project aims to analyze and forecast electricity sales using historical data from 2010 to 2022. The analysis involves several key steps: time series decomposition, residual analysis, ARMA model fitting, predicting future values, and spectral analysis. We accurately forecast values and find that there exists strong annual and semi-annual components in the data.

 :robot: Data Source: U.S Energy Information Administration (EIA). Used Electricity Sales data from 2010 - 2022
 
 :robot: Tools: R/R-studio, LaTex 
 
 ## Data Preprocessing:
1. Dropped unnecessary columns
2. **Exploratory Data Analysis** 
    * Time series decomposition: yearly trend, seasonality, residuals  
3. **Analysis of residuals** showed 2 outliers in 2018
    * Solution: fit separate ARMA models to time series data before and after the outlier -> forecast and backcast the outlier value -> replace outliers by with the average of the forecasted and backcasted values
4. **Hypothesis Testing for Stationarity**: using the Augmented Dickey-Fuller test for stationarity
    * Rejected the null hypothesis of non-stationary. Can use residuals for the model fitting process
5. Excluded data from 2022 during the model fitting process to assess prediction accuracy.

 ## Summary of Steps:
 1. **ARMA Model Fitting on residuals**: Created a function to determine the optimal ARMA(p, q) model that minimizes the AIC. Selected ARMA(4,4) model.
    * Independent residuals with white noise characteristics, normally distributed 👍
    * Conducted significance test for the coefficients and only kept statistically significant coefficients
2. **Trend Fitting**: 4th-degree polynomial estimated the trend line accurately with an adjusted R-squared value of 0.926
3. **Prediction**
   * Summed predicted trend, seasonality, and residuals to obtain the predicted time series for 2022. Obtained a MAPE of 5.08%, meaning that the average absolute percentage difference between the predictions and the actuals is 5.08%.
