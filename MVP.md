# MVP
##### Sabrina Yang


## EDA:

The follwing data visualization charts show the relationship between

 - **target** :  _lifetime_gross_ 
 - **numberic features** : _rank_, _year_, _budget_, _runtime_minutes_.

### Heatmap
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_heatmap.png" width = "450" height = "450">


  1.  Features with positive correaltion:  _year_, _budget_, _runtime_minutes_.
  2.  Features with negative correaltion: _rank_.
  3.  _budget_ is relatively higher respond (0.5) to our target, and followed by runtime_minutes_(0.078).
  4. _rank_ is defined by an ascending list based on _lifetime_gross_, so it makes sense that here shows the highly negavtive correlation. 

--------------------------------------------------------------------------------------------------------------------------------------------------------


### Pairplot
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_pairplot.png" width = "600" height = "600">

 _lifetime_gross_ (y) is a right-skewed distribution. The following are each features ploting obversations with y:
 
  1. _rank_ : 
  					Top rank movies indicates more gross, so we can see the outstanding points are on the lift top corner, then the curves bend around after rank 100 or so and slowly comes down to the right bottom.

  2. _budget_ : 
  					a few outlier on budget that we might need to consider to remove.

  3. _runtime_minutes_ : 
  					major movies runtime are between 90 to 150 minutes
  					
  4. _year_ : 
  					most movies in our datasets are released after 2000.
  
--------------------------------------------------------------------------------------------------------------------------------------------------------
## Modeling:

### Linear Regression
 
 1. joinplot : a plot of actual vs. predicted values
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_jointplot.png">
  
 2. OLS summary table: 
   
 <img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_ols.png">
 
 3. coef matrix : [-2.02806949e+05 -4.89324741e+04  2.58974262e-01  4.24933926e+05]
 4. * rmse: 59480872.89841622
    * mae:  38341358.58492877
    
 5. Train/ Validation/ Test result: Linear Regression test R^2: **0.652**
 

 
### Next step: Features Engineering 
Overall, we will need to do some Features Engineering to help building the model.

  1. adding polynomial terms:   
 
                           df['budget'] ** 2
                           
  2. Transform log on _lifetime_gross_ to adjust its right-skewed distribution: 
  
                           np.log(df["lifetime_gross"])
     
      <img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/transform_log_liftimegross.png">
      
  3. adding interaction terms : 
 
                           df['budget'] / df['runtime_minutes']
                           
   4. add catergorial dummies: 


                            a .ratings
                            b. genres
    










