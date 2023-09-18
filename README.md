# Auto_Village_Motors
Portfolio Project - 2nd Hand Car Dealership

# Scenario
Bellabeat is a high-tech manufacturer of health-focused products specifically for women. Bellabeqat is a successful small company, however they have a vision of becoming one of the major players in the global smart device market. The Co-founder of Bellabeat Urška Sršen, beleives that by analysing smart device fitness data can help unlock new growth opportunities for the company. 

We will be looking at data from an existing dataset [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit) to determine if there are any trends that we can identify. These insights will then be used to give high level recommendations to guide the marketing strategy for the company.

# 1.0 Ask

### 1.1 Business Task:
Use the data provided in the [FitBit Fitness Tracker Data](https://www.kaggle.com/datasets/arashnic/fitbit) dataset to gain insights into how people use non-Bellabeat smart devices. Use these insights to help guide the marketing strategy for the company.

### 1.2 Business Objectives:
- What are some trends in smart device usage?
- How could these trends apply to Bellabeat customers?
- How could these trends help influence Bellabeat marketing strategy?

### 1.3 Deliverables:
- A clear summary of the business task
- A description of all data sources used
- Documentation of any cleaning or manipulation of data
- A summary of your analysis
- Supporting visualizations and key findings
- Your top high-level content recommendations based on your analysis

### 1.4 Key Stakeholders:
- **Urška Sršen:** Bellabeat’s cofounder and Chief Creative Officer
- **Sando Mur:** Mathematician and Bellabeat’s cofounder; key member of the Bellabeat executive team
- **Bellabeat marketing analytics team:** A team of data analysts responsible for collecting, analyzing, and
reporting data that helps guide Bellabeat’s marketing strategy.

### Products:
- **Bellabeat app:** The Bellabeat app provides users with health data related to their activity, sleep, stress,
menstrual cycle, and mindfulness habits. This data can help users better understand their current habits
and make healthy decisions. The Bellabeat app connects to their line of smart wellness products.
- **Leaf:** Bellabeat’s classic wellness tracker can be worn as a bracelet, necklace, or clip. The Leaf tracker connects
to the Bellabeat app to track activity, sleep, and stress.
- **Time:** This wellness watch combines the timeless look of a classic timepiece with smart technology to track user
activity, sleep, and stress. The Time watch connects to the Bellabeat app to provide you with insights into your
daily wellness.
- **Spring:** This is a water bottle that tracks daily water intake using smart technology to ensure that you are
appropriately hydrated throughout the day. The Spring bottle connects to the Bellabeat app to track
your hydration levels.
- **Bellabeat membership:** Bellabeat also offers a subscription-based membership program for users.
Membership gives users 24/7 access to fully personalized guidance on nutrition, activity, sleep, health
and beauty, and mindfulness based on their lifestyle and goals.

# 2.0 Prepare

### 2.1 Information on Data Source:
- Data is publicly available on Kaggle: FitBit Fitness Tracker Data and stored in 18 csv files.
- Generated by respondents from a survey via Amazon Mechanical Turk between 12 March 2016 to 12 May 2016.
- 30 FitBit users consented to the submission of personal tracker data.
- Data collected includes physical activity recorded in minutes, heart rate, sleep monitoring, daily activity and steps.

### 2.2 Limitations of Data Set:
- Data is collected 5 years ago in 2016. Users’ daily activity, fitness and sleeping habits, diet and food consumption may have changed since then. Data may not be timely or relevant.
- Sample size of 30 FitBit users is not representative of the entire fitness population. The central limit theorem general rule of n≥30 applies and we can use the t test for statstic reference. However, a larger sample size is preferred for the analysis.
- As data is collected in a survey, we are unable to ascertain its integrity or accuracy.
- After further investigation with n_distinct() to check for unique user Id, the set has 33 user data from daily activity, 24 from sleep and only 8 from weight. There are 3 extra users and some users did not record their data for tracking daily activity and sleep.
- For the 8 user data for weight, 5 users manually entered their weight and 3 recorded via a connected wifi device (eg: wifi scale).
- Most data is recorded from Tuesday to Thursday, which may not be comprehensive enough to form an accurate analysis.

### 2.3 Is Data ROCCC?
A good data source is ROCCC which stands for Reliable, Original, Comprehensive, Current, and Cited.

Reliable — LOW — Not reliable as it only has 30 respondents

Original — LOW — Third party provider (Amazon Mechanical Turk)

Comprehensive — MED — Parameters match most of Bellabeat products’ parameters

Current — LOW — Data is 5 years old and may not be relevant

Cited — LOW — Data collected from third party, hence unknown

Overall, the dataset is considered bad quality data and it is not recommended to produce business recommendations based on this data.

### 2.4 Data Selection
The following file is selected and copied for analysis.

dailyActivity_merged.csv

### 2.5 Tool
We are using BigQuery in Google Cloud for data cleaning and transformation. Tableau is being used for the visualisations.

# 3.0 Process

### 3.1 Setting-Up the Environement
A new project is created withtin BigQuery whith a relevent title for the project 'bellebeat-capstone-case-study'. We then created a new dataset within the project with the title 'FitBit_Fitness_Tracker_Data
'.

![Preparing the Environement](https://github.com/jwilsh/Bellabeat_Case_Study/assets/98908958/0e7d8993-7c6e-4e1e-a5a2-45e072718bcd)

### 3.2 Importing the Dataset
The .cvs files from ealrier were uploaded onto this newly created dataset.

### 3.2 Preview the Data and it's Structure
The .cvs files from ealrier were uploaded onto this newly created dataset. Here you can see a preview of the dataset.

![Data Preview 2](https://github.com/jwilsh/Bellabeat_Case_Study/assets/98908958/dae534ce-65a4-4257-bb4a-d56fbeb27647)

You can check the structure of the data in the 'schema' tab.

![Data Preview 1](https://github.com/jwilsh/Bellabeat_Case_Study/assets/98908958/e430154c-bc89-4460-842f-597fe0466dd2)

Information of the data including how many rows it contains in the 'Details' tab.

![Data Preview 3](https://github.com/jwilsh/Bellabeat_Case_Study/assets/98908958/b0af7b7e-3296-43e3-a8c0-0f101db2e3ed)

### 3.3 Data Cleaning and Manipulation
Now that we are familiar with the structure of the data we can clean the data by checking for any errors.

### 3.3.1 Check the number of participants for each data set
Its important to check that the same amount of participants have participated in all of our datasets.
```
SELECT COUNT(distinct Id)
 FROM `bellebeat-capstone-case-study.FitBit_Fitness_Tracker_Data.dailyActivity`
```



### 3.3.2 Check Data for null or Missing Values
All columns were checked for Null data or missing values. However none were found.

```
SELECT Id

FROM `bellebeat-capstone-case-study.FitBit_Fitness_Tracker_Data.dailyActivity` 

WHERE Id is null
```


### 3.3.2 Check If Correct Datatypes are Applied
Luckily all of the collumns have the correct data type applied so there will be no need to chnage these.

### 3.4 Data Manipulation & Transformation
After checking for dirty data its now time for some data manipultion to get it ready for some analysis. Below are the steps I took in order to transform the data ready to create some visualisations with.

- Create new column DayOfTheWeek by generating date in the form of day of the week for further analysis.

- Create new column TotalMinutes being the sum of VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes and SedentaryMinutes.

- Create new column TotalHours by converting new column TotalMinutes to number of hours.

- Rearrange and rename columns.

```
ALTER TABLE `bellebeat-capstone-case-study.FitBit_Fitness_Tracker_Data.dailyActivity` 
ADD COLUMN DayOfTheWeek DATE;
```

# 4.0 Analyse

# 5.0 Share

# 6.0 Act
