# forecasting-powerlifting-competition-totals
This project uses data from the OpenPowerlifting database (1975–2019), which contains approximately 800,000 observations curated by professional powerlifters. The data was aggregated to a monthly frequency by selecting the best overall total lift (TotalKg) per month across squat, bench press, and deadlift.

# Objective
The primary objective is to forecast monthly peak TotalKg for women in order to estimate future competitive benchmarks. In addition, targeted models were developed to forecast specific lifts, particularly the winning deadlift, to better understand performance dynamics at a more granular level.
# Time Series Structure
Although competitions occur at discrete events (“meets”), the data was transformed into a time series by aggregating to monthly maxima. The resulting series exhibits a clear nonlinear upward trend and strong seasonality. Stationarity, while not necessary for Sarimax, was examined through log transformation, first differencing and seasonal differencing
# Modeling Approach
The primary model is a SARIMA model specified as:
(1,1,1)(1,0,0,12)
Key features of the model
	•	Log-transformed target variable
	•	Reimputed exogenous variables
	•	Seasonal autoregressive component
The model achieved a Mean Absolute Percentage Error (MAPE) of 1.58%.

Alternative models included state-space approaches using Kalman Filters, which captured hidden structure in the data but introduced higher variance depending on specification.
# Key Features and Exogenous Variables
Body weight was a critical explanatory variable and significantly improved model performance. It reduced variance by accounting for differences across weight classes and athlete profiles.
Drug Testing Indicator: The inclusion of a tested/untested variable increased the predicted mean performance. This likely reflects selection bias, as top-performing athletes are more likely to be tested. The relationship appears correlational rather than causal.
# Future Work
Apply Hidden Markov Models (HMMs) to identify latent performance regimes.
Explore nonlinear or multiplicative relationships between exogenous variables and performance.
Model individual lifts separately to compare their long-term dynamics.
Investigate interactions between testing status and performance trajectories.
# Key Findings
There is a strong long-term upward trend in powerlifting performance since 1975. The trend appears to level off in the mid-2000s, potentially due to physiological limits or structural changes in the sport.
Men’s deadlift data is relatively stable and less noisy, likely due to a larger participant pool. Women’s data is more volatile, reflecting smaller sample sizes and less consistent competition fields.
Powerlifting performance trends reflect both physiological limits and structural dynamics within the sport. Accurate forecasting requires careful integration of time series techniques, domain knowledge, and thoughtful feature engineering.


