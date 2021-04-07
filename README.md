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

<img src="https://i.ibb.co/MN37PFF/trello-cluster.png" alt="Reg-ppline" border="2">



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


## <a name="dictionary"></a>Data Dictionary  
[[Back to top](#top)]

---
|   Feature      |  Data Type   | Description    |
| :------------- | :----------: | -----------: |
|  parcelid | float64  | Unique parcel identifier    |
| heatingorsystemtypeid    | float64| Identifier for heating type|
| airconditioningtypeid  | float64 | Identifier for ac type|
| bathroomcnt | float64 |number of bathrooms in property|
|  bedroomcnt    | float64  | number of bedrooms in property   |
| calculatedfinishedsquarefeet   | float64 | total livable square footage|
| fips    | object| Federal Information Processing Code (county code)|
| latitude | float64 | geographic coordinate that specifies the north–south position|
|  longitude  | float64   | geographic coordinate that specifies the east-west position |
| poolcnt    | float64 | has pool = 1, no pool = 0|
| roomcnt   | float64 | count of rooms in property|
| yearbuilt   | float64 | year home was built |
|  fireplaceflag  | int64   | Has fireplace = 1, no fireplace = 0     |
| taxvaluedollarcnt   | float64 | The most recent year property taxes were assessed|
| taxamount   | float64 | ad valorem tax on the value of a property.|
| logerror  | float64 | age of home as of today's date in years|
| transactiondate     | datetime64[ns] | date property was last sold|
| airconditioningdesc   | object | description of AC type|
| heatingorsystemdesc  | object| description of Heating type|
|age_of_home  | float64   | Current date - Year Built in years    |
|  age_bin  | float64 | year home was built|
|  baths_per_sqft | float64 | numbers of baths per sqft|
|  taxrate   | float64 | This is property tax / tax_assessed_value |
|  acres   | float64   | lot square footage / 43,560     |
|  acres_bin   | float64 | properties binned into groups by acreage amounts|
|  sqft_bin | float64 | properties binned into groups by square footage amounts|
|  bath_bed_ratio  | float64 | bathroomcnt/bedroomcnt|
|   la_county   | uint8  | property in LA = 1, not in LA = 0|
|  orange_county  | uint8  | property in Orange = 1, not in Orange = 0|
| ventura_county  | uint8 | property in Ventura = 1, not in ventura = 0|
​
***
​
\* - Indicates the target feature in this Zillow data.
​
​
***
​

-------------------
  <h3><u>Hypothesis and Questions</u></h3>

- What is driving the errors in zestimates?
- Is Log Error related to counties?
- Is there correlation between log error and other features?
- Is there a relationship between the age of a home and the county it resides in?
- Is there a relationship between homes with amenities (pool or fireplace) and log error?


<h5> The questions above will be answered using t-tests and correlation tests.</h5>

--------------------
 <h3><u>How To Recreate This Project</u></h3>
 
 To recreate this project you will need use the following files:
 
 wrangle.py
 
 explore.py
 
 Your target variable will be tax_assessed_value which is defined in the above data dictionary. Please visit my final notebook to see this variable being used.
 
 <b>Step 1.</b> Import all necessary libraries to run functions. These can be found in each corresponding .py file
 
 <b>Step 2.</b> Use acquire.py to help pull data from your SQL database. You will need to have your own env.py file with your login information to be able to cpnnect and pull fomr your SQL program.
 
 <b>Step 3.</b> To see the the cleaned data set before training do the following:
 
```df = wrangle_zillow()``` 

After you have gotten to know the data set, run the following to gather the train, validate, test data

```X_train, y_train, X_validate, y_validate, X_test, y_test = seperate_y(train, validate, test)```
    
 
 <b>Step 4.</b> Verify that your data has been prepped using df.head()
 
 <b>Step 5.</b>. Enter the explore phase using the different univariate, bivariate, and multivariate functions from the explore.py file. This is also a great time to use different line plots, swarm plots, and bar charts. The associated libraries to make the charts happen are from matplotlib, seaborn, scipy, plotly and sklearn
 
 <b>Step 6.</b> Evaluate and model the data using different regression algorithms. 
         
* Linear Regression
* Lasso Lars
* Tweedie Regressor
* Polynomial Regressor (using a 2nd degree)
 
<b>Step 7.</b> After you have found a model that works, test that model against out of sample data using the function in my notebook.
 
 For a more detailed look, please visit my final notebook for zillow regression for further assistance.
 
--------------------

