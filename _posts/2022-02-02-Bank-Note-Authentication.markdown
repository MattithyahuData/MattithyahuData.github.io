---
layout: post
title:  "Project: 💵 Bank Note Authentication"
date:   2022-02-02 16:30:58 +0100
categories: jekyll update
---
# Project Overview 
* End to end project classifying real and fake bank notes.
* Apache Spark Python API used for speed benefits. 

## Table of Contents 
*   [Resources](#resources)<br>
*   [Data Collection](#DataCollection)<br>
*   [Data Pre-processing](#DataPre-processing)<br>
*   [Data Warehousing](#DataWarehousing)<br>
*   [Exploratory data analysis](#EDA)<br>
*   [Feature Engineering](#FeatEng)<br>
*   [ML/DL Model Building](#ModelBuild)<br>
*   [Model performance](#ModelPerf)<br>
*   [Model Evaluation](#ModelEval)<br>
*   [Project Management (Agile/Scrum/Kanban)](#Prjmanage)<br>
*   [Project Evaluation](#PrjEval)<br>
*   [Looking Ahead](#Lookahead)<br>
*   [Questions & Contact me](#Lookahead)<br>

<a name="resources"></a>  

## Resources Used
**PySpark, Python 3, PostgreSQL** 

[**Anaconda Packages:**](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/requirements.txt) **pandas numpy sklearn matplotlib seaborn sqlalchemy kaggle psycopg2 ipykernel pyspark** <br><br>
Powershell command for installing anaconda packages used for this project  
```powershell
pip install pandas numpy sklearn matplotlib seaborn sqlalchemy kaggle psycopg2 ipykernel pyspark 
```
<br><br>
Initiating spark session 
```python
# Creating spark session 
spark = SparkSession.builder.appName('P10').getOrCreate()
```

<a name="DataCollection"></a>  

## [Data Collection](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)
Powershell command for data import using kaggle API <br>
```powershell
!kaggle datasets download -d ritesaluja/bank-note-authentication-uci-data -p ..\Data --unzip 
```
[Data source link](https://www.kaggle.com/ritesaluja/bank-note-authentication-uci-data)
[Data](Data/BankNote_Authentication.csv)
*  Rows: 1372 / Columns: 5
    *   variance                   
    *   skewness                      
    *   curtosis                 
    *   entropy                 
    *   class                      
                    

<a name="DataPre-processing"></a>  

## [Data Pre-processing](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)
After I had all the data I needed, I needed to check it was ready for exploration and later modelling. I made the following changes and created the following variables:   
*   General NULL and data validity checks  
*   The datatypes needed fixing as well as renaming a column because of the use of the name 'class' in python<br>

```python
# Correcting data types 
data = data.selectExpr("cast(variance as double) variance",
    "cast(skewness as double) skewness",
    "cast(curtosis as double) curtosis",
    "cast(entropy as double) entropy",
    "cast(class as double) class")

# Renaming class column 
data = data.withColumnRenamed("class","outcome")
```

<a name="DataWarehousing"></a>

## [Data Warehousing](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)
I warehouse all data in a Postgre database for later use and reference.

*   ETL in python to PostgreSQL Database.
*   Formatted column headers to SQL compatibility.  <br>

```python 
# Function to warehouse data in a Postgre database and save cleaned data in Data folder -  AS THIS IS PYSPARK, THERE WAS A NEED TO ADD .toPandas anywhere the dataset is called 
def store_data(data,tablename):
    """
    :param data: variable, enter name of dataset you'd like to warehouse
    :param tablename: str, enter name of table for data 
    """

    # SQL table header format
    tablename = tablename.lower()
    tablename = tablename.replace(' ','_')

    # Saving cleaned data as csv
    data.toPandas().to_csv(f'../Data/{tablename}_clean.csv', index=False)

    # Engine to access postgre
    engine = create_engine('postgresql+psycopg2://postgres:password@localhost:5432/projectsdb')

    # Loads dataframe into PostgreSQL and replaces table if it exists
    data.toPandas().to_sql(f'{tablename}', engine, if_exists='replace',index=False)

    # Confirmation of ETL 
    return("ETL successful, {num} rows loaded into table: {tb}.".format(num=len(data.toPandas().iloc[:,0]), tb=tablename))
 
# Calling store_data function to warehouse cleaned data
store_data(data,"P10 Bank Note Authentication")
```

<a name="EDA"></a>  

## [Exploratory data analysis](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb) 
I looked at the distributions of the data and the value counts for the various categorical variables that would be fed into the model. Below are a few highlights from the analysis.
*   55.54% of the bank notes in the data are real notes.

<img src="/images/P10/banknote_barchart_distrib.png" />

*   Boxplots were used to visualise features with outliers. These features were not scaled as this was POC project. I know that LogisticRegression models are very sensitive to the range of the data points so scaling is advised. 
<img src="/images/P10/boxplots.png" />

*   I visualised the distribution of features for the fake bank notes 
<img src="/images/P10/histogramdistribution.png" />

*   The correlation matrix shows those features with strong and particularly weak correlations 
<img src="/images/P10/data_correlation.png" />


<a name="FeatEng"></a>  

## [Feature Engineering](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb) 
There was no need to transform the categorical variable(s) into dummy variables as they are all numeric. I also split the data into train and tests sets with a test size of 20%.
*   I had to random Split instead of using train_test_split from sklearn <br>

```python
# Splitting data into train and test data
train_data,test_data=model_data.randomSplit([0.80,0.20], seed=23)
```
<!-- *   One Hot encoding to encode values -->
  

<a name="ModelBuild"></a> 

## [ML/DL Model Building](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)

I used the LogisticRegression model and evaluated them using initially using accuracy_score and a confusions matrix. 
*   I fed the independent and dependent features to the model and training it on the training data <br>

```python
# Calling LinearRegression algorithm and applying features and outcome 
regressor=LogisticRegression(featuresCol='features', labelCol='outcome')

# Training model on training data 
model=regressor.fit(train_data)
```

<a name="ModelPerf"></a> 

## [Model performance](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)
The Logistic Regression model performed well on the train and test sets. 
*   **Logistic Regression** : Accuracy = 100% 


<a name="ModelEval"></a> 

## [Model Evaluation](https://github.com/MattithyahuData/P10-Bank-Note-Authentication/blob/master/Code/P10_Code.ipynb)
* The ROC Curve shows the accuracy show reflect of both the train and test datasets 
<img src="/images/P10/ROCtrain.png" />
<img src="/images/P10/ROCtest.png" />

*   A confusion matrix showing the accuracy score of True and False predictions achieved by the model. 
*   The model performed perfectly with no FP or FN (False Positive or False Negatives)

<img src="/images/P10/Confusionmatrixlog.png" />


<a name="Prjmanage"></a> 

## [Project Management (Agile/Scrum/Kanban)](https://www.atlassian.com/software/jira)
* Resources used
    * Jira
    * Confluence
    * Trello 

<a name="PrjEval"></a> 

## [Project Evaluation]() 
*   WWW
    *   The end-to-end process
    *   Use of Spark and Databricks
*   EBI 
    *   Look at productionising use MLlib
    

<a name="Lookahead"></a> 

## Looking Ahead
*   What next
*   More Pyspark??? 

<a name="Questions"></a> 

## Questions & Contact me 
For questions, feedback, and contribution requests contact me
* ### [Click here to email me](mailto:contactmattithyahu@gmail.com) 
* ### [See more projects here](https://mattithyahudata.github.io/)



[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
