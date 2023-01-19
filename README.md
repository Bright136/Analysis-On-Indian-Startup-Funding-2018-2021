# 🚀 The Indian Startup Funnding Analysis 2018 -2021 🚀
[![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
## Bright Ofori Boye Eshun


### Azubi Data Analytics Trainee Program

Git-hub repository at:
https://github.com/Bright136/Analysis-On-Indian-Startup-Funding-2018-2021

- Jupyter notebook: **Indian Startup Funding.ipynb**
- data set: .csv

<img src="https://www.startupindia.gov.in/content/sih/en/funding/_jcr_content/main/row_container-banner/row-content/image.img.png/1623322163395.png" alt="Startup" >

# Table of contents
1. [Introduction](#introduction)
2. [Ask](#ask)
    1. [Business Task](#prepare)
    2. [Hypothesis ](#sec3p1)
    3. [Assumptions](#sec3p2)
    4. [Questions](#sec3p3)
    5. [Deliverables](#sec3p3)
3. [Prepare Data](#prepare)
    1. [Information on Data ](#sec3p1)
    2. [Limitations of Data](#sec3p2)
    3. [Data Selection](#sec3p3)
    4. [Tool](#sec3p3)



## 1. Introduction <a name="introduction"></a>
This project as worked on as group while enrolled in the Azubi Data Analytics Trainee program. The project is to allow students to showcase their knowledge and skills acquired so far in the program. The data to be used is the Indian startup data from 2018 to 2021. The data source is not known. This article will take us through Ask, Prepare, Process, Analyze, Share and Act phase.

##  2. Ask <a name="ask"></a>
In this phase we define the business objective, define our hypothesis and raise questions to support or reject out hypothesis.

###  2.1 Business Task
The business task was to analyze an Indian startup data to gain insights answer to influence the decisions of startup companies.
###  2.2 Hypothesis

###  2.3 Assumptions
- In the 2018 Amount if the amount does not begin with any currency symbol it will be considered as in dollars.
- If the Year the company was founded and the year it was funded are the same, replace null values in the stage column with 'Seed' stage
###  2.3 Questions
- How many companies were funded each year?
- Which sectors had most startups each year?
- What was the highest average funding yearly?
- Did Companies receive multiple funding through out the time period? What are the percentages?
- Which cities had most startups?
- Which Investors funded more startups?
- Is there any correlation between the features?:
- What was the dominant startups in the top cities
- What is the correlation between Company Age at the time of funding and Amount?
- What is the relationship between the Amount and the top 4 Funding Stage?
- What is the relationship between the top 3 Cities with more startups, the funding stage and the amount
###  2.4 Deliverables


##  3. Prepare Data <a name="prepare"></a>
In this phase we will collect and store data for our upcoming analysis but in our case the data has already been given. We will have to identify the data v=being used and its limitations.

###  3.2 Infomation on Data
- The source of data is unknown 
-	The data contains 4 csv files: 2018 start-ups, 2019 start-ups, 2020 start-ups and  20121 start-ups.

###  3.3 Limitations of Data 
- The according to the ecomonicttimes.indiatimes.com, an economic survey showed that from 2020-2021 the government of India recognised 41, 061 start-ups. This goes on to prove the most start -ups didn’t appear in the data.
- The 2019 start-ups data had 2 missing columns compared to the 2019, 2020 and 2021 datasets.

###  3.3 Data Selection
We will use all 4 data csv files.

###  3.3 Tool
We will be using python for data cleaning, manipulation and visualization.

##  4. Process <a name="process"></a>
In this phase we will find and eliminate the errors, inaccuaries and inconsistencies in the data that get in the way of the analysis and results. This usually means cleaning and transforming the data to ensure that it is consistent, releveant and and completely free from errors.

Explore and observe the data
Check for and treat missing values or null values
Check and transaform data-data types
Merge all 4 datasets into one.

###  4.2 Loading packages
We loaded the libraries that will be used for this. The libraries were aliased to make easy to work with.

```
# Data manipulation and cleaning
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np

```

### Importing Datasets
We imported the selected files.
```
# load the datasets with pandas
df_2018 = pd.read_csv('startup_funding2018.csv')
df_2019 = pd.read_csv('startup_funding2019.csv')
df_2020 = pd.read_csv('startup_funding2020.csv')
df_2021 = pd.read_csv('startup_funding2021.csv')

print('Dataset loaded')

```



###  4.3 Data Cleaning and Manupulation
1. we Explored data
2. we checked for null values 



We previewed the 2018 datasets and display the shape of the datasets.


```
# Check the datatypes
df_2018.info()

# display  dataframe
df_2018.head()

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 526 entries, 0 to 525
Data columns (total 6 columns):
 #   Column         Non-Null Count  Dtype 
---  ------         --------------  ----- 
 0   Company Name   526 non-null    object
 1   Industry       526 non-null    object
 2   Round/Series   526 non-null    object
 3   Amount         526 non-null    object
 4   Location       526 non-null    object
 5   About Company  526 non-null    object
dtypes: object(6)
memory usage: 24.8+ KB
```
<img src="images\view.png" alt="view" >



We checked to see if there are null values in the data.


```
# check the null values in each column of the dateframe
df_2018_copy.isnull().sum()


Company Name         0
Industry             0
Round/Series         0
Location             0
About Company        0
Amount($)          148
Year of Funding      0
Funding Status       0
dtype: int64

```
After previewing the data the following observations were made:
>2018 Observations

- The columns in 2018 are different from 2019-2021 dataset
- The amount column has a mixture of Indian rupees and US dollar symbol
- The industry and location columns have multiple information
>2019 Observations

- The founded column has float data type
- The amount column has object data type. It gas a dollar sign and commas
>2020 Observations

- The amount column has object data type. It gas a dollar sign and commas
- There's a column 'Unnamed: 9'
>2021 Observations

- The amount column has object data type. It gas a dollar sign and commas.
- The founded column has float data type

Now that we have noticed some of the issues with our data we can perform data cleaning and transformation.

- I applied string formatting to all columns except the amounts columns which were formatted as numerics.
- I separated the values in the location and industry columns using a comma as the delimiter and selected the first value in the split column as the primary sector.
- For the 2018 Amount column, I created two new columns to help with the currency conversion and then dropped them after standardising the amounts.
- I removed all commas and currency signs from the “Amounts” columns.
- I replaced the “Undisclosed” text in the “Amounts”.
- I replaced the “nan” values in the “Founders” column with nulls.
- I replaced notable misplaced and/or erroneous values in the respective rows.
- I dropped the extra unnamed in the 2020 DataFrame.
For each DataFrame, I appended a column indicating the year of funding


##  5. Analyze <a name="analyze"></a>