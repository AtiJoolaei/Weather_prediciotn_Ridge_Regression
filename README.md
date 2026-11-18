# Weather Prediction Using Machine Learning 🌦️

## Project Overview

This project focuses on predicting the next day's maximum temperature using historical weather data and Machine Learning techniques.

The main objective is to explore historical weather patterns, prepare and clean the dataset, engineer meaningful features, and build a predictive model using **Ridge Regression**.

The project demonstrates a practical Machine Learning workflow, from raw data preprocessing to model evaluation.

The data set is prepared oneline from the  National Centers for Environmental Information (NOAA). 

## Objectives

- Explore and understand historical weather data.
- Handle missing values and clean the dataset.
- Identify relevant weather features for temperature prediction.
- Apply Feature Engineering to capture short-term and seasonal weather patterns.
- Train a Ridge Regression model.
- Evaluate model performance using Mean Absolute Error (MAE).
- Analyze prediction errors and identify opportunities for improvement.

## Dataset

The project uses historical weather measurements stored in `weather_measurement.csv`.

The initial dataset includes the following weather variables:

- `PRCP`: Precipitation
- `TMAX`: Maximum temperature
- `TMIN`: Minimum temperature
- `SNOW`: Snowfall
- `SNWD`: Snow depth

After exploring the data and analyzing missing values, the project focuses on precipitation and temperature-related features.

## Project Workflow

### 1. Data Loading and Exploration

- Load the dataset using Pandas.
- Set the date column as the DataFrame index.
- Explore data types, missing values, and descriptive statistics.
- Analyze weather patterns over time using visualizations.

### 2. Data Cleaning and Preprocessing

- Select relevant weather columns.
- Rename columns for better readability.
- Remove features with insufficient useful information.
- Handle missing precipitation values by replacing them with zero.
- Fill remaining missing values.
- Convert the index to datetime format.

### 3. Target Variable Creation

The target variable represents the maximum temperature of the following day.

This is created by shifting the maximum temperature column one day backward:

```python
core_weather['target'] = core_weather.shift(-1)['temp_max']
```

This allows the model to learn relationships between current weather conditions and the next day's maximum temperature.

### 4. Feature Engineering

Additional features are created to capture different weather patterns:

| Feature | Description |
|---|---|
| `precip` | Daily precipitation |
| `temp_max` | Current day's maximum temperature |
| `temp_min` | Current day's minimum temperature |
| `month_max` | Rolling 30-day average of maximum temperature |
| `month_day_max` | Ratio of the 30-day average to the current maximum temperature |
| `max_min` | Ratio between maximum and minimum temperatures |
| `monthly_avg` | Expanding average of maximum temperature grouped by calendar month |
| `day_of_year_avg` | Expanding average of maximum temperature grouped by day of year |

These engineered features aim to capture short-term trends as well as recurring seasonal patterns.

### 5. Model Training

The project uses **Ridge Regression**, a regularized linear regression algorithm.

The dataset is split chronologically:

- **Training set:** Data up to December 31, 2020.
- **Testing set:** Data from January 1, 2021, onwards.

A chronological split is used to evaluate the model on later observations rather than randomly mixing past and future data.

### 6. Model Evaluation

Model performance is evaluated using Mean Absolute Error (MAE):

MAE measures the average absolute difference between predicted and actual temperatures.

The project also compares actual and predicted temperatures visually and investigates observations with the largest prediction errors.

## Technologies and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Ridge Regression
- Time Series Feature Engineering

## Key Learnings

Through this project, I gained practical experience in:

- Working with time-indexed weather datasets.
- Data cleaning and missing-value handling.
- Creating lagged target variables.
- Feature Engineering using rolling and expanding averages.
- Understanding regularization through Ridge Regression.
- Training and evaluating Machine Learning models using chronological data splits.
- Analyzing model coefficients and prediction errors.

## Future Improvements

Potential next steps include:

- Experimenting with different regression algorithms.
- Optimizing Ridge Regression hyperparameters using time-series cross-validation.
- Comparing Rolling and Expanding features with different window sizes.
- Exploring additional weather-related features.
- Improving missing-value treatment.
- Comparing model performance using MAE, RMSE, and other evaluation metrics.

---------------------------------------------------------------
Learning Journey & Acknowledgements

This project was independently implemented as part of my hands-on journey into Machine Learning.

The project idea and learning materials were inspired by Dataquest, and I also used educational YouTube tutorials as additional learning resources to better understand the concepts and implementation.

While learning from these resources, I independently worked through the code, implemented the different steps, experimented with the features, and explored the model's predictions and performance.

I would like to acknowledge Dataquest and the educational content creators on YouTube for providing valuable learning resources and inspiration throughout this project.

This project represents an important step in my practical learning journey in Python, Data Analysis, and Machine Learning.

**Project Focus:** Time Series Forecasting | Regression | Feature Engineering | Machine Learning
