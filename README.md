### Time_Series_Homework
### Student: Michael De Paula

---
---

<p align="center">
    <ins><b>Machine Learning: Time Series and Regression Analysis:</b><br><ins>
    
</p>

Within this repository we are going to using using machine learning specifically time series and regression analysis to do two things: 
            
1. To decide whether it is a good time to invest the in the Japanese Yen currency.
2. Are the models being used in the regression analysis a good fit to analyze the currency.

We are using two separate jupyter lab notebooks (Time Series Analysis and Regression Analysis) to look at the data an write code to provide a conclusion for each item. Within the time series analysis we will be using the ARMA model, ARIMA model and GARCH. With the regression analysis we will be primarily focused on linear regression and RMSE (Root Mean Squared Error) in order to determine fit. 

We will be using the following imports:

- import numpy as np
- import pandas as pd
- from pathlib import Path
- from sklearn.linear_model import LinearRegression
- from sklearn.metrics import mean_squared_error
- %matplotlib inline
- import statsmodels.api as sm
- import warnings
- from statsmodels.tsa.arima_model import ARMA
- from statsmodels.tsa.arima_model import ARIMA
- import arch 
- from arch import arch_model
- warnings.filterwarnings('ignore')

__Time Series Analysis:__

We begin by listing the imports for each library being used in this notebook. We read in the data as a dataframe using Pandas. The data seems to be Japanese Yen historical pricing data from the 1970s to 2019. The dataset was then trimmed to begin in the 1990s and we begin forecasting. We plotted the Yen Futures Settling Prices from 1990 to 2019. We then used the Hodrick-Prescott Filter or HP Filter to determine the noise and trend within the settle price dataframe and filter it out. When filtering out noise and trend we included it in a new dataframe as columns with the settle prices. We then plotted the settle prices vs the trend in a line chart that visualized the original Yen futures plot with a trend line running in unison. We then plotted to noise which when visualized resembles exactly that "Noise". 

- Forecasting:

We are now in the forecasting part of this notebook starting with the ARMA model which is a combination of the AR model (Auto Regressive - Past values used to predict future values) and the MA model (Moving Average - Past errors used to predict future values). Using this ARMA model we plotted a 5 day returns forecast. With a high AIC and BIC the model seems to be a good fit. We then did the same using an ARIMA model which is similar to the ARMA model but includes a differentiator for DELTA within the order. With a P-value above 0.05 and the AIC and BIC being significantly higher it is probably a better fit than the ARMA model. Finally, we used the GARCH model to determine volatility of Japanese Yen future returns and plotted the forecasted returns and determined the volatility continues to increase. 

__Regression Analysis:__

With the regression analysis we begin with the same Yen dataframe as before. We prepare the dataframe by calculating the return wit the pct.change() function from pandas and including the result as a column. Using the shift function we also include Lagged returns within the data. Using the returns and lagged returns data we setup our testing and training data in order to prepare our linear regression model. Using this information we then make predction using our test data and we visualize our Returns vs Predicted Returns. WE then use our test data (X and y) as our out of sample data as well as our In sample performance and calculate an RMSE for each to test the fitness of each model against the data and come to a conclusion. 