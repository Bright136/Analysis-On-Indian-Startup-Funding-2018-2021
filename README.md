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
This project was part of my projects to be completed in the Azubi Data Analytics Trainee program. The project is to allow students to showcase their knowledge and skills acquired so far in the program. The data to be used is the Indian startup data from 2018 to 2021. The data source is not known. This article will take us through Ask, Prepare, Process, Analyze, Share and Act phase of the data analysis process.

##  2. Ask <a name="ask"></a>
In this phase we define the business objective, define our hypothesis and raise questions to support or reject out hypothesis.

###  2.1 Business Task
The business task is to analyze Indian startup data to give insights and answers to entreprenuers who are seeking to venture into the Indian start-up ecosystem by highlighting key metrics to consider before venturing.
###  2.2 Hypothesis

###  2.3 Assumptions
- In the 2018 Amount if the amount does not begin with any currency symbol it will be considered as in dollars.
- If the Year the company was founded and the year it was funded are the same, replace null values in the stage column with 'Seed' stage.
- Rows with duplicate company names will be treated as multiple fundings.

###  2.3 Questions
- How many Tech and Non tech companies were funded?
- What was the trend funding over the years. How many companies were - funded each year?
- Top Ten Cities with Most Startups
- Did Companies receive multiple fundings through out the time period?
- Which sector had most startups?
- Which Top 10 Investors funded more (different companies)startups?
- What was the highest average funding yearly?
- What is the sum of investments Yealy?
- What is the sum of fundings in by sector class(Tech, Non Tech, - Unkown)
- Among the highly funded compnaies which of them were were Tech companies
- Which top 10 Funding Stages received most fundings? How much of it was used to fund a Tech companies?
###  2.4 Deliverables


##  3. Prepare Data <a name="prepare"></a>
In this phase we will collect and store data for our upcoming analysis but in our case the data has already been given. We will have to identify the data being used and its limitations.

###  3.2 Infomation on Data
- The source of data is unknown 
- The data contains 4 csv files: 2018 start-ups, 2019 start-ups, 2020 start-ups and  20121 start-ups.


###  3.3 Limitations of Data 
- According to the ecomonicttimes.indiatimes.com, an economic survey showed that from 2020-2021 the government of India recognised 41,061 start-ups. This goes on to prove that most start-ups didn’t appear in the data.
- The 2018 start-ups data had 2 missing columns (Founders, Founded) compared to the 2019, 2020 and 2021 datasets.
- I wouldn't say the is credible no reliable. This data can can not be considered in making real life recommendations to a enterpreneurs.

###  3.3 Data Selection
We will use all 4 data csv files.

###  3.3 Tool
We will be using python for data cleaning, manipulation and visualization.

##  4. Process <a name="process"></a>
In this phase we will find and eliminate the errors, inaccuaries and inconsistencies in the data that get in the way of the analysis and results. This usually means cleaning and transforming the data to ensure that it is consistent, relevant and completely free from errors.

These are the basic steps we will followed
1. Explore and observe the data
2. Check for and treat missing values or null values
3. Check and transaform data-data types
3. Merge all 4 datasets into one.

###  4.2 Loading packages
Let's load the libraries that will be used for this project. The libraries were aliased to make them easy to work with.

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


Let's preview the datasets and display the shape-number of rows and columns in the datasets and also check the data types


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


The above steps were repeated for 2019, 2020 and 2021 dataframe

After previewing the data the following observations were made:
>2018 Observations
- The dataframe has 6 columns and 525 rows
- The columns in 2018 are different from 2019-2021 dataset
- The amount column has a mixture of Indian rupees and US dollar symbol
- The industry and location columns have multiple information
>2019 Observations
- Dataframe had 9 columns and 89 rows
- The founded column has float data type
- The amount column has object data type. It has a dollar sign and commas
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
- In the 2018 datframe I extracted the numerics values from the amount and converted the ones with rupees sigh into dollars using regular expression.
- Created a column called 'Year of Funding' in the  2018, 2019, 2020 and 2021 datframe and gave it the value of 2018, 2019, 2020 and 2021 respectively.
- I created another column call Fundung Status to identify whether a funding amount was disclosed or not. It had the values 'Undiscloed' and 'Discloded'.
- In 2018 datatframme I imputed the null values in the Amount column with mode using the SimpleImputer.
- The np.nan values used to replace 'undisclosed' in the dataframe was maintaned but the ones already in the data was imputed with the mode using the SimpleImputer/ This was done for 2019, 2020 and 2021 dataframes.
- In each datframe null values in 'Funding Stage' columnn was replaced with 'seed' if the funding year was the same as the Founded year.
- I replaced the “nan” values in the “Founders” column with nulls.
- I replaced notable misplaced and/or erroneous values in the respective rows.
- I dropped the extra 'unnamed' column in the 2020 DataFrame.

After the dataframes has been cleaned indiviaduallym  we merged them together. The 2019, 2020 and 2021 dataframes were merged together first since the columns had the same names. The columns in 2018 were renamed before merging into our new data

After the dataframes were combined we did extra cleaning to the data.

- The Funding Stage column in the combined data were cleaned to acheive 30 distinsct stages using regular expressions.
- I create a new column called 'New Sector' this was a more clean version of the 'Sector'. The cleaning was done using regualr expressions.
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

Let's create new columns for 'Year of Funding' and 'Funding Status'

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
After lets's confirm the change in number of missing values

```
# comfirm null value have been replaced
df_2018_copy['Amount($)'].isnull().sum()

0
```

>Cleaning 2019 dataframe

*Note 2019, 2020 and 2021 dataframes had similar issues. Most of the cleaning methods used on 2019 will be applied to 2020 and 2021*

Let's createa a function to clean the "Amount($)" in 2019, 2020 and 2021 dataframe.
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
In rows where the "Year Founded" is the same as "Year of Funding", the null values in the Funding stage should be  filled with 'Seed'

```
# get indexes of rows with empty Funding stage
stage_null_2019 = founded_2019[founded_2019['Stage'].isnull()].index.tolist()
stage_null_2019

# fill stage null value with seed
df_2019_copy.at[stage_null_2019, 'Stage'] = 'Seed'

```


### Feature Engineering
I realised the the numerical column in the combined_set was just one so I created two columns 'Age at Funding' and 'Age of Company'. 'Age at Company' is how old the company is and 'Age at Funding' is how old the company was at the time it recieved funding.



```
# Create new features/columns 'Company Age'  and 'Age at Funding'
combined_set['Company Age'] = 2022 - combined_set['Year Founded']

combined_set['Age at Funding'] = combined_set['Funding Year'] - combined_set['Year Founded']

```
Some extra cleaning was done afterwards.

##  5. Analyze <a name="analyze"></a>
In this phase we find the insights and relationships between the feature of the dataset. We can can start by looking at the statistical summary of the combined dataset.

We can check the 
- mean
- 25%, 50%, 75% percentiles
- Count
- Standard deviation and 
- min and max value in our numrical columns

<img src="images\statis.png" alt="view" >

The minimum amount received by a company as funding is $876 and the maximum amount is $150,000,000,000. The mean and the 25%, 50%, 75% percentiles in the amount column were $114,274,992.7, $1,000,000, $2,500,000, $10,000,000 respectively. Using the current year as 2022 we had a startup that had been around for 59 years. Company was able to pull off getting  funded as a startup at the age of 58 years.

The rest of the analysis will be added to share phase. Visualizations will be provided to answer our questions


## 6. Share
In this phase we will allow the data to tell its own story using visualizations. Visualizations will be used to communicate the findings and answers to the questions we asked about the data in the ask phase.

### 6.1 Communicating Findings
### Univariate Analysis

#### How many Tech and Non tech companies were funded?

```

# count the values in the 'Tech or Non Tech' column
sector_class = combined_no_duplicates['Tech or Non-Tech'].value_counts()
sector_class
Tech        1176
Non Tech     994
Unknown       44
Name: Tech or Non-Tech, dtype: int64



# plot a bar chart represeting the count of the sector class
plt.figure(figsize=(8, 5))
sns.countplot(data=combined_set, x='Tech or Non-Tech')
plt.title('Count of Sector Class')
plt.xlabel('Sector Class')
plt.show();

```

<img src="images\tech1.png" alt="view" >

- Through the period from 2018 to 2021 more than 1150 Tech companies were funded.
- There are about 994 non tech companies that were funded too.
- The rest companies had unknown sector class.

#### What was the trend of funding over the years. How many companies were funded each year?


```
# plot a line gragh to show the trend of startup with the period 2018 - 2021
plt.figure(figsize=(16, 5))
plt.subplot(1, 2, 1)
funding_year_count = combined_set.groupby(['Funding Year'])['Company Name'].count()
funding_year_count.plot();
plt.title('Trend of Startups over the period')


# plot a bar chart to show the number of startups within each year
plt.subplot(1, 2, 2)
sns.countplot(
    x='Funding Year',  
    data=combined_set, 
    color=base_color)

plt.title('Number of Companies Funded In The Year 2018 - 2021')
plt.show()

```
<img src="images\trend.png" alt="view" >

- The rend of the indian startup ecosysten has been increasing yearly except that there was the number of startups dropped in the year 2019, from more than 500 startups in 2018 to less than 100 startups in 2019. We can expect an increase in the number startup in the next year.

#### Top Ten Cities with Most Startups
```
# count the number of startups in each city
top_ten_HQ = combined_set['Headquarters'].value_counts().head(10).sort_values()
top_ten_HQ
Hyderabad     76
Gurgaon       80
Noida         86
Delhi         88
Pune         104
Chennai      106
New Delhi    230
Gurugram     238
Mumbai       468
Bangalore    859
Name: Headquarters, dtype: int64


# plot a horinzontal bar chart to show the number of startups in each city
plt.figure(figsize=(12, 5))
top_ten_HQ.plot(kind='barh')
plt.title('Top Ten Cities with Most Startups')
plt.xlabel('Count')
plt.ylabel('Cities');


```
<img src="images\cities.png" alt="view" >

- Cities that headquartered most startups within the period 2018 to 2021 were in the order Bangalore, Mumbai, Gurugram, New Delhi,, Chennai, Pune, Delhi, Noida, Gurgaon, Hyderabad with 859, 468, 238, 230, 106, 104, 88, 86, 80, 76 startups respevtively
-  Bangalore has alomost twice the number of starups in India's largest city Mumbai. There is a higher chance to be funded as a startup if you have your headquarters in any of these cities.

#### Did Companies receive multiple fundings through out the time period? 

```
# get the fraction of the number of company that received funding once, twice and three times or more
total = len(number_of_fundings)
number_of_fundings['Number of Fundings'] = number_of_fundings['Number of Fundings'].astype(int)

one_funding = len(number_of_fundings[number_of_fundings['Number of Fundings'] == 1]) / total
two_funding = len(number_of_fundings[number_of_fundings['Number of Fundings'] == 2]) / total

multiple_funding = len(number_of_fundings[number_of_fundings['Number of Fundings'] >= 3]) / total
print(one_funding +two_funding+ multiple_funding)
1.0



# plot a bar chart to show the fractions or percentages for fundings
plt.figure(figsize=(8, 5))
locations = [1, 2, 3]
heights = [one_funding, two_funding, multiple_funding]
labels = ['Once Funded', 'Twice Funded', 'Multiple Funded']
plt.bar(locations, heights, tick_label=labels)
plt.title('T')
plt.xlabel('Number of times funded')
plt.ylabel('Fraction')

```

<img src="images\frequency.png" alt="view" >

Over the period of four years only 6% out of the total number of funded startups were funded more than twice. Around 13 percent of the total number of startup were funded twice, the rest were all funded once. There is a high possibility of receving funding just once within a longer time period.

#### Which sector had most startups?


```
# check the top 10 cities with the most startups
Top_ten_sectors = combined_set['New Sector'].value_counts().head(10)
Top_ten_sectors

Fintech                    276
Edtech                     261
Healthcare and wellness    169
Financial services         168
E-commerce                 128
Food and nutrition         103
It                          81
Automotive                  80
Artificial inteligence      76
Technology                  67
Name: New Sector, dtype: int64



# plot a bar chart to show the top 10 sectors with the most number of startups
plt.figure(figsize=(8, 5))
Top_ten_sectors.sort_values().plot(kind='barh')
plt.title('Top 10 Sectors with the Most Startup')
plt.xlabel('Number of Startups')
plt.ylabel('Sector');
```
<img src="images\sector.png" alt="view" >


> The top 10 sectors with the most startups were in the order of, from first to tenth: Fintech, Edtech, Healthcare and wellness , Financial services, E-commerce, Food and nutrition, It, Automotive, Artificial inteligence, Technology with 276, 261, 169, 168, 128, 103, 81, 80, 76 and 67 startups respectively. Enterpreneurs can to venture into these top 10 sectors to increase their chances of getting funded. Out of the sectors with most startups 7 of them were tech companies.



#### Which Top 10 Investors funded more (different companies)startups


```
Top_10_investors_ = combined_no_duplicates['Investors'].value_counts().head(10)
Top_10_investors_

Inflection Point Ventures    28
Venture Catalysts            25
Mumbai Angels Network        16
Angel investors              14
Titan Capital                11
Undisclosed                  10
Unicorn India Ventures       10
Sequoia Capital India         7
Better Capital                7
Elevation Capital             6
Name: Investors, dtype: int64

plt.figure(figsize=(8, 5))
Top_10_investors_.sort_values().plot(kind='barh')
plt.title('Top 10 Investors who funded different startups')
plt.xlabel('Number of Startups')
plt.ylabel('Investor');

```

<img src="images\investor.png" alt="view" >

- Together these Investors Funded more than 120 startup. Inflection Point Ventures and Venture Catalysts funded 28 and 25 different compabies respectively.


### Multivariate Analysis
####  What is the highest average funding yearly?


```
# get the average(mean) funding yearly
average_funding_year= combined_set.groupby(['Funding Year']).agg({'Amount': 'mean'})
average_funding_year.reset_index(inplace=True)
average_funding_year

	Funding Year	Amount
0	2018	12932425.1
1	2019	43330301.3
2	2020	112950185.8
3	2021	171218804.6


# plot a bar chart to show the avearge funding yearly
plt.figure(figsize=(22, 10))
plt.subplot(1, 2, 1)
sns.barplot(
    data=average_funding_year,
    x='Funding Year',
    y='Amount',
    color=base_color)
plt.title('Average Funding Per Year')

# plot a box plot to show the avearge funding yearly
plt.subplot(1, 2, 2)
sns.boxplot(data=combined_set, y='Amount', x='Funding Year')
plt.title('Funding vs  Year');
plt.ylim(-10,80000000);

```


<img src="images\average.png" alt="view" >

- Looking at the the bar chart graph the average funding by mean has been increasing yearly. From around 13M dollars in 2018 to 43M dollars in 2019 to 113M dollars in 2020 to 171 M dollars in 2021.
- Lokking at the boxplot the year 2019 has the highest average by median compared to the years.This was due to the fact that 2019 had a very small number of startups recorded. Most of the amount in 2018, 2020 and 2021 were treated as outliers. Considering the current trend we can anticipate/assume the median funding in the subsequent years will increase or be high.


### What is the sum of investments Yealy?


```
# get the sum of fundings per year
sum_funding_year= combined_set.groupby(['Funding Year']).agg({'Amount': 'sum'})
sum_funding_year.reset_index(inplace=True)
sum_funding_year


	Funding Year	Amount
0	2018	6789523177.0
1	2019	3336433200.0
2	2020	90924899604.0
3	2021	179608526000.0

# plot a bar chart to show te sum of funings in ech year
plt.figure(figsize=(8, 5))
sns.barplot(
    data=sum_funding_year,
    x='Funding Year',
    y='Amount',
    color=base_color)

plt.title('Sum of Funding Per Year')
plt.show()
```
<img src="images\sum.png" alt="view" >
- Clearly the year with highest number of startups  had the highest sum of funding.

### What is the sum of fundings in by sector class(Tech, Non Tech, Unkown)

```
# group the dataframe by sector class and get the sum
sum_sector_class = combined_set.groupby(['Tech or Non-Tech'])['Amount'].sum()
sum_sector_class

Tech or Non-Tech
Non Tech    98776168099.0
Tech       181567569962.0
Unknown       315643920.0
Name: Amount, dtype: float64


# plot a bar chart to show the sum of the fundings in each sector class
plt.figure(figsize=(8, 5))
sum_sector_class.plot(kind='bar')
plt.title('Sum Fundings by Sector class', pad=40)
plt.ylabel('Sum')
plt.xlabel('Sector Class')
plt.show()

```

<img src="images\tech2.png" alt="view">


- The total amount of funds received by Tech companies was more than Non Tech companies
- It was around 181B dollars for Tech against the 99B dollars for Non Tech


#### Among the highly funded compnaies which of them were Tech companies

```
# get the median amountin the dataframe 
median = combined_set['Amount'].median()
# create filter of the companies that received funding greater than the median value
highly_funded = combined_no_duplicates.query('Amount > {}'.format(median))
# count the nnumber of companies in the sector class
highly_funded_companies = highly_funded['Tech or Non-Tech'].value_counts()
highly_funded_companies

Tech        440
Non Tech    347
Unknown      12
Name: Tech or Non-Tech, dtype: int64


# plot a bar chart to show the number of highly funded companies in each sector class
plt.figure(figsize=(8, 5))
highly_funded_companies.plot(kind='bar')
plt.title('Number highly funded compines ', pad=40)
plt.ylabel('Number of startups')
plt.xlabel('Sector Class')
plt.show()


```
<img src="images\highf.png" alt="view">

- From the chart, the Tech sector class had the highest number highly funded startups. It had 440 startups compared to Non Tech's 347


#### Which top 10 Funding Stages received most fundings? How much of it was used to fund a Tech companies?

```
# Used a stacked barplot to visualize the data
stacked_cities_df_.plot(kind='bar', stacked=True, color=['red', 'skyblue', 'green'], figsize=(8, 100))
plt.title('Investments by cities according to sector class', pad=40)
plt.xlabel('Headquarters')
plt.ylabel('Amount')
plt.ylim(0, 2.4e11)
plt.show()

```
<img src="images\stack1a.png" alt="view">



When zoomed into the chart.

<img src="images\stack1b.png" alt="view">
- From the graph, Mumbai startups had a more than 230billion dollars in fundings. Out of the Fundings almost two-third of it was used to fund Tech companies. Tech companies that heardquarted in carlifonia had all of their funds used to fund Tech companies. Bangalore, Chennai, Delhi, New Delhi and Prune had more of their fundings used to invest in Tech comapnies.




## 7. Act
In this phase we give recommendations alse explain to our stakeholser the meanings of the findings we have acheived so far and how we can use it to make data driven decisions.

#### 7.1 Recommendations