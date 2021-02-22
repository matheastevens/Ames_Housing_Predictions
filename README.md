# Ames Housing Predictions

The Ames Assessor’s Office released a data set of assessed values for individual residential properties sold in Ames, Iowa from 2006 to 2010. The data set contains 

### Problem Statement
Develop a model to predict, to the highest degree accuracy available, housing prices in Ames Iowa. 

### Methodology

To create a predictive model, we begin with a thorough investigation of the data provided. There data set contained extensive information of housing features. The data types could be broken down into three disctinct types: *nominal, ordinal, and numeric*. The image to the right breaks down the variables accordingly ([*image courtesy of NYC Data Science Academy*](https://nycdatascience.com/blog/student-works/studying-regression-model-efficacy-on-the-ames-housing-data-set/)). 

<img src = 'https://nycdsa-blog-files.s3.us-east-2.amazonaws.com/2019/09/ML_project_variables-1-1024x576.png' style="width: 200px; float: right;">

Each of these housing features will have to be transformed in different ways in order to be able to create a model. 

The numeric variables, like number of bedrooms and above grade square feet are great indicators for our model, however, variables like MS Subclass (how the municipaility classifies the house) is still a categorical variable. The Ordinal variables were treated as a ranking scale, with the highest qualities being a 5 and the lowest a 1. The Nominal variables, on the other hand, had to ranking to the various categories, and thus were broken down into 1's and 0's. 

#### Feature Engineering

In order to improve our model's performance, a few outliers were removed from the training dataset. Removing the 4 data points below improved model performance. 

<img src="/Images and Backup/outliers.png"/>

New features were also created with stronger correlations with sale price, which ensured their datapoints could be captured in the model. 

|Feature|Interaction Type|Pearson Correlation|
|---|---|---|
|Age Since Built|*Year Built subtracted from Year Sold*|-0.57 | 
|Age Since Renovated|*Year Renovated subtracted from Year Sold*| -0.55| 
|Total Living Squarefoot Quality|*Living Square Footage multiplied by overall Quality of Finishes*| 0.90| 
|Garage Quality Square Footage|*Garage Square feet multiplied by Overall Quality of Finishes*|0.66 | 
|Patio Quality|*All outdoor patio types added together*|0.41 | 

From this, we selected features with a correlation above 0.45 and below -0.45, and to bring down the dimentionality of the dataset, we used a built-in scaler (*Scikit learn Standard Scaler*), and took the natural log of the sale prices. With regards to the sale price, taking the natural log not only brings down the sale price data by an order of magnitude but helps to normalize the distribution of sales price, as seen in the graphs below. While there is still a skew, it is much more normal than the original sale price distribution. 

<img src = "/Images and Backup/sale_price_distribution.png"  style="width: 250px; float: left;"/>


Several models were tested to identify which performed best on the training data. 

<img src="/Images and Backup/model_perf_graph.png" alt="drawing" style="width: 250px; float: left;"/>

Unsurprisingly, the Random Forest and AdaBoost models were very overfit, however their results in the Kaggle competition were competitive with the other models, as outlined below. 

|Model|Kaggle Score|
|---|---|
|SVM|24,324|
|Ridge Linear Regression|24,334| 
|Lasso Linear Regression|24,444| 
|Ada Boost|29,109| 
|Random Forest|29,301| 
|KNN|33,325| 

## Feature Importance

The model presented can, with 90% confidence, predict the sale price for housing in Ames. 
Key features include:
 - Overall quality
 - Kitchen quality
 - Total liveable square feet squality indicator
 - Whether a house has a concerete foundation
 - Neighborhood

While this list is not exhaustive, it is no surprices that these items are the top of the list: house prices are often a reflection of the quality of materials used, the quality of the kitchen, square footage, foundation and neighborhood. What this model tell us over and above common-sense pricing, however, is whether a listing over or under priced. 

Through also examining other factors, like garage type, age, fireplace quality, masonry and unfinished basement square footage, the model empowers home buyers in Ames to identify opportunities for under-valued homes or flag homes which are over-priced for the features present. Of coruse there will always be room for negotiation in home sales, however, the models explored in this project can help provide another quanitative measure in the process of home buying or selling. 

## Data Dictionary 
A complete data dictionary is available [here](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data).
