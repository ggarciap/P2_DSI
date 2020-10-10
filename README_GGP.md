# Project 2 - Ames Housing Data and Kaggle Challenge

### Problem Statement

A construction and development company new to the Ames, IA area has recently received permission to begin construction of new residences. The company has asked for insight into which kind of characteristics and amenities a house should have in order for them to create a baseline house that guarantees that their investment is going to be maximized.


### Model developed

The dataset that we are working with has around 2051 observations  and 82 columns from which most of them contain categorical values (nominal or ordinal) that we want to analyze, because of this we want to use a model such as Lasso. This particular model will allow us to find feature importance within our model and allow us to determine which attributes are the ones that contribute the most when it comes to predicting the price of houses. 

Furthermore, it's important for this problem statement to be able to provide another  interpretable model that can give an indication of what numerical features might also contribute for the the prediction of price of houses 

In this model success will be evaluated by the R^2 score provided by the fitted model after performing cross-validation on the training dataset.

#### Data Cleaning and EDA

![alternativetext](images/initial_corr_numerical.png)

**Comment**: 

Decided to start my EDA process  by analyzing the correlations that exist for all the numerical values with the price, and from there choose the features that display the highest correlation. 


![alternativetext](images/missing_vals.png)

**Comment**: 

After selecting the most correlated features (Top5) it was important to look for missing values, which were present as shown in the graph. Althought there are not a high presence of them in the data set, it is important for the preprocessing steps later performed. 

![alternativetext](images/closer_corr_numerical.png)

![alternativetext](images/hist_numerical.png)

![alternativetext](images/pairplot_numerical.png)

**Comment**: 

Decided to check linearity and normality of the features that where selected to see if they follow in some degree the LINE assumptions of linear regression. 

### Model using numerical features for prediction of `SalesPrice`

**Comment**: 

A linear regression model was used for the prediction of `SalesPrice` using numerical features. The following table gives the results and interpretation of the beta coefficients. 

Interpretation of Coefficients:
Now as we consider multiple features, our interpreatation are holding all other variables constant. 
- For every 1 unit increase in `1st Flr SF`, we expect `SalePrice`  to increase by 13.921302344970547, holding all else constant
- For every 1 unit increase in `Full Bath`, we expect `SalePrice`  to increase by 4500.09606563663, holding all else constant
- For every 1 unit increase in `Garage Area`, we expect `SalePrice`  to increase by 58.83531628845373, holding all else constant
- For every 1 unit increase in `Gr Liv Area`, we expect `SalePrice`  to increase by 39.13412475280334, holding all else constant
- For every 1 unit increase in `Overall Qual`, we expect `SalePrice`  to increase by 25276.80036221399, holding all else constant
- For every 1 unit increase in `Total Bsmt SF`, we expect `SalePrice`  to increase by 14.699568507929111, holding all else constant

![alternativetext](images/betas_graph_numerical.png)

### Model using categorical features for prediction `SalesPrice`

For this particular model pre-processing step was done in order to select all the columns from the dataframe that contianed only objects that could be dummified, also any column that contain a nan was not considered.  

A Lasso model was used for the prediction of `SalesPrice` using numerical features. The following table gives the results and interpretation of the beta coefficients. 


![alternativetext](images/corr_categorical.png)

![alternativetext](images/barplot_categorical.png)

**Comment**: 

One of the main reasons for using lasso was beucase we can perfrom feature selection through the method of apply a regularization process where it penalizes the coefficients of the regression variables shrinking some of them to zero and in this way leaving the features that contirbute the most to the model for predicting `SalePrice`

### Comparison of score

![alternativetext](images/rmse_scores.png)


![alternativetext](images/r2_scores.png)


### Recommendations/Conclusion

In the case  of focus solely in numerical features we can rely on the features that contain high correlation such as  Overall Qua, Gr Liv Area, Garage Area, Total Bsmt SF, 1st Flr SF and Full Bath along with the coefficient given by the linear regression model to choose any of the those features as potential characteristics to focus on when building the baseline model for the house.
Furthermore, if we want  to focus in the categorical features we can rely in the feature selection done after performing a Lasso model on all the dummified features and choosing the top 10 features with highest beta coefficients, and in this way analyze the magnitude of importance that each attribute has for the lasso model. 
