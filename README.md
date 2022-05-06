# Rented bikes demand prediction (Regression)


## Objective
We are provided with the Seoul Bike Sharing dataset that contains information about bike count along with many environmental variables for each hour of each day from December 2017 to November 2018. 
The main objective is to build a predictive model, which could predict the count of rental bikes required for each hour.
## Dataset
We are given a Seoul Bike Sharing dataset. This dataset contains information about bike count for each hour of each day along with following features.

```
- Date : year-month-day
- Hour : Hour of the day (24hr fomat)
- Temperature : Temperature in Celsius
- Humidity : Percentage of humidity
- Windspeed : windspeed in m/s
- Visibility : visibility of 10m
- Dew point temperature : In Celsius
- Solar radiation : In units of MJ/m2
- Rainfall : Amount of rainfall for each day in units of mm
- Snowfall : Amount of snowfall for each day in units of cm
- Seasons : Winter, Spring, Summer, Autumn
- Holiday : Holiday/No holiday
- Functional Day : Yes/No
- Rented Bike count : Count of bikes rented at each hour (Dependent variable)

```

- Total number of rows in data : 8760
- Total number of columns : 14
## Data Cleaning and Feature Engineering

### (1) Removing Duplicate rows
- No duplicate rows were present in dataset.

### (2) Handling null values
- No null values were present in dataset.  

### (3) Converting columns to appropriate data types

- Changed datatype of `Date` to date type. 

### (5) Creating new columns
- Created new column `month` from `date` column.
- Created new column `day of month` from `date` column.

## Exploratory Data Analysis

Mainly performed using Matplotlib and Seaborn library and the following graph and plots had been used:
  - Bar Plot.
  - Histogram.
  - Scatter Plot.
  - Pie Chart.
  - Line Plot.
  - Heatmap.
  - Box Plot
             


- Variables like `Rented Bike Count`,`Snowfall`,`Windspeed`,`Solar Radiation` and `Rainfall` were positively skewed.
- `visibility` variable was negatively skewed.
- There was high demand for rental bikes in months of May, June and July.
- Number of bookings for rented bikes is high in evening as compared to morning.
- Demand for rented bikes is very low in winters and almost high in all other seasons.
- On holidays, demand of rented bikes is low as compared to demand on non holidays.
- Dew point temerature and temperature are highly correlated. 

## Applying ML models

Since we have to predict the count of rented bikes, so this is a regression problem.

We have used following ML regression models and have compared there performance.
- Decision Tree Regressor
- Random Forest
- Linear Regression
- Lasso
- Ridge
- Elastic Net
-
## Conclusion

```


And many more conclusions.
```
## Challenges
```


```

