# 🚀 The Indian Startup Funnding Analysis 2018 -2021 🚀
[![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
## Bright Ofori Boye Eshun


### Azubi Data Analytics Trainee Program

Git-hub repository at:
https://github.com/Bright136/Analysis-On-Indian-Startup-Funding-2018-2021

- Jupyter notebook: **Indian Startup Funding.ipynb**

- data set: startup_funding2018.csv, startup_funding2019.csv, startup_funding2020.csv, startup_funding2021.csv

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
This project was worked on as group in the Azubi Data Analytics Trainee program. The project is to allow students to showcase their knowledge and skills acquired so far in the program. The data to be used is the Indian startup data from 2018 to 2021. The data source is not known. This article will take us through Ask, Prepare, Process, Analyze, Share and Act phase of the analysis process.

##  2. Ask <a name="ask"></a>
In this phase we define the business objective, define our hypothesis and raise questions to support or reject out hypothesis.

###  2.1 Business Task
The business task was to analyze Indian startup data to give insights and answers to entreprenuers who are seeking to venture into the Indian start-up ecosystem by highlighting key metrics to consider before venturing.
###  2.2 Hypothesis

###  2.3 Assumptions
- In the 2018 Amount if the amount does not begin with any currency symbol it will be considered as in dollars.
- If the Year the company was founded and the year it was funded are the same, replace null values in the stage column with 'Seed' stage.

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
In this phase we will collect and store data for our upcoming analysis but in our case the data has already been given. We will have to identify the data being used and its limitations.

###  3.2 Infomation on Data
- The source of data is unknown 
- The data contains 4 csv files: 2018 start-ups, 2019 start-ups, 2020 start-ups and  20121 start-ups.

###  3.3 Limitations of Data 
- According to the ecomonicttimes.indiatimes.com, an economic survey showed that from 2020-2021 the government of India recognised 41,061 start-ups. This goes on to prove that most start-ups didn’t appear in the data.
- The 2018 start-ups data had 2 missing columns (Founders, Founded) compared to the 2019, 2020 and 2021 datasets.

###  3.3 Data Selection
We will use all 4 data csv files.

###  3.3 Tool
We will be using python for data cleaning, manipulation and visualization.

##  4. Process <a name="process"></a>
In this phase we will find and eliminate the errors, inaccuaries and inconsistencies in the data that get in the way of the analysis and results. This usually means cleaning and transforming the data to ensure that it is consistent, relevant and completely free from errors.

These are the basic steps we followed
1. Explore and observe the data
2. Check for and treat missing values or null values
3. Check and transaform data-data types
3. Merge all 4 datasets into one.

###  4.2 Loading packages
We loaded the libraries that will be used for this project. The libraries were aliased to make them easy to work with.

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
1. Explored data
2. Checked for null values 


Let's previewed the datasets and display the shape-number of rows and columns of the datasets and also check the data types


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



Let's checked if there are null values in the data.


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


The above step were repeated for 2019, 2020 and 2021 dataframe

After previewing the data the following observations were made:
>2018 Observations
- The dataframe had 6 columnsrow and 525 rows
- The columns in 2018 are different from 2019-2021 dataset
- The amount column has a mixture of Indian rupees and US dollar symbol
- The industry and location columns have multiple information
>2019 Observations
- Dataframe had 9 columns and 89 rows
- The founded column has float data type
- The amount column has object data type. It gas a dollar sign and commas
>2020 Observations
- Dataframe had 9 columns and 1054 rows
- The amount column has object data type. It gas a dollar sign and commas
- There's a column 'Unnamed: 9'
>2021 Observations
- Dataframe had 9 columns and 1208 rows
- The amount column has object data type. It gas a dollar sign and commas.
- The founded column has float data type

Now that we have noticed some of the issues with our data we can perform data cleaning and transformation.
- I dropped duplicate rows in each dataframe separately.
- I applied string formatting to all columns except the amounts columns which were formatted as numerics.
- I split the values in the location and industry columns in the 2018 dataframe using a comma as the delimiter and selected the first value as the primary sector.
- in the 2018 datframe I extracted the numerics values from the amount and converted the ones with rupees sigh into di=ollars using regialar expression.
- Created a column called 'Year of Funding' 2018, 2019, 2020 and 2021 and gave it a value of 2018, 2019, 2020 and 2021 respectively.
- I created another column call Fundung Status to identify whether a funding amount was specified or not, It had the values Undiscloed and Discloded.
- In 2018 datatframme I imputed the null values with mode using the SimpleImputer
- The na.nan values used to replace 'undisclosed' in the dataframe was maintaned but the ones already in the data was imputed with the mode using the SimpleImputer
- In each datframe null values in 'Funding Stage' columnn was replaced with 'seed' iif the funsing year is the same as the Founded year.
- I replaced the “nan” values in the “Founders” column with nulls.
- I replaced notable misplaced and/or erroneous values in the respective rows.
- I dropped the extra 'unnamed' column in the 2020 DataFrame.

After the dataframes has been cleaned indiviadually we merged it together. The 2019, 2020 and 2021 dataframes were merged together since the columns had the same names. The columns in 2018 were renamed before merging into our new data

After the dataframes were combined we did extra cleaning if the data.

- The Funding Stage column in the combined data were cleaned to acheive 29 distinsct stages using regular expressions.
- I create a new column called 'New Sector' this was a clean versions of the 'Sector'. The cleaning was done usinf regualr expressions.
- I  create a new column called 'Tech or Non-Tech' to classify the values in the setor as Tech or Non-Tech

>Cleaning 2018 dataframe

Lets clean the amount column in 2018

```
# Let's clean the Amount column
# replace commas and extract numbers to create a new column
df_2018['Amount($)'] = df_2018['Amount'].str.replace(',', '').str.extract(r'(\d+)').astype(float)      

# Let's assume the amount with no amount sign is already in dollars 
# loop through both Amount and Amount$ and convert Rupees into Dollars
for i in range(len(df_2018['Amount'])):
    df_2018.reset_index(drop=True, inplace=True)
    if df_2018.loc[i, 'Amount'][0] == '₹':
        df_2018.loc[i, 'Amount($)'] = df_2018.loc[i, 'Amount($)'] * 0.0146

# create a copy of the 2018 datframe
df_2018_copy = df_2018.copy()
df_2018_copy.head()
```
<img src="images\amount_18.png" alt="view" >

I will later on drop the 'Amount' column

I created new column for 'Year of Funding' and 'Funding Status'

```
# drop Amount column
df_2018_copy.drop(columns=['Amount'], inplace=True)

# Create Year of Funding column
df_2018_copy['Year of Funding'] = '2018'

#Create Funding Status column
df_2018_copy['Funding Status'] = 'Disclosed'

```


Let's impute the null values in the 'Amount($)' with the mode

```
# # fill null values with the mode in the Amount($) column
from sklearn.impute import SimpleImputer
imputer = SimpleImputer(strategy='most_frequent', missing_values=np.nan)
imputer_18 = imputer.fit(df_2018_copy[['Amount($)']])
df_2018_copy['Amount($)'] = imputer_18.transform(df_2018_copy[['Amount($)']])

```
After we confirm the number of missing values

```
# comfirm null value have been replaced
df_2018_copy['Amount($)'].isnull().sum()

0
```

>Cleaning 2019 dataframe
*Note 2019, 2020 and 2021 dataframes had similar issues. Most of the cleaning methods used on 2019 will be applied to 2020 and 2021*
let's createa a function to clean the "Amount($)" in 2019, 2020 and 2021 dataframe.
```
# Changing the data type of Founded column to a string
def clean_create_cols(data, fund_year):
    data['Amount($)'] = data["Amount($)"].replace({r"(\$$)": np.nan}, regex=True)
    # create a funsing status column
    data['Funding Status'] = data["Amount($)"].replace({r"(^[$\d].+)": "Disclosed"}, regex=True)
    # Changing the data type of Founded column to a string
    data["Amount($)"] = data["Amount($)"].replace({r"(\$U.+|\$u.+|U.+)": np.nan, "nan": np.nan}, regex=True)
    data["Amount($)"] = data["Amount($)"].replace({r"(\D)": ""}, regex=True).astype(float)
    # Adding a column to represent the year of funding
    data["Year of Funding"] = fund_year

```
In rows whwere the "Year Founded" is the ame as "Year of Funding" the null values in the Funding stage was filled with 'Seed'

```
# get index with empty stage
stage_null_2019 = founded_2019[founded_2019['Stage'].isnull()].index.tolist()
stage_null_2019

# fill stage null value with seed
df_2019_copy.at[stage_null_2019, 'Stage'] = 'Seed'

```


### Feature Engineering
I realised the the numerical column in the combined_set was just one so I created two columns 'Age at Funding' and 'Age of Company'. 'Age at Company' was how old the company has been in existence and 'Age at Funding was how old the company was at the time it recieved funding.



```
# Create new features/columns 'Company Age'  and 'Age at Funding'
combined_set['Company Age'] = 2022 - combined_set['Year Founded']

combined_set['Age at Funding'] = combined_set['Funding Year'] - combined_set['Year Founded']

```

##  5. Analyze <a name="analyze"></a>
In this we find the insights and relationships between the feature of the dataset. We can can start by looking at the statistical summary of the combined dataset.

We can check the 
- mean
- 25%, 50%, 75% percentiles
- Count
- Standard deviation and 
- min and max value in our numrical columns

<img src="images\statis.png" alt="view" >

The minimum amount received by a company as funding is $876 and the maximum amount is %150,000,000,000. The mean and the 25%, 50%, 75% percentiles in the amount column were $122,067,030.3, $1,000,000, $2,000,000, $9,000,000 respectively. Using the current year as 2022 we had startups that that had been around for 59 years. Company was able to pull off getting  funded as a startup at the Age of 50 years.


## 6. Share
In this Pahe we will alow the the data to tell its own story using visualizations. Visualizations will be used to communicate the findings and answer the questions we wanted to know anout the data in the ask phase.

