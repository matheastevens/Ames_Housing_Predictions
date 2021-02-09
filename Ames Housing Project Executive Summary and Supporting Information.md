# Ames Housing Predictions

The Ames Assessor’s Office released a data set of assessed values for individual residential properties sold in Ames, Iowa from 2006 to 2010. The data set contains 

### Problem Statement
Develop a model to predict, to the highest degree accuracy available, housing prices in Ames Iowa. 

### Methodology

To create a predictive model, we begin with a thorough investigation of the data provided. There data set contained extensive information of housing features. The data types could be broken down into three disctinct types: *nominal, ordinal, and numeric*. The image to the right breaks down the variables accordingly ([*image courtesy of NYC Data Science Academy*](https://nycdatascience.com/blog/student-works/studying-regression-model-efficacy-on-the-ames-housing-data-set/)). 

<img src = 'https://nycdsa-blog-files.s3.us-east-2.amazonaws.com/2019/09/ML_project_variables-1-1024x576.png' style="width: 500px; float: right;">

Each of these housing features will have to be transformed in different ways in order to be able to create a model. 

The numeric variables, like number of bedrooms and above grade square feet are great indicators for our model, however, variables like MS Subclass (how the municipaility classifies the house) is still a categorical variable. The Ordinal variables were treated as a ranking scale, with the highest qualities being a 5 and the lowest a 1. The Nominal variables, on the other hand, had to ranking to the various categories, and thus were broken down into 1's and 0's. 

Additional feature engineering created features with a higher correlation to the target, allowing for higher accuracy from the final predictions. 

Several models were tested to identify which performed best on the training data. 


### Conculsions and Recommendations

The model presented can, with 90% confidence, predict the sale price for housing in Ames. 
Key features include:
 - Overall quality
 - Kitchen quality
 - Total liveable square feet squality indicator
 - Whether a house has a concerete foundation
 - Neighborhood

While this list is not exhaustive, it is no surprices that these items re the top of the list: house prices are often a reflection of the quality of materials used, the quality of the kitchen, square footage, foundation and neighborhood. What this model tell us over and above common-sense pricing, however, is whether a listing over or under priced. 

Through also examining other factors, like garage type, age, fireplace quality, masonry and unfinished basement square footage, the model empowers home buyers in Ames to identify opportunities for under-valued homes or flag homes which are over-prices for the features present. 

The model is capable of predicting a house sale price within an 87 - 90% accuracy. Next steps would include exploring additional feature engineering to increase the model's generalization for future sales prices. 


## Data Dictionary 
A complete data dictionary is available [here](https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data).
