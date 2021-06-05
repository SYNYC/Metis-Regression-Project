# Project 2 Movies   
# Project Proposal


## Question & need:

### Given movies that are being made, which movies should I invest in?

The purpose of the model I plan to build is to determine which movies will realize the highest lifetime domestic gross, and thus result in the highest return for movie futures.   

Our clients, movie futures investment firms, will benefit from this model by being able to predict which movies will have the high domestic gross and profit, and potentially invest in those movies futures to yield a high return.


## Data Description:


There are multiple datasets I will be using from two main resources:

#### Resource  1 : Box Office Mojo
   - [Top Lifetime Grosses by MPAA Rating(Domestic)](https://www.boxofficemojo.com/chart/top_lifetime_gross/?ref_=bo_cso_ac)
   		- Features:
   					* Title
   					* Rank
   					* Lifetime Gross
   					* Year

   - [Each movie profile page](https://www.boxofficemojo.com/title/tt2488496/?ref_=bo_cso_table_1)
   		- Features:
   					
   					* Distributor
   					* Budget       
   					* Release Date
   					* MPAA Rating
   					* Runtime
   					* Genres
                                        * Cast & Crew
                                        * Domestic Opening Gross
                                       



#### Resource 2 :  IMDbPro

   - [STARmeter](https://pro.imdb.com/discover/people?profession=actor&sortOrder=STARMETER_ASC&ref_=nm_nv_ppl_tsm&pageNumber=1) : A reference from this ranking system for actors, producers and directors etc



The individual unit of analysis would be each row of data as below:


<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/df%20head.png">




**Data columns  (total 12 columns):**
  Index |  Column |   Dtype
-|---------- | ----------
 0 |  link_stub  |  object
 1  | title    |object
 2  | rank_pg13_movies  |object
 3  | lifetime_gross |  object
 4  | rank_overall | object
 5  | year  | object
 6  | domestic_total_gross  |object
 7  | budget |    object
 8  | genres    |  object
 9  | runtime_minutes  | float64
 10 | rating     | object
 11 | release_date  | datetime64[ns]


##### The target of the modeling will be Domestic Total Gross (=Lifetime Gross}.


## Tools:
##### Web scrapping packages
- BeautifulSoup
    * from bs4 import BeautifulSoup
    * import requests
- Selenium
	* import time, os
	* from selenium import webdriver
	* from selenium.webdriver.common.keys import Keys

##### Python packages
- numpy
	* import numpy as np
- pandas
    * import pandas as pd
    * clean and merge different datasets

##### Visual tools
- pairplot
    * import matplotlib.pyplot as plt
    * %matplotlib inline
- heatmap
    * import seaborn as sns

##### Regression models & Validations
- Linear Regression
    * import statsmodels.api as sm
    * from sklearn.linear_model import LinearRegression, Ridge
    * from sklearn.preprocessing import StandardScaler, PolynomialFeatures
- Train test split
	* from sklearn.model_selection import train_test_split
- Cross Validations
	* from sklearn.model_selection import cross_val_score


I will use regression evaluation metrics such as MSE, RMSE, MAE, R-squared to test out models, also using validation framework for model selections to avoid overfitting/underfitting.


## MVP Goal:

🎬 A data visualization chart to help to identify the correlations between variables.🎬
