# MVP
##### Sabrina Yang


## EDA:

The follwing data visualization charts show the relationship between

 - **target** :  _lifetime_gross_ 
 - **numberic features** : _rank_, _year_, _budget_, _runtime_minutes_.

### Heatmap:
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_heatmap.png" width = "450" height = "450">


  1.  Features with positive correaltion:  _year_, _budget_, _runtime_minutes_.
  2.  Features with negative correaltion: _rank_.
  3.  _budget_ is relatively higher respond (0.5) to our target, and followed by runtime_minutes_(0.078).
  4. _rank_ is defined by an ascending list based on _lifetime_gross_, so it makes sense that here shows the highly negavtive correlation. 

--------------------------------------------------------------------------------------------------------------------------------------------------------



### Pairplot:
<img src="https://github.com/SYNYC/2_Project_Movies/blob/main/charts/movies_num_pairplot.png" width = "600" height = "600">

  1. _lifetime_gross_ is a right-skewed distribution. 
  2. _lifetime_gross_ v.s. _rank_ : Top rank movies indicates more gross, so we can see the outstanding points are on the lift top corner, then the curves bend around after rank 100 or so and slowly comes down to the right bottom.
  3. _lifetime_gross_ v.s. _budget_ : a few outlier on budget that we might need to consider remove.
  4. _lifetime_gross_ v.s. _runtime_minutes_ : major movies runtime are between 90 to 150 minutes, but no 
  5. _lifetime_gross_ v.s. _year_ : most movies in our datasets are released after 2000.
  
Overall, no clear linear regression pattenrs on our current dataset so far so we will need to do some Features Engineering.








