# Time-series-Sales-forecast
## Business objective
From available data about performance of company across many media platforms, build a model to predict sales

## Overview (only for modelling)
Note: if you want to see full analysis, check out the code script: 
12_Capstone_WORK.ipynb

Account subscription by week:
<img width="1001" height="419" alt="image" src="https://github.com/user-attachments/assets/4f694956-374c-492c-8eff-9158fe95bd54" />

As shown, the sales peak around May to July every year for 3 consecutive years. Similarly, the trend line goes sideway, signalling no clear trend. Therefore, this data is stationary while having seasonality.

## Modelling
Afterr testing with OLS, ARIMA, SARIMA, ARIMAX, and SARIMAX, I finally choose ARIMA with hyper-parameters as 3,0,3 for p,d,q respectively.
This model performs better than the others in terms of RMSE, MAPE, AIC and BIC. For detail metrics' values, check out the code script.

## Result

<img width="608" height="425" alt="image" src="https://github.com/user-attachments/assets/f9652ee8-0456-4bf4-ba72-4b0667bae227" />

Intepretation

Summary result:

Statistically significant base level of 8.63
- While forcast error (ma.L1, ma.L2, ma.L3) all significantly have positive impact on current value, the previous time-step values (ar.L1, ar.L2, ar.L3) did not agree with each other
- Indeed, while ar.L2 has negative impact on current value, ar.L3 has positive one.
- sigma2 representing residual variance is small and significant (0.0055 with p-val < 0.05) -> a good model

Diagnostic test:
- Prob(Q) > 0.05, indicating residuals are independant and resemble random noise, in turn indicating no auto-correlation (this is good because it helps satisfy assumption of a good time-series model, which is residuals are like white noise)
- JB > 0.05 indicates residuals are normally distributted, a key component to satisfy assumptions of time-series model
- Hetereokedasticity > 0 .05 (good) means the variance is residual is constant over time, this ensures reliability of model over time.



