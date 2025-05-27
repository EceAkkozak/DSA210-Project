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

[image](https://github.com/user-attachments/assets/f4d77512-d3e7-47f8-9f52-e65b2e2d5034)

The correlation heatmap confirms that temp and feelslike are nearly identical (ρ = 0.98), which is expected and suggests potential redundancy. AVERAGE_SPEED is strongly correlated with both MINIMUM_SPEED (0.79) and MAXIMUM_SPEED (0.81), validating internal consistency in traffic data.
Weather-related variables show weak correlations with AVERAGE_SPEED, such as windspeed (−0.04), precip (−0.01), and humidity (−0.02), indicating that no single weather factor dominates speed outcomes linearly. However, this does not rule out nonlinear or interaction effects, which could be further explored in the modeling stage.


![image](https://github.com/user-attachments/assets/12ece788-c13a-4d44-9759-e66e2385c6c3)

