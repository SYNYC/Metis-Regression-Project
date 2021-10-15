# Predicting Movie Box Office Gross by Linear Regression

Sabrina Yang


## Abstract

The purpose of the model I plan to build is to determine which movies will realize the highest lifetime domestic gross, and thus result in the highest return for movie futures. Our clients, movie futures investment firms, will benefit from this model by being able to predict which movies will have the high domestic gross and profit, and potentially invest in those movies futures to yield a high return. I worked with box office and movie profile data provided by [Box Office Mojo](https://www.boxofficemojo.com) and applied multiple tools/analyses including web scrapping packages, python packages, visual tools, and regression models and validations. After analyzing the data, I determined the key features of movies that would maximize domestic lifetime gross and yield the highest return for movie investment firms.



## Design
The project’s goal is to help movie investment firms determine which movies will result in a high lifetime domestic gross. Movies have many features that may impact their success including a budget, release date, cast and crews, and various others. As well, movies with a series can span many years and include multiple continuations and accumulated awareness, resulting in even further success for movies. In order to analyze these features, it is first prudent to choose the most transparent resource, which in this case was Box Office Mojo. First, web scrapping is critical to draw data effectively and efficiently. Once data is collected, the next step EDA involved applying pairplot and heatmap to draw insights from the data. Afterward, it involves using sklearn Linear Regression, Ridge, and Lasso Models to compare model evaluations based on the result of R-square and Mean Absolute Error.
  

## Data

The dataset is gathered from Box Office Mojo with 15 features in total, 4 of which are numerical and will be the focal points of this analysis. The time period of the data is the last 40 years, from 1980 until 2020. The reason for choosing this time frame was to prevent outliers, considering that the dollar value of budgets has changed significantly over time. Some of the features included in the analyses are lifetime gross, year, budget, and running time. The rest of the data features are categories, which includes ratings, genres, cast & crew, and distributors. Overall, I was selective on the features that were chosen and I did not include all features.



## Methodology
*Web Scrapping*

1. Used BeautifulSoup to gather data, starting from one page and using loops to collect data from additional pages

*Linear Regression Modeling*

2. 	Gross is relatively high so I converted data to Log to perform the following analyses
3.	I started with a pair plot and observed that there were outliers in movie year - Removed outliers by reducing time frame to 1980-2020, and took numerical data types of features to run the base line linear regression model
      a.	Result: r^2 score is 0.277
4.	I did the train test split on Simple Linear Regression
      a.	Result: r^2 score is 0.303
5.	Feature engineering
      a.	Result: r^2 score is 0.378
6.	I added category features including ratings, seasons, and distributor (one by one) but the r score did not improve – so I decided to create dummies and put it into one big data frame to compare the features fairly
7.	For this big data frame, I did the train test split and put it into the linear regression
      a.	Result: r^2 score is 0.33 (Te is 0.27 and is slightly overfit)
      b.	Result: rsme is 0.415
      c.	Result: mae is 0.328
8. 	Since the model is already slightly overfit, I wanted to add feature engineering but didn’t want to complicate the model so I chose to manually input budget and running time feature interactions instead of applying polynomial function
9.	RidgeCV to perform regularization on the existing model, after tuning alpha
      a.	Result: r^2 score is 0.315 (Te is 0.278 and is still overfit)
      b.	Result: rsme is 0.398
      c.	Result: mae is 0.327
10.	To compare RidgeCV, I did LassoCV to perform regularization on the same existing model, after tuning alpha
      a.	Result: r^2 score is 0.330 (Te is 0.28 and is still overfit, but is the least range I got)
      b.	Result: rsme is 0.396
      c.	Result: mae is 0.327


## Tools

Web Scrapping Packages: BeautifulSoup 
Python Packages: numpy, pandas
Visual Tools: pairplot, seaborn,  matplotlib
Regression Models & Validations: 
    •	Linear Regression
            o	import statsmodels.api as sm
            o	from sklearn.linear_model import LinearRegression, RidgeCV, LassoCV
            o	from sklearn.preprocessing import StandardScaler, PolynomialFeatures
    •	Train test split
            o	from sklearn.model_selection import train_test_split
    •	Cross Validations
            o	from sklearn.model_selection import cross_val_score


## Summary
The results showed that LassoCV was the best model based on my exploration of modeling selection given it brought the train and test scores closer than others. Overall, the score didn’t have a lot of volatile results between the different models. However, the LassoCV MAE showed that the predicting model has a 0.327 log units difference.



### OLS
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/ols.png" >

### Actual vs Predicted Gross
#### Ridge CV
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/ridge.png" >

#### Lasso CV
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/LassoCV_log.png" >

### Diagnostic_Plots
#### Ridge CV 
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/Diagnostic_Plots_Ridge.png" >

#### Lasso CV
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/Diagnostic_Plots_Laao.png" >





