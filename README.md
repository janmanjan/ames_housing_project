# Project 2 - Ames Housing Data and Kaggle Challenge

### Problem Statement
What are the 6 most important features in predicting housing price? What's important as a buyer?


### Background
The Ames Housing Dataset is a popular dataset on Kaggle that is famous for examining 80 different features of houses sold in Ames, Iowa. Many users have tackled the dataset in order to predict prices by selecting among the multitude of features. Given that the housing market is known to be both a lucrative and unstable way to gain capital; success in predictions is validation of skill and statistical learning.   

### Data that was analyzed
* [`train.csv`](./datasets/train.csv): DSIR-1129 Ames Competition ([source](https://www.kaggle.com/c/dsir-1129-prime/data))
* [`train_only_cleaned.csv`](./datasets/train_only_cleaned.csv): Data tranformations done from DSIR-1129 Ames Competition 


### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|gr_liv_area|int|train|Above grade (ground) living area square feet|
|age|int|train_only_cleaned|The amount of years passed from year built to date of observation|
|overall_qual|int|train|Rates the overall material and finish of the house|
|gr_liv_area/totrms_abvgrd|float|train_only_cleaned|Above grade (ground) living area square feet divided by the total rooms above grade (excluding bathrooms)|
|since_remod/add|int|train_only_cleaned|The amount of years from remodel date (same as construction date if no remodeling or additions)|
|garage area|float|train|Size of garage in square feet|
|kitchen_qual_order|int|train_only_cleaned|Kitchen quality ordered from poor to excellent|
|total_bsmt_sf|float|train|Total square feet of basement area|
|before_1940|int|train_only_cleaned|Whether the house was built before 1940|
|over_10|int|train_only_cleaned|Whether the house is over 10 years old|
|bsmtfin_sf_1|float|train|Type 1 finished square feet|
|fireplaces|int|train|Number of fireplaces|
|neighborhood|int|train|Physical locations within Ames city limits|
|saleprice|int|train|Sale price|


### Analysis, Conclusions, and Recommendations
All else held constant, the production model explains .93 of the variation of housing prices given the independent variables. The model is slightly overfit, however is within .01 of the r2 for test. The mae and rmse are 15433 and 21799 respectively. The relative closeness of the rmse to the mae suggest that despite a few outliers the model isn't heavily penalized. Moreover, the model also passes all the LINEM assumptions however if not for L1 regularization, the independent variables are prone to collinearity. In terms of the key independent variables: overall quality of the basement & living area, basement finish, general living area for the Northridge Heightt & kitchen quality as well as total basement square foot have the greatest effects on price. 

Upon further analysis, the production model without neighborhoods and regularization suggests that despite the importance of overall quality, general living area, basements, and squarefootage; the years since remodeling a house older than 10 years old have significant effects unaccounted for in the lasso model. What this means is that although the importance of general iving area and overall quality is unquestioned the variations are due to neighborhood preferences. Thus if a prospective buyer wishes to maximize price, understanding trends in particular neighborhoods are key.

The limitations to the model are the unused features that have may have corresponding interaction effects that improve r2. Another potential limitation would be how price inflation interacts with prices. Finally, the model neither accounts for external variables such as socio-political or economic factors nor market competition. It is important to note that these external factors may need to be tested against the model to ensure an actual affect on price. To ensure the generalizability and robustness of the model, more testing needs to be done with other locations. Finally, in order to better control the variability of the feature neighbors an experimentation of better ways to partition neighborhoods may lead to lower variance. 