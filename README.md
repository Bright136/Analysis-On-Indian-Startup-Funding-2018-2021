# 🚀 The Indian Startup Funnding Analysis 2018 -2021 🚀
[![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
## Bright Ofori Boye Eshun


### Azubi Data Analytics Trainee Program

Git-hub repository at:
https://github.com/Bright136/Analysis-On-Indian-Startup-Funding-2018-2021

- Jupyter notebook: **Indian Startup Funding.ipynb**
- data set: .csv

![Bike Rental](images/startup.png)

# Table of contents
1. [Introduction](#introduction)

2. [Ask](#ask)

3. [Prepare Data](#prepare)
    1. [Initial steps ](#sec3p1)
    2. [Feature Engineering](#sec3p2)
    3. [Descriptive statistics and Correlation](#sec3p3)



## 1. Introduction <a name="introduction"></a>
This project as worked on as group while enrolled in the Azubi Data Analytics Trainee program. The project is to allow students to showcase their knowledge and skills acquired so far in the program. The data to be used is the Indian startup data from 2018 to 2021. The data source is not known. This article will take us through Ask, Prepare, Process, Analyze, Share and Act phase.

##  2. Ask <a name="ask"></a>
In this phase we define the business objective, define our hypothesis and raise questions to support or reject out hypothesis.

###  2.1 Business Task
The business task was to analyze an Indian startup data to gain insights answer to influence the decisions of startup companies.
###  2.2 Hypothesis:
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

This data set includes information about individual rides made in a bike-sharing system covering the greater San Francisco Bay area stored in 201902-fordgobike-tripdata.csv file. The idividuals have been group by gender(male, female and other) and by the type of users they are, whether subcribers or customers. They birth year of the individuals were also given, hence we can go to calculate for their ages since the year at the time was 2019. The data contains 183412 rows and 16 columns


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
(?sample codes))

###  4.3 Data Cleaning and Manupulation
- The according to the ecomonicttimes.indiatimes.com, an economic survey showed that from 2020-2021 the government of India recognised 41, 061 start-ups. This goes on to prove the most start -ups didn’t appear in the data.
- The 2019 start-ups data had 2 missing columns compared to the 2019, 2020 and 2021 datasets.


After previewing the data the following observations were made:
-
Now that we have noticed some of the issues with our data we can perform data cleaning and transformation.
-
-

##  5. Analyze <a name="analyze"></a>