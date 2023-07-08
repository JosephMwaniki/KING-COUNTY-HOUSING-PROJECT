# KING-COUNTY-HOUSING-PROJECT

## Overview
A real estate firm has contacted us for advice on how to fairly value homes in King County so that they may offer their clients fair recommendations when it comes to buying and selling homes. A data file containing various details about the various homes in King County has been provided to us. We want to be able to break down the aspects that eventually increase the value of their homes.
## Business Understanding
We'll be looking to answer the following questions to help us better understand the layout of the housing industry.

* How does number of bathrooms/bedrooms effect the price?
* How much does square footage matter?
* Are there any other features that effect the price significantly?

## Data Understanding

King County House Data: a dataset that we were provided at the onset of the project. This file contains data for 21,597 homes built in King County from 1900 to 2015. Each home in the set contains information regarding features such as number of bedrooms/bathrooms, number of floors, square footage, zip code, condition, and more.  

# First Model
![image] (Visualisations/correlation.png)
The heatmap shows that sqft_living is the most correlated feature, so that will be our baseline model. 0.48733518973535617 for the train The validity score is 0.4945445156766466.
We ran linear regression on our baseline model, and the r-squared value was.49. We will work hard to improve our model.

# Second Model
we started by checking linearity between price and independent variables.
![image] (Visualisations/RELATIONSHIP.png)
From the above graphs, we can see that the following independent variables have a linear relationship to listing price:

* sqft_living15
* grade
* sqft_above
* sqft_living
* bathrooms

# Third Model
We check for collinearity between independent variabels
![image] (Visualisations/corr.png)

![image] (Visualisations/ols1.png)

Upon analyzing our data, we have observed significant collinearity among certain variables. To address this, we need to drop one variable from each pair to avoid redundancy. After considering our options, we decided to retain the variables grade, bathrooms, sqft_living15, bedrooms, and sqft_basement by dropping sqft_living and sqft_above.

However, during the initial collinearity check, outliers were included in the dataset. Upon reintroducing the columns we initially planned to remove and removing outliers, we obtained different results.

Now, the only collinear factors we found are sqft_living and sqft_above. Consequently, we can remove sqft_above, allowing us to retain more columns in our dataset compared to before removing outliers. With these adjustments, we can proceed with modeling the data again to see the updated outcomes.

Upon examining the coefficients from this new model, we observe that, on average, each square foot increase in a home's size contributes to a $114 increase in the sale price. Additionally, a one-unit increase in the size of the surrounding homes (sqft_living15) corresponds to a $50 increase in the sale price. Improving the grade of a property is associated with a substantial $90,000 increase in the sale price.

However, it's important to note that the grade is essentially a categorical variable rather than a numerical one. Therefore, while we can ascertain a strong correlation between grade and price, we cannot assign a specific numerical value to it.

Interestingly, bathrooms exhibit a negative correlation. One possible explanation is that our model, taking into account the square footage, is attempting to determine the impact of bathrooms on price in the context of larger homes. In such cases, it is possible that very large and expensive homes do not command higher prices solely based on the number of bathrooms they possess.

## Checking For Assumptions
Investigating Normality
![image] (Visualisations/normality.png)

Regression Plots
![image] (Visualisations/regression plots.png)
![image] (Visualisations/regression plots 2.png)
![image] (Visualisations/regression plots 3.png)

## Final Model

![image] (Visualisations/compilation.png)

This is how we anticipate our final model will perform.  To satisfy the linear regression assumptions, we made these changes to the final model. According to the graphs above, the four independent variables are homoscedastic, which means that the variance does not increase as the independent variable increases or decreases. We also know from the correlation graph that these aren't collinear. 

# Conclusion

Based on our analysis of King County data, we have determined that the key factors contributing to an increase in property value are the square footage of the property and its grade. Grade refers to the classification based on the construction quality of a structure, which encompasses the materials used and the quality of workmanship. Properties with higher grades tend to have higher values, despite the higher cost of construction per unit of measurement. 

However, our final model has its limitations. The R^2 value of our model was 48%, indicating that only 48% of the variance in property value could be explained by the factors included. Additionally, the root mean square error (RMSE) of $194,053 suggests that our model's predictions deviate from the actual property values by an average of $194,053. 

It is evident that linear regression may not have been the most suitable tool for extracting the maximum accuracy from this dataset. In future iterations, we intend to explore more powerful machine learning techniques to improve the predictive capabilities of our model and achieve a higher level of accuracy.








