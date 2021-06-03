# 2_Project_Movies

## Project Proposal


## Question & need:

The purpose of the model I plan to build is to determine which movies will yield the highest box office and profit, and thus result in the highest return for movie futures.   

Our clients, movie futures investment firms, will benefit from this model by being able to predict which movies will have the high domestic gross and profit, and potentially invest in those movies futures to yield the high return.


## Data Description:


There are multiple datasets I will be using from two main resources:
	
##### Resource  1 : Box Office Mojo 
   - [PG-13 movies for Top Lifetime Grosses by MPAA Rating(Domestic)](https://www.boxofficemojo.com/chart/mpaa_title_lifetime_gross/?by_mpaa=PG-13)
   		- Features: 
   					* Title 
   					* Rank
   					* Lifetime Gross
   					* Overall Rank
   					* Year

   - [Each movie profile page](https://www.boxofficemojo.com/title/tt2488496/?ref_=bo_cso_table_1)
   		- Features: 
   					* Cast & Crew 
   					* Budget _(Profit = Gross - Budget)_
   					* Gernes 
   					* Release Date 
   					* Runtime

##### Resource 2 :  IMDbPro

[STARmeter](https://pro.imdb.com/discover/people?profession=actor&sortOrder=STARMETER_ASC&ref_=nm_nv_ppl_tsm&pageNumber=1)

	  	-  A ranking system for actors, producers and directors etc



The individual unit of analysis would be each row of data as below: 


	link_stub	title	rank_pg13_movies	lifetime_gross	rank_overall	year	domestic_total_gross	budget	genres	runtime_minutes	rating	release_date
Star Wars: Episode VII - The Force Awakens	/title/tt2488496/?ref_=bo_cso_table_1	Star Wars: Episode VII - The Force Awakens	1	$936,662,225	1	2015	936662225	245000000	[Action, Adventure, Sci-Fi]	138.0	PG-13	2015-12-16
Avengers: Endgame	/title/tt4154796/?ref_=bo_cso_table_2	Avengers: Endgame	2	$858,373,000	2	2019	858373000	356000000	[Action, Adventure, Drama, Sci-Fi]	181.0	PG-13	2019-04-24
Avatar	/title/tt0499549/?ref_=bo_cso_table_3	Avatar	3	$760,507,625	3	2009	760507625	237000000	[Action, Adventure, Fantasy, Sci-Fi]	162.0	PG-13	2009-12-16


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

##### Regression models & Cross Validations
- Linear Regression
    * import statsmodels.api as sm
    * from sklearn.linear_model import LinearRegression, Ridge
    * from sklearn.preprocessing import StandardScaler, PolynomialFeatures
- train_test_split
	* from sklearn.model_selection import train_test_split
- Cross Validations
	* from sklearn.model_selection import cross_val_score


And I will use regression evaluation metrics such as MSE, RMSE, MAE, R-squared to test out models to avoid overfitting/underfitting. 


## MVP Goal:

✨A data visualization chart to help to identify the correlations between varaibles.✨
