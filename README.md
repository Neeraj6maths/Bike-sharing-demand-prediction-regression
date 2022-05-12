# Rented bikes demand prediction (Regression)


## Objective
This main objective of this project is to build a predictive model, which could predict the count of rental bikes required for each hour using the Seoul Bike Sharing dataset that contains information about bike count along with many environmental variables for each hour of each day from December 2017 to November 2018. 
## Dataset used
 The dataset contains information about bike count for each hour of each day along with following features.

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

### (6) Feature encoding
- Used One hot encoding to transform categorical feature - `Seasons`.
- Used Label encoding to transform categorical features - `Holiday`, `Functional Day`.

### (7) Handling skewness
- Used square root transformation to reduce skewness of skewed features.

### (8) Standardization of features
- Used `Z-score` for normalization of features.This step scales data into a uniform format that would utilize the data in a better way while performing fitting and applying different algorithms to it. 

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
- Number of bookings for rented bikes found to be high in evening as compared to morning.
- Demand for rented bikes found to be very low in winters and almost high in all other seasons.
- On holidays, demand of rented bikes found to be low as compared to demand on non holidays.
- Dew point temerature and temperature found to be highly correlated. 

### Feature Selection

Feature Selection is crucial step before model training as it improves the performance of model and also to reduce multicollinearity in dataset.
Since tree based algorithms are immune to multicollinearity that's why in this project feature selection is performed only before training `Linear', `Lasso`, `Ridge` and `Elastic Net` regression.

```

         Feature selection increases the predictive power of machine learning algorithms by selecting the most important variables 
         and eliminating redundant and irrelevant features. I removed all the multicollinear features from the dataset prior training 
         the model. For removing multicollinearity I used Vif and heatmap.
         
         (a) Correlation Matrix: 
                 (i)   Found that `Dew point temperature` and `temperature` are highly collinear.
                 
                 
          (b) VIF:  Variation Inflation Factor is another way of measuring multicollinearity. A high VIF indicates that the associated independent 
          variable is highly collinear with the other variables in the model.
                 (i) `Dew point temperature`, `Humidity` and `Visibility` found to have high Vif Values.
                 
                 
           Therefore, `Dew point temperature`, `Humidity` and `Visibility` were dropped.
```

### Features for model building

For `Decision Tree Regressor` and `Random Forest` we have not removed highly correlated features. Therefore features while training these algorithms are:

```
 - Hour
 - Temperature
 - Humidity
 - Wind speed 
 - Solar Radiation
 - Visibility
 - Rainfall
 - Dew point temperature
 - Snowfall 
 - month	
 - day_of_month	
 - Seasons_Autumn	
 - Seasons_Spring	
 - Seasons_Summer	
 - Seasons_Winter	
 - holiday_n	
 - fday_n

```

For `Linear', `Lasso`, `Ridge` and `Elastic Net` regression, we have used VIF and dropped some highly correlted features.  Therefore features while training these algorithms are:
```
 - Hour
 - Temperature
 - Wind speed 
 - Solar Radiation
 - Rainfall
 - Snowfall 
 - month	
 - day_of_month	
 - Seasons_Autumn	
 - Seasons_Spring	
 - Seasons_Summer	
 - Seasons_Winter	
 - holiday_n	
 - fday_n

```



## Model Building


Since we have to predict the count of rented bikes, so this is a regression problem. Based on the problem statement which is basically to predict the demand of rented bikes for each hour I decided to develop predictive models using following algorithms and haev compared ther performance.
```
- Decision Tree Regressor
- Random Forest
- Linear Regression
- Lasso
- Ridge
- Elastic Net


Following necessary steps have been employed for better model performance.
                (i)   train test split for model evaluation.
                (ii)  Hyperparameter tuning for best learning parameters that developed a better model. Hyperparameter tuning was done with the help
                      of GridSearchCV.
                      
                      
                  
```


### Evaluation metrics

To evaluate the models I have used MSE( Mean Square error) and R2-Score.


## Conclusion

```
                 (i)   Random forest performed best as compared to other models with
                         R2-Score for test dataset = 0.812
                         MSE for test dataset      = 78132.54
                 (ii)  Linear Regression is the least accurate as compared to other models performed.
                         R2-Score for test dataset = 0.3660
                         MSE for test dataset      = 193993.06
           

```
## Challenges
```

                (i) Hyperparameter tuning using GridSearchCV was ver time consuming.
                (ii) Feature selection was tedious due to high multicollinearity.

```

