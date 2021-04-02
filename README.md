# Zillow Clustering-Project

------------

<h3> <a name="top"></a> Hi there 👋,</h3>

Welcome to the README file for the Zillow Clustering Project.

In here, you will find expanded information on this project including goals, how we will be working through the pipeline and a data dictionary to help offer more insight to the variables that are being used.

------------
![couple looking at house](https://www.zillowstatic.com/s3/homepage/static/Buy_a_home.png)
​
***
[[Project Description](#project_description)]
[[Project Planning](#planning)]
[[Key Findings](#findings)]
[[Data Dictionary](#dictionary)]
[[Data Acquire and Prep](#wrangle)]
[[Data Exploration](#explore)]
[[Statistical Analysis](#stats)]
[[Modeling](#model)]
[[Conclusion](#conclusion)]
___
​
​

------
## <a name="project_description"></a>Project Description:


This project is utilizing data from the Codeup SQL server featuring 2017 property data from Zillow. Our goal is to identify the drivers of log error in Zillow's zestimate. We are using unsupervised clustering to help narrow down the features driving the error and then utilizing linear regression to see if we can create a more accurate model.


<u>Data Source</u>
* This data is being pulled from the Codeup SQL database under the name 'Zillow'
    * For this project, I am utilizing the 2017 properties, predictions and all other associated tables available
* The data can also be pulled from Kaggle.com 
    * https://www.kaggle.com/c/zillow-prize-1/data
* This repository also has a CSV of the data available as well


[[Back to top](#top)]
​

------------
## Goals
​
The goals of the project are to answer the questions and deliver the following:
​
- Use clustering to identify what groups of features are the strongest drivers of log error
- Deliver a final notebook that shows the key drivers behind log error
- Give a succinct 5 min presenation that covers the exploration, modeling, & takeaways 
​
***
## <a name="planning"></a>Project Planning: 

- We have two places where you can view our project planning. One is our Trello board, which can be found at this link and you can also see a snippet in the image below. 

- The other place where you can view our initial project planning stage is in the project_plan.md file here in our git hub. That too is kept up to date and progress is marked using the following:

- ✅    to mark a completed item
- 💻    to mark an in-progress item
- 🚨    to mark a late item (more than one day)


A link to the Trello board below can be found at https://trello.com/b/VRlIpoeo/zillow-cluster-project


Here is a snapshot of our project planning/setup on the evening of 4/1/21

<img src="https://i.ibb.co/MN37PFF/trello-cluster.png" alt="Reg-ppline" border="0">



[[Back to top](#top)]
​

----------
### Projet Outline:
- Acquisiton of data through Codeup SQL Server, using env.py file with username, password, and host
- Prepare and clean data with python - Jupyter Labs Notebook
- Explore data
    - if value are what the dictionary says they are
    - null values
        - are the fixable or should they just be deleted
    - categorical or continuous values
    - Make graphs that show 
- Run statistical analysis
- Model data 
- Test Data
- Conclude results
 
----------- 
### Hypothesis
- Input hypothesis of entire project (anticipated outcomes, models, statistics, etc)
​
### Target variable
- What are you trying to predict or analyze
​
### Need to haves:
- Requirements for completing report
​
### Nice to haves:
- If you have time, what will you include.
​
***
​
## <a name="findings"></a>Key Findings:
[[Back to top](#top)]
​
### Explore:
- What are your key findings from explore?
​
​
### Stats
- What are your key findings from stats?
​
### Modeling:
- Model results?
​
​
***
​
## <a name="dictionary"></a>Data Dictionary  
[[Back to top](#top)]
​
### Data Used
---
|   Feature      |  Data Type   | Description    |
| :------------- | :----------: | -----------: |
|  parcelid | int64   | Unique parcel identifier    |
| landuse_id     | float64 | Identifier for landuse type|
| landuse_desc   | object | Describes the type of landuse|
| last_sold_date  | object |transaction date of when property last sold|
|  total_sqft  | float64   | Total livable square footage    |
| bedroom_quanity    | float64 | count of bedrooms|
| bathroom_quanity   | float64 | count of bathrooms|
| fips  | object | Federal Information Processing Code (county code)|
|  zip_code | object   | 5 digit code used by US Postal Service    |
| year_built    | object | year home was built|
| tax_assesed_value   | float64 | total value of home established by taxing authority|
| latitude  | float64 | geographic coordinate that specifies the north–south position |
|  longitude  | float64   | geographic coordinate that specifies the east-west position     |
| tax_assess_yr    | float64 | The most recent year property taxes were assessed|
| property_tax   | float64 | ad valorem tax on the value of a property.|
| age_of_home  | int64 | age of home as of today's date in years|
| tax_rate    | float64 | This is property tax / tax_assessed_value|
| baths_pers_qft   | float64 | numbers of baths per sqft|
| beds_pers_qft  | float64| number of beds per sqft|
​
***
​
\* - Indicates the target feature in this Zillow data.
​
​
***
​
## <a name="wrangle"></a>Data Acquisition and Preparation
[[Back to top](#top)]
​
### Acquisition and Preparation
- Did you use a wrangle?  acquire and prepare files?
- 
​
| Function Name | Purpose |
| ----- | ----- |
| acquire_functions | DOCSTRING | 
| prepare_functions | DOCSTRING | 
| wrangle_functions() | DOCSTRING |
​
***
​
## <a name="explore"></a>Data Exploration:
[[Back to top](#top)]
- wrangle.py 
​
| Function Name | Definition |
| ------------ | ------------- |
| select_kbest | This function takes in a dataframe, the target feature as a string, and an interger (k) that must be less than or equal to the number of features and returns the (k) best features |
| rfe | This function takes in a dataframe, the target feature as a string, and an interger (k) that must be less than or equal to the number of features and returns the best features by making a model, removing the weakest feature, then, making a new model, and removing the weakest feature, and so on. |
| train_validate_test_split | This function takes in a dataframe, the target feature as a string, and a seed interger and returns split data: train, validate, test, X_train, y_train, X_validate, y_validate, X_test, y_test |
| get_object_cols() | This function takes in a dataframe and identifies the columns that are object types and returns a list of those column names |
| get_numeric_cols(X_train, object_cols) | This function takes in a dataframe and list of object column names and returns a list of all other columns names, the non-objects. |
| min_max_scale(X_train, X_validate, X_test, numeric_cols) | This function takes in 3 dataframes with the same columns, a list of numeric column names (because the scaler can only work with numeric columns), and fits a min-max scaler to the first dataframe and transforms all 3 dataframes using that scaler. It returns 3 dataframes with the same column names and scaled values. 
​
​
### Function1 used:
- Outcome of the use of the function 
​
### Function2 used:
- Outcome of the use of the function 
​
***
​
## <a name="stats"></a>Statistical Analysis
[[Back to top](#top)]
​
### Stats Test 1:
 - What is the test?
 - Why use this test?
 - What is being compared?
​
#### Hypothesis:
- The null hypothesis (H<sub>0</sub>) is... 
- The alternate hypothesis (H<sub>1</sub>) is ...
​
​
#### Confidence level and alpha value:
- I established a 95% confidence level
- alpha = 1 - confidence, therefore alpha is 0.05
​
#### Results:
 - Results of statistical tests
​
 - Summary:
     - In depth take-a-ways from the results
​
### Stats Test 2 
 - What is the test?
 - Why use this test?
 - What is being compared?
​
#### Hypothesis:
- The null hypothesis (H<sub>0</sub>) is... 
- The alternate hypothesis (H<sub>1</sub>) is ...
​
​
#### Confidence level and alpha value:
- I established a 95% confidence level
- alpha = 1 - confidence, therefore alpha is 0.05
​
#### Results:
 - Results of statistical tests
​
 - Summary:
     - In depth take-a-ways from the results
​
### Stats Test 3
 - What is the test?
 - Why use this test?
 - What is being compared?
​
#### Hypothesis:
- The null hypothesis (H<sub>0</sub>) is... 
- The alternate hypothesis (H<sub>1</sub>) is ...
​
​
#### Confidence level and alpha value:
- I established a 95% confidence level
- alpha = 1 - confidence, therefore alpha is 0.05
​
#### Results:
 - Results of statistical tests
​
 - Summary:
     - In depth take-a-ways from the results
​
***
​
## <a name="model"></a>Modeling:
[[Back to top](#top)]
​
Summary of modeling choices...
​
### Baseline
​
​
- What is the first step?
    
```json
{
Input code here if you want...
}
```
- Next Step:
​
```json
{
Code...
}
```
​
- Baseline Results: 
    - What are the numbers we are trying to beat with our model.
        
***
​
### Models and R<sup>2</sup> Values:
- Will run the following models:
    - Model 1
        - brief summary of what the model does.
    - Model 2 
        - brief summary of what the model does.
    - etc.
​
- Other indicators of model performance with breif defiition and why it's important:
    - R<sup>2</sup> Value is the coefficient of determination, pronounced "R squared", is the proportion of the variance in the dependent variable that is predictable from the independent variable. 
    - Essentially it is a statistical measure of how close the data are to the fitted regression line.
#### Model 1:
​
```json 
{
Model 1 code:
}
```
- Model 1 results:
    - Metric for Model 1:
        - Training/In-Sample:  **Results**
        - Validation/Out-of-Sample:  **Results**
    - Other metrics: (R<sup>2</sup> Value = )
​
​
### Model 2 :
​
```json 
{
Model 2 code:
}
```
- Model 2 results:
    - Metric for Model 1:
        - Training/In-Sample:  **Results**
        - Validation/Out-of-Sample:  **Results**
    - Other metrics: (R<sup>2</sup> Value = )
​
​
### Eetc:
​
## Selecting the Best Model:
​
### Use Table below as a template for all Modeling results for easy comparison:
​
| Model | Training/In Sample RMSE | Validation/Out of Sample RMSE | R<sup>2</sup> Value |
| ---- | ----| ---- | ---- |
| Baseline | 271194.48 | 272149.78 | -2.1456 x 10<sup>-5</sup> |
| Linear Regression | 217503.9051 | 220468.9564 | 0.3437 |
| Tweedie Regressor (GLM) | 217516.6069 | 220563.6468 | 0.3432 |
| Lasso Lars | 217521.8752 | 220536.3882 | 0.3433 |
| Polynomial Regression | 211227.5585 | 214109.6968 | 0.3810 |
​
- Why did you choose this model?
- 
​
## Testing the Model
```json
{
Model Testing Code...
}
```
- Model Testing Results
     - Out-of-Sample Performance:  **Results**
​
​
***
​
## <a name="conclusion"></a>Conclusion:
[[Back to top](#top)]
​
Reiterate explore findings, statistical analysis, and modeling take-a-ways
​
What could be done to improve the model?
What would you do with more time? 
​
Anything else of note worth adding? Add it here.
