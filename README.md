# Medical_Payment_Classification
Identify whether a medical payment is for research purposes or for general use

### Identify Research Payment V.S. General Payment based on Medical Transaction features
The purpose of this analysis is to build a model to identify medical payment types <br>
This tesk is an aggregated workflow to build a ml process, more like in real cases <br>

The analysis including 3 parts <br>
#### 1. Understand features and select/create features
- drop features with too many missing value, taken into consideration as missing are not correlated to the final result
- winsorize / normalize variables, to avoid 
  - 1. curse of dimension when transforming categorical variable to lables 
  - 2. impact of outlier to the model, by transform the variable into normal distribution
- check data leakage, some of the feature have totally different value for Research payment v.s. General Payment. Understand how those 2 share similar features is critical to avoid data leakage

#### 2. Building model and train/select
- baseline model as tree and logistic regression to understand how features contribute to the result by looking at baseline model coefficients
- refine model by 
  - 1. grouping descriptions with regular expression to reduce dimension
  - 2. spliting some field that could be the combination of multiple dimensions
  - 3. try to find patterns in street/zip <br>
<b> select the model by <br>
  - 4. hyper parameter tuning with cross validation and random search
  - 5. ensemble (RF, Voting, XGBoosting)
    
#### 3. Findings
- amount of payment and location are the most important feature, especially if it is of higher amount and if in U.S. the probability for research funding is high
- also whether the payment is covered by insurance (covered by insurance indicate it is a general payment)
- what is payment method (cash indicate it is a general payment)
- what is the area of treatment, as the research fund is not similarly distributed as the general medical spend - for Oncology the payment is more likely to be research
- other reasons including devices, and code number for cases

#### 4. Result
- the predicted result 95% accuracy for testing set with runed tree, and 98 with XGB model
