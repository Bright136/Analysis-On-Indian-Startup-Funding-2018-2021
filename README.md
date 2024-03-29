# 🚀 The Indian Startup Funnding Analysis 2018 -2021 🚀
[![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
[![python](https://img.shields.io/badge/Jupyter-white?style=for-the-badge&logo=jupyter&logoColor=orange)](https://img.shields.io/badge/Jupyter-3776AB?style=for-the-badge&logo=jupyter&logoColor=white)
[![pandas](https://img.shields.io/badge/Pandas-0C134F?style=for-the-badge&logo=pandas)](https://img.shields.io/badge/Pandas-3776AB?style=for-the-badge&logo=pandas&logoColor=white)


### Azubi Data Analytics Trainee Program


- Jupyter notebook: <a href='dev\notebooks\Indian Startup Funding.ipynb'>**Indian Startup Funding.ipynb**</a>

- datasets: <a href='dev\datasets'>**Datasets**</a>

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
4. [Process Data](#prepare)
    1. [Loading Packages ](#sec3p1)
    2. [Importing Dataset](#sec3p2)
    3. [Data Cleaning and Manipulation](#sec3p3)
    4. [Feature Engineering](#sec3p3)
5. [Analyse Data](#analyse)
 
6. [Share Data](#share)
    1. [Communicating Findings ](#sec3p1)

7. [Act Data](#prepare)
    1. [Recommendations ](#sec3p1)


## 1. Introduction <a name="introduction"></a>
This project was part of my projects to be completed in the Azubi Data Analytics Trainee program. The project is to allow students showcase their knowledge and skills acquired throughout the program so far.

The data to be used is contained a zip file that with 4 csv files for Indian startup data for 2018 to 2021. The source of data is unknown. This article will take us through the Ask, Prepare, Process, Analyze, Share and Act phase of the data analysis process as used in the Google Data Analytics Course.

##  2. Ask <a name="ask"></a>
In this phase we define the business objective, develop ahypothesis and raise questions to support or reject our hypothesis and aslo to get some general insights into the data.

###  2.1 Business Task
The business task is to analyze Indian startup data to give insights and answers to entreprenuers who are seeking to venture into the Indian start-up ecosystem by highlighting key metrics to consider before venturing.

###  2.2 Hypothesis

**Null Hypothesis**: Technology companies receive more funding than the rest of the sectors.

**Alternate Hypothesis**: Technology companies do not receive more funding than the rest of the sectors.

###  2.3 Assumptions
- In the 2018 data, if the amount does not begin with any currency symbol, it will be considered as dollars.
- If the year the company was founded is the same as the year it was funded, we will replace null values in the Stage column with ‘Seed’ value.
- Rows with duplicate company names will be treated as multiple fundings

###  2.4 Questions
1. How many Tech and Non Tech companies were funded?
2. What was the trend for funding over the years. How many companies were funded each year?
3. What were the Top Ten Cities with Most Startups?
4. Did Companies receive multiple fundings through out the time period?
5. Which sectors had most startups?
6. Which Top 10 Investors funded more (different companies)startups?
7. What was the highest average funding yearly?
8. What is the sum of investments yealy?
9. What is the sum of fundings by sector class(Tech, Non Tech, — Unkown)?
10. Among the highly funded companies which of them were Tech companies?
11. Which top 10 Funding Stages received most fundings? How much of it was used to fund a Tech companies?
12. Which top 10 Cities received most fundings? How much of it was used to fund Tech companies?
###  2.5 Deliverables
1. A hypothesis.
2. Questions to help gain insights into the data.
3. A summary of the Analysis.
4. Visualizations to communicate findings.
5. Recommendations based on the analysis.


##  3. Prepare Data <a name="prepare"></a>
In this phase we will collect and store data for our analysis but in our case the data has already been given. We will have to identify the data being used and its limitations.

###  3.1 Infomation on Data
1. The source of data is unknown.
2. The data contains 4 csv files: startup_funding2018.csv, startup_funding2019.csv, startup_funding2020.csv and startup_funding2021.csv.

The columns in the data are:
- Company Name — The name of the company.
- Founded — The year the company was founded.
- Sector — The sector the company operates in.
- Stage — The funding stage of the company.
- Location — The location of the company’s headquarters.
- Amount — The amount of funding the company received.
- Description — The ‘The About of company’.
- Investor — The investor who funded the company.
- Founder — The founders of the company.


###  3.2 Limitations of Data 
1. According to the ecomonicttimes.indiatimes.com, an economic survey showed that from 2020–2021 the government of India recognised 41,061 start-ups. This goes on to prove that most start-ups didn’t appear in the data.
2. The 2018 start-up data has 2 missing columns (Founders, Founded) compared to the 2019, 2020 and 2021 datasets.
3. I wouldn’t say the data is credible nor reliable. This data can not be considered when making real life recommendations for entrepreneurs.

###  3.3 Data Selection
All 4 csv files will be used for the analysis.

###  3.4 Tool
Python will be used for data cleaning, manipulation and visualization.

##  4. Process <a name="process"></a>
In this phase we will find and eliminate the errors, inaccuracies and inconsistencies in the data that will get in the way of the analysis and results. This usually means cleaning and transforming the data to ensure that it is consistent, relevant and completely free from errors.

These are the basic steps to be followed.

1. Explore and observe the data.
2. Check for and treat missing values or null values.
3. Check and transaform data-data types.
4. Merge all 4 datasets into one.

###  4.1 Loading packages
Let’s load the libraries that will be used for this project. The libraries were aliased to make them easy to work with.

```
# Data manipulation and cleaning
import pandas as pd # Data manipulation
import numpy as np # Data manipulation
import seaborn as sns # Data visualization
import matplotlib.pyplot as plt # Data visualization

```

### 4.2 Importing Datasets
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
1. Explore data
2. Check for null values 


Let’s preview the datasets and display the shape-number of rows and columns in the datasets and also check the data types.


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
<img src="dev\images\view.png" alt="view" >



Let’s check for null values in the data.


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


*The above steps were repeated for 2019, 2020 and 2021 dataframe*

After previewing the data the following observations were made:
>2018 Observations
- The dataframe has 6 columns and 525 rows
- The columns in 2018 are different from 2019-2021 dataset
- The amount column has a mixture of Indian rupees and US dollar symbol
- The industry and location columns have multiple information
>2019 Observations
- Data frame had 9 columns and 89 rows.
- The ‘Founded’ column has a float data type.
- The ‘Amount’ column has object data type. It has dollar sign and commas.
>2020 Observations
- Data frame has 9 columns and 1054 rows.
- The ‘Amount’ column has object data type. It has dollar sign and commas.
- There’s an erroneous column ‘Unnamed: 9.
>2021 Observations
- Data frame has 9 columns and 1208 rows.
- The ‘Amount’ column has object data type. It has dollar sign and commas.
- The ‘Founded’ column has a float data type

Now that we have noticed some of the issues with our data, we can perform data cleaning and transformation.

Steps involved in cleaning the data:

- I dropped duplicate rows in each data frame.
- I applied string formatting to all columns except the amounts columns which were formatted as numeric.
- I split the values in the location and industry columns in the 2018 data frame using a comma as the delimiter and selected the first value as the primary sector.
- In the 2018 data frame I extracted the numeric values from the amount and converted the ones with rupees sign into dollars using regular expression.
- I created a column called ‘Year of Funding’ in the 2018, 2019, 2020 and 2021's data frame and gave it a value of 2018, 2019, 2020 and 2021 respectively.
- I created another column called ‘Funding Status’ to identify whether a funding amount was disclosed or not. It had the values ‘Undisclosed’ and ‘Disclosed’.
- In 2018 data frame I imputed the null values in the Amount column with mode using the SimpleImputer.
- The np.nan values used to replace ‘undisclosed’ in the Amount column were maintained but the null values that already existed in the data were imputed with the mode using the SimpleImputer from Sklearn. This was repeated for 2019, 2020 and 2021 data frames.
- In each data frame null values in Funding Stage column was replaced with ‘Seed’ if the funding year was the same as the founded year.
- I replaced notable misplaced and/or erroneous values in the respective rows.
- I dropped the extra ‘unnamed’ column in the 2020 data frame.

After the data frames have been cleaned individually, we merged them together. The 2019, 2020 and 2021 data frames were merged together first since the columns had the same names. The columns in 2018 were renamed before merging into our new data

After the data frames were combined we did extra cleaning on the data.

- The Funding Stage column in the combined data were cleaned to achieve 30 distinct stages using regular expressions.
I created a new column called ‘New Sector’ which was a more cleaned version of the ‘Sector’ column. The cleaning was done using regular expressions.
- I created a new column called ‘Tech or Non-Tech’ to classify the values in the sector as Tech or Non-Tech.

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

<img src="dev\images\amount_18.PNG" alt="view" >

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

>Cleaning Combined Dataset

Let’s combine the datasets

```
# Joining all DataFrames with similar column names
combined_2019_2021 = pd.concat([df_2019_copy, df_2020_copy, df_2021_copy], ignore_index = True)
combined_2019_2021.columns = ["Company Name", "Year Founded", "Headquarters", "Sector", "Description", "Founders", "Investors", "Amount", "Funding Stage", "Funding Status", "Funding Year"]


# Renaming the columns in the 2018 dataframe to match with the other dataframes
df_2018_copy.columns = ['Company Name', 'Sector', 'Funding Stage', 'Headquarters', 'Description', 'Amount', 'Funding Year', 'Funding Status']


# Joining the 2018 DataFrame to the 2019-2021 DataFrame
combined_set = pd.concat([df_2018_copy, combined_2019_2021], ignore_index = True)
combined_set.head()

```

<img src="dev\images\Combined.PNG" alt="view" >

Let’s clean the Funding Stages column

<img src="dev\images\correc.PNG" alt="view" >

```

# Run and effect changes in the dataset
combined_set['Funding Stage'] = combined_set['Funding Stage'].str.capitalize().replace(Stage_corrections, regex=True)

# get the number of unique stages
Stages = combined_set['Funding Stage'].sort_values().unique()
print(len(Stages))
Stages

30
array(['Angel', 'Bridge', 'Corporate round', 'Debt Financing', 'Edge',
       'Fresh Funding', 'Grant', 'Mid series', 'Non-equity assistance',
       'Post-ipo debt', 'Post-ipo equity', 'Pre Seed', 'Pre Series A',
       'Pre Series B', 'Pre Series C', 'Pre-series', 'Private equity',
       'Secondary market', 'Seed', 'Series A', 'Series B', 'Series C',
       'Series D', 'Series E', 'Series F', 'Series G', 'Series H',
       'Series i', 'Undisclosed', 'Unknown'], dtype=object)



```

### Feature Engineering
I realised the Amount column was the only numerical column in the combined data. I created two numerical columns ‘Age at Funding’ and ‘Age of Company’. This will help incase we want find correlations between the features. ‘Age of Company’ is how old the company is and ‘Age at Funding’ is how old the company was at the time it received funding.



```
# Create new features/columns 'Company Age'  and 'Age at Funding'
combined_set['Company Age'] = 2022 - combined_set['Year Founded']

combined_set['Age at Funding'] = combined_set['Funding Year'] - combined_set['Year Founded']

```
Some extra cleaning was done afterwards.

##  5. Analyze <a name="analyze"></a>
In this phase we find the insights and relationships between the features/columns of the combined data. We can can start by looking at the statistical summary.

We can check the following:

- mean
- 25%, 50%, 75% percentiles
- count
- standard deviation and
- min and max values in our numrical columns


<img src="dev\images\statis.PNG" alt="view" >

From the figure above, the minimum amount received by a company was $876 and the maximum amount was $150,000,000,000. The mean and the 25%, 50%, 75% percentiles in the amount column were $114,274,992.7, $1,000,000, $2,500,000, $10,000,000 respectively. Using the current year as 2022 we had a startup that had been around for 59 years and was able to pull off getting funded as a startup at the time when it was 58 years old.

The rest of the analysis will be added to share phase. Visualizations will be provided to answer the questions in the Ask phase.



## 6. Share
In this phase we will allow the data to tell its own story using visualizations. Visualizations will be used to communicate the findings and answers to the questions raised about the data.

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

<img src="dev\images\tech1.png" alt="view" >

- Through the period from 2018 to 2021 more than 1150 Tech companies were funded.
- There are about 994 non tech companies that were funded too. The rest of companies had unknown sector class.

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


<img src="dev\images\trend.PNG" alt="view" >

- The trend in the indian startup ecosysten has been increasing yearly except that the number of startups dropped in the year 2019, from more than 500 startups in 2018 to less than 100 startups in 2019. We can expect an increase in the number startup in the year after 2021.

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
<img src="dev\images\cities.png" alt="view" >

- Cities that headquartered most startups within the period 2018 to 2021 were in the order Bangalore, Mumbai, Gurugram, New Delhi,, Chennai, Pune, Delhi, Noida, Gurgaon, Hyderabad with 859, 468, 238, 230, 106, 104, 88, 86, 80, 76 startups respevtively.
- Bangalore has almost twice the number of startups in India’s largest city Mumbai. There is a higher chance to be funded as a startup if you have your headquarters in any of these cities.

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

<img src="dev\images\frequency.png" alt="view" >

Over the period of four years only 6% of the total number of funded startups were funded more than twice. Around 13 percent of the total number of startup were funded twice, the rest were all funded once. There isn’t high possibility of being funded more than twice within even a longer time period.

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
<img src="dev\images\sector.png" alt="view" >


- The top 10 sectors with the most startups weThe top 10 sectors with the most startups were in the order of- from first to tenth: Fintech, Edtech, Healthcare and wellness , Financial services, E-commerce, Food and nutrition, It, Automotive, Artificial inteligence, Technology with 276, 261, 169, 168, 128, 103, 81, 80, 76 and 67 startups respectively.
- Enterpreneurs can to venture into these top 10 sectors to increase their chances of getting funded. Out of these sectors , 7 of them were tech companies



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

<img src="dev\images\investor.png" alt="view" >

- Together these Investors Funded more than 120 startups. Inflection Point Ventures and Venture Catalysts funded 28 and 25 different compabies respectively. We can later find out which sectors or sector class these investors were involed in most.


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


<img src="dev\images\average.png" alt="view" >

- Looking at the the bar chart graph, the average funding by mean has been increasing yearly. From around 13M dollars in 2018 to 43M dollars in 2019 to 113M dollars in 2020 and to 171 M dollars in 2021.
- From at the boxplot the year 2019 has the highest average by median compared to the other years. This was due to 2019 having a very small number of startups recorded. Most of the amount in 2018, 2020 and 2021 were treated as outliers. Considering the current trend we can anticipate/assume the median funding in the subsequent years will increase or be high.

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
<img src="dev\images\sum.png" alt="view" >
- Clearly the year with highest number of startups had the highest sum.

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

<img src="dev\images\tech2.png" alt="view">


- The total amount of funds received by Tech companies was more than Non Tech companies. It was around 181B dollars for Tech against the 99B dollars for Non Tech. The amount for “Unknown” isn’t visisble because compared to the rest it was very small.


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
<img src="dev\images\highf.png" alt="view">

- From the chart, the Tech sector class had the highest number highly funded startups. It had 440 startups compared to Non Tech’s 347


#### Which top 10 Cities received most fundings? How much of it was used to fund a Tech companies?

```
# Used a stacked barplot to visualize the data
stacked_cities_df_.plot(kind='bar', stacked=True, color=['red', 'skyblue', 'green'], figsize=(8, 100))
plt.title('Investments by cities according to sector class', pad=40)
plt.xlabel('Headquarters')
plt.ylabel('Amount')
plt.ylim(0, 2.4e11)
plt.show()

```
<img src="dev\images\stackedcities.png" alt="view">



- From the graph, Mumbai startups had a more than 230billion dollars in fundings. Out of the Fundings almost two-thirds of it was used to fund Tech companies. Tech companies that heardquarted in carlifonia had all of their fundings used to invest in Tech companies. Bangalore, Chennai, Delhi, New Delhi and Prune had more of their fundings used to invest in Tech comapnies.

#### Which top 10 Funding Stages received most fundings? How much of it was used to fund a Tech companies?

```
# Used a stacked barplot to visualize the data
stacked_stages_df_.plot(kind='bar', stacked=True, color=['red', 'skyblue', 'green'], figsize=(8, 80))
plt.title('Investments by Funding stages according to sector class', pad=40)
plt.xlabel('Funding Stage')
plt.ylabel('Amount')
plt.ylim(0, 0.4e11)
plt.show()

```

<img src="dev\images\stackedstages.png" alt="view" >


-From the graph, 9 of the Funding stages had some of their fundings used to fund Tech companies. All the amount in the Debt Financing was used to fund Tech companies. This shows that investor were comfortable paying for debt for Tech companies. Series A, B, C and D, F had all had slightly above 50% of their amount used to fund Tech companies spliy for Tech and Non Tech companies.

## 7. Act

In this phase we give recommendations to our stakeholders, explain the meanings of the findings we have acheived so far and how we can use it to make data driven decisions.

Hypothesis: Based on the questions answered so far we can go on to accept our hypothesis. Companies in the tech industry are mostly funded and also receive higher fundings than the rest (non tech startups).

### 7.1 Recommendations

1. Entrepreneurs who are considering starting a company should consider venturing into Tech. Most the companies that were funded were Tech companies and also they were the same ones that received higher investments.

2. Enterpreneurs should consider headquartering their companies in Mumbai, Bangalore and Gurugram. These cities are in the top three cities by both number of startups and by the sum of fundings generated.

3. During the Pre seed and Seed stage of the startup journey, entrepreneurs should seek fundings from family and friends since it gives them a certain flexibility. Loans from families and friends may be without security or less security than banks. Families and friends may also lend funds interest-free or at a low rate. A company received funding as low as $ 876. This money might come with no interest if given out by a family or friend.

4. Entrepreneurs venturing into startups can consider the following sectors Fintech, Edtech, Healthcare and wellness , Financial services, E-commerce. Entrepreneurs who venture into these sectors might increase their chances of getting funded-not necessarily a huge amount.

## Contact Information <a name="contact"></a>

<table>
  <tr>
    <th>Name</th>
    <th>Twitter</th>
    <th>LinkedIn</th>
    <th>GitHub</th>
    <th>Hugging Face</th>
  </tr>
  <tr>
    <td>Bright Eshun</td>
    <td><a href="https://twitter.com/bright_eshun_">@bright_eshun_</a></td>
    <td><a href="https://www.linkedin.com/in/bright-eshun-9a8a51100/">@brighteshun</a></td>
    <td><a href="https://github.com/Bright136">@bright136</a></td>
    <td><a href="https://huggingface.co/bright1">@bright1</a></td>
  </tr>
</table>