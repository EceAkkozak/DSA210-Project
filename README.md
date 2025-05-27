# DSA210-Project

According to the feedback I received before the Machine Learning step of my project, I realized that I could not fully provide what was expected from me in the project. My previous project, which is located on my github under the name of old version, consisted of Istanbul traffic density and public transportation data sets. While I was planning to cover the last quarter of 2024, when I looked back at my data sets, I noticed that there was a big inconsistency between the time periods they covered, the public transportation data had stopped being shared after a certain period of time. For this reason, I kept my traffic density data and added weather data to it, and started working from scratch with Istanbul traffic density and weather for January 2024. While I was re-doing my project, I realized that the previous version of my project was quite incomplete, and this time the work I put forward was shaped within the scope of feedback and office hours, I hope it meets expectations.

## Project Overview
This project focuses on analyzing the relationship between weather conditions and traffic density in Istanbul. 
Using hourly data from January 2024, the study investigates how environmental factors such as temperature, precipitation, humidity, windspeed, and visibility influence average traffic speed. 
As Istanbul is a densely populated metropolitan area, understanding how weather impacts traffic flow can provide valuable insights for urban mobility planning and infrastructure resilience. 
The dataset includes hourly weather records and traffic intensity metrics, merged and cleaned for analysis. Basic statistical tests and machine learning models are used to quantify the strength of these relationships and to forecast daily average speeds under varying weather conditions.

## Data Sources
Weather Data: Collected from Visual Crossing website where Istanbul's hourly weather conditions for January 2024. (https://www.visualcrossing.com/weather-query-builder/)

Traffic Density Data: İBB’s database where traffic density from Istanbul's January 2024 hourly data is shown by minimum speed, maximum speed, and average speed. (https://data.ibb.gov.tr/dataset/hourly-traffic-density-data-set)

## Motivation
Istanbul frequently struggles with traffic congestion, often worsened by unpredictable weather patterns. By uncovering the statistical links between atmospheric conditions and traffic performance, this project aims to support smarter, data-driven traffic management strategies. In the long term, these insights can aid city authorities in making informed decisions to mitigate congestion, especially during adverse weather conditions.

## Objectives
- To explore the correlation between hourly weather variables and traffic indicators.  
- To determine which environmental factors most significantly impact average vehicle speed.  
- To develop a predictive model for daily average speed based on weather and traffic data.  
- To provide recommendations for integrating weather forecasting into urban traffic planning.

## Tools and Technologies
The analysis was conducted using:  
- **Python** for data processing, analysis, and visualization  
- **Pandas** for data manipulation  
- **Seaborn/Matplotlib** for exploratory data visualization  
- **Scikit-learn** for linear regression modeling  
- **Jupyter Notebook** (via Anaconda) for interactive development  
- **GitHub** for code versioning and sharing  

## Expected Outcome
This project is expected to reveal how weather variations affect traffic flow in Istanbul and to what extent these factors can be used to predict average daily speed. By visualizing patterns and building a basic linear regression model, the study seeks to generate actionable insights for municipal transportation departments. These findings may support the design of weather-adaptive traffic control systems and help reduce congestion through anticipatory planning.



## Exploratory Data Analysis (EDA)

## Descriptive Statistics
![image](https://github.com/user-attachments/assets/51e5cb01-b742-4f14-b053-7e2cfc16cb65)
fter merging weather and traffic datasets, the resulting dataset contains 957,453 rows, indicating a high-resolution hourly-level dataset covering multiple traffic points across Istanbul.
Key descriptive statistics include:
Average Speed: Mean of 56.28 km/h, ranging from 1 km/h to a maximum of 181 km/h, reflecting both congested and free-flow conditions.
Maximum Speed: Average of 97.5 km/h, reaching up to 241 km/h, which may include outliers or unusually fast records on low-traffic roads.
Minimum Speed: Average of 24.7 km/h, with some values as low as 1 km/h, indicating heavy congestion at times.
Number of Vehicles: Mean of 82.3 vehicles per record, but a wide range up to 1,550, showing highly variable traffic density across different areas and times.
Weather features:
Temperature: Ranges from –0.8°C to 16.6°C, with a mean of ~8°C, consistent with typical January conditions in Istanbul.
Precipitation: Highly skewed with most values at 0, but occasional spikes reaching up to 14,931 mm, confirming the need for filtering or binning extreme values.
Visibility and Wind Speed: Fairly consistent values, suggesting limited variation over the period.


## Correlation Heatmap
![image](https://github.com/user-attachments/assets/12ece788-c13a-4d44-9759-e66e2385c6c3)
The correlation heatmap confirms that temp and feelslike are nearly identical (ρ = 0.98), which is expected and suggests potential redundancy. AVERAGE_SPEED is strongly correlated with both MINIMUM_SPEED (0.79) and MAXIMUM_SPEED (0.81), validating internal consistency in traffic data.
Weather-related variables show weak correlations with AVERAGE_SPEED, such as windspeed (−0.04), precip (−0.01), and humidity (−0.02), indicating that no single weather factor dominates speed outcomes linearly. However, this does not rule out nonlinear or interaction effects, which could be further explored in the modeling stage.


## Boxplots
![image](https://github.com/user-attachments/assets/fe55a74d-e3ba-47a2-af51-39d8ab24a974)
This plot shows the distribution of average speed across different precipitation levels (binned). As precipitation increases, a noticeable decrease in average speed is observed—especially in the lowest two bins where speeds are generally higher and more variable.
This suggests that drivers tend to slow down during heavier rainfall, indicating a cautious driving pattern and confirming that precipitation negatively impacts traffic flow.


![image](https://github.com/user-attachments/assets/1e235012-ad7e-4ba2-b012-74bd885694fd)
This boxplot shows how average speed varies across different temperature ranges. The distribution of average speed remains relatively stable across all bins, with only slight increases at higher temperatures.
This suggests that temperature alone does not have a strong direct impact on traffic speed, unlike precipitation. However, the consistency across bins supports the earlier correlation heatmap findings, where temperature showed minimal linear correlation with average speed.


![image](https://github.com/user-attachments/assets/fe9e9032-17eb-4716-88b6-d82213d32378)
The number of vehicles slightly increases with higher humidity levels, but the distribution remains wide and heavily skewed with many outliers. This suggests that humidity may have a marginal influence on traffic volume, but other factors likely play a more dominant role.


![image](https://github.com/user-attachments/assets/2b1ad982-5c40-4d8e-8464-65cbfc7bbc4f)
Average speed appears relatively stable across all visibility levels, with only minimal variation between bins. This suggests that within the observed range, visibility does not have a significant impact on traffic speed in Istanbul during January.


![image](https://github.com/user-attachments/assets/228503a8-1c81-4156-aed4-bc97457bbb8a)
Maximum speed shows a slight upward trend as visibility improves, though the differences are minor and distributions largely overlap. This implies that better visibility may encourage higher speeds, but the effect appears weak in this dataset.


![image](https://github.com/user-attachments/assets/106421a5-ba2d-4418-a930-3589fb2af21a)
There is a clear downward trend in maximum speed as precipitation increases, especially in the highest rainfall bins. This suggests that heavier rainfall leads to reduced maximum driving speeds, indicating cautious behavior and reduced traffic performance under wet conditions.


![image](https://github.com/user-attachments/assets/34e5084d-19d9-471f-99df-0942b65d7c64)
Average speed decreases slightly as precipitation level increases, with the lowest median speed observed under heavy rain conditions. While the overall distributions are similar, this pattern reinforces the negative impact of rainfall on traffic flow.


## Histograms
![image](https://github.com/user-attachments/assets/2cf12f0b-0120-4c1b-afd3-61d9d139e490)
The temperature distribution is multimodal, with peaks around 4–5 °C and 14 °C, indicating two dominant temperature clusters during January. This suggests frequent temperature shifts throughout the month, possibly due to varying weather systems affecting Istanbul.


![image](https://github.com/user-attachments/assets/4c9841a6-73da-4525-bc9d-50b5b6794c29)
Humidity levels in January are mostly concentrated between 70% and 90%, showing a slightly right-skewed distribution. This indicates that Istanbul experienced consistently high humidity during the month, which may contribute to traffic slowdowns when combined with other weather conditions.


![image](https://github.com/user-attachments/assets/6d706f4f-422f-4b0f-99a6-fba6d0fa1faf)
The precipitation distribution is highly right-skewed, with the vast majority of values clustered near zero. This indicates that most hours in January had little to no rainfall, highlighting the sparsity of wet weather events during the observed period.


![image](https://github.com/user-attachments/assets/de13dead-63a7-4b05-98ec-aaaff1586e28)
The distribution of vehicle counts is heavily right-skewed, with most observations concentrated under 50 vehicles per record. This suggests that low-traffic conditions are much more common, while high vehicle counts occur relatively rarely.


![image](https://github.com/user-attachments/assets/cf234517-36a7-4fbb-8e86-40b75d265394)
The average speed distribution is bimodal, with peaks around 30 km/h and 85 km/h, reflecting distinct traffic flow patterns—possibly corresponding to congested versus free-flow conditions. This separation suggests that traffic speed in Istanbul during January tends to cluster into either low-speed or high-speed regimes.


![image](https://github.com/user-attachments/assets/9511403d-303e-45e2-a619-b9c22681ca02)
Average speed is highest during late-night and early-morning hours, and steadily declines after 6 AM, reaching the lowest point around 6 PM, likely due to evening rush hour. This clear daily pattern highlights the impact of commuter traffic on urban mobility.


![image](https://github.com/user-attachments/assets/88fa36fe-b927-4e15-80f9-522598651701)
The number of vehicles surges sharply after 5 AM, peaking during the morning and evening rush hours, and decreases again late at night. This pattern aligns with typical urban commuting behavior and explains the corresponding dips in average speed during peak hours.


![image](https://github.com/user-attachments/assets/f776cdd0-945b-49a7-9490-b8479c7e6fab)
This line chart shows daily changes in average speed and vehicle count during January 2024. While average speed stays mostly stable, the number of vehicles changes a lot from day to day.
On days with more vehicles, speed slightly drops, suggesting that heavier traffic slows down movement—just as expected. These changes could be due to weekdays, weekends, or weather effects.


![image](https://github.com/user-attachments/assets/2f69a9da-f69e-4a1e-a9cd-439edca35fd9)
This line plot shows a general downward trend in average speed as the number of vehicles increases, especially after around 300 vehicles. The relationship becomes more scattered at higher volumes, but overall it suggests that heavier traffic leads to slower speeds—supporting the expected congestion effect.


![image](https://github.com/user-attachments/assets/756b1e21-60a3-4bdb-abf8-06bd89665a2b)
This plot shows a strong positive relationship between maximum speed and average speed, with the two increasing almost linearly up to around 150 km/h. After that point, average speed levels off, suggesting a limit to how much higher maximum speeds affect overall flow—possibly due to traffic regulations or physical constraints.


![image](https://github.com/user-attachments/assets/99c8accc-f7c9-48a6-9798-0627e2db554c)
This plot reveals a very strong and nearly linear relationship between minimum speed and average speed. As the lowest speed recorded increases, the average speed rises consistently—indicating that fewer slow-moving vehicles contribute to a smoother overall traffic flow.



## Correlations and Hypothesis Testing

NUMBER_OF_VEHICLES vs AVERAGE_SPEED
Correlation: –0.0510
P-Value: 0.0000
➤ There is a statistically significant but very weak negative correlation, meaning that as the number of vehicles increases, average speed slightly decreases—supporting the idea of traffic congestion.

MAXIMUM_SPEED vs AVERAGE_SPEED
Correlation: 0.8123
P-Value: 0.0000
➤ A very strong, statistically significant positive correlation shows that maximum speed and average speed increase together—indicating internal consistency within the traffic data.

MINIMUM_SPEED vs AVERAGE_SPEED
Correlation: 0.7948
P-Value: 0.0000
➤ Another strong, significant correlation; higher minimum speeds are associated with higher average speeds, suggesting smoother traffic flow.

PRECIPITATION vs AVERAGE_SPEED
Correlation: –0.0111
P-Value: 0.0000
➤ Despite a very weak negative correlation, the result is statistically significant due to the large sample size. Precipitation has a slight slowing effect on traffic.

TEMPERATURE vs AVERAGE_SPEED
Correlation: 0.0018
P-Value: 0.0714
➤ The null hypothesis cannot be rejected. There is no significant relationship between temperature and average speed.

HUMIDITY vs NUMBER_OF_VEHICLES
Correlation: 0.0267
P-Value: 0.0000
➤ A very weak but statistically significant positive relationship—higher humidity is slightly associated with higher traffic volume.

VISIBILITY vs AVERAGE_SPEED
Correlation: –0.0423
P-Value: 0.0000
➤ A weak but significant negative relationship; lower visibility may contribute to slightly reduced driving speeds.

WINDSPEED vs AVERAGE_SPEED
Correlation: –0.0360
P-Value: 0.0000
➤ A weak negative correlation indicates that higher wind speeds slightly reduce average traffic speed.

VISIBILITY vs MAXIMUM_SPEED
Correlation: 0.0062
P-Value: 0.0000
➤ Statistically significant but negligible correlation. Visibility has almost no practical effect on maximum speed.

PRECIPITATION vs MAXIMUM_SPEED
Correlation: –0.0198
P-Value: 0.0000
➤ A very small but significant negative relationship. Increased precipitation slightly reduces maximum speed.



## Machine Learning

![image](https://github.com/user-attachments/assets/7bc666f2-2216-4a7a-b07d-0378cf9a1e35)
This plot compares the predicted and actual average daily speeds from January 25 to 31, using a model trained on earlier data. The predicted values (orange line) follow the real data (blue line) quite closely, showing the model captures general trends well, especially the mid-week peak on January 28 and the significant drop on January 29.
Although the model slightly overestimates or underestimates on some days, the overall pattern is preserved—indicating that the relationship between weather and traffic conditions is reasonably well learned. This suggests that the model can be useful for short-term traffic speed forecasting, though improvements may be needed for more precise daily predictions.


## Forcast Results

--- Forecast Results (25-31 Ocak) ---
         date     Actual  Predicted
14 2024-01-25  55.459800  56.210814
15 2024-01-28  58.337056  58.770677
16 2024-01-29  53.859562  53.448327
17 2024-01-30  54.177653  53.800620
18 2024-01-31  55.082385  56.146338

Performans Metrikleri:
R² skoru: 0.8257
RMSE: 0.66
MAE: 0.61

Explanations:
Forecast Results (January 25–31)
Date	Actual Average Speed (km/h)	Predicted Speed (km/h)	Difference (≈)
Jan 25	55.46	56.21	+0.75
Jan 28	58.34	58.77	+0.43
Jan 29	53.86	53.45	–0.41
Jan 30	54.18	53.80	–0.38
Jan 31	55.08	56.15	+1.07
The predicted values closely match the actual speeds, with most daily differences staying within ±1 km/h.

R² Score = 0.8257
The model explains approximately 82.57% of the variance in average speed, indicating a strong and meaningful fit.
RMSE = 0.66 km/h
The root mean square error shows that the model’s predictions deviate by about 0.66 km/h on average—reflecting high precision.
MAE = 0.61 km/h
The mean absolute error is also low, confirming the model's consistent accuracy across days.

The model performs well in short-term (one-week) average speed forecasting. Its high R² score and low error values suggest it can reliably estimate traffic speed based on weather and traffic data—making it a practical tool for municipalities and traffic planners seeking data-driven insights.













































