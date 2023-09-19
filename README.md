# Auto_Village_Motors
Portfolio Project - This is a project which follows a 2nd Hand Car Dealership looking into their own data which has been collected about the vehicles that have passed through their business.

# Scenario
Auto Village Motors are a 2nd hand car dealership in Manchester UK. They have lots of competition from other local car dealerships in the area and the arrival of a new deaership on the same street means that the business owner Clive has been looking into ways which he can improve his busniess. He wants to look into the companies past data to look for any potential ways to improve company performance.

# 1.0 Ask

### 1.1 Business Task:
Use the internal data provided by Auto Village Motors to gain insights into the vehicles that the company has sold in previous years. Use these insights to help guide some new strategies for the company.

### 1.2 Business Objectives:
- 
- 
- 
- 
- 
- 

### 1.3 Deliverables:
- A clear summary of the business task
- A description of all data sources used
- Documentation of any cleaning or manipulation of data
- A summary of your analysis
- Supporting visualizations and key findings
- Your top high-level content recommendations based on your analysis

### 1.4 Key Stakeholders:
- **Clive Warren:** Auto Village Motor's owner and founder
- **Auto Village Motors Sales team:** A team of sales representaties which dictate the companies sales.

# 2.0 Prepare

### 2.1 Information on Data Source:
- Data has been provided by the company owner with his permission to use and share it. The data is stored on a .csv file.
- The data has been stored manually by employees between 2017 and 2023.
- Data collected includes information about the vehicles sold such as the model, price, milage and fuel type.

### 2.2 Limitations of Data Set:
- The dataset doesn't have a primary key so there is no way of recognising each row as a unique entry.
- As data is collected by employees and entered manually, its difficult to calculate the amount of human error within the data.
- The data only includes information about the sale price and not the buy price which will limit the amount of calculations that can be made.

### 2.3 Is Data ROCCC?

Reliable — LOW — Data was entered manually by employees

Original — HIGH — Origional Company Internal Data

Comprehensive — MED — All important information about the vehicles are included.

Current — HIGH — Data has been collected from the opening of the busniess until now.

Cited — LOW — Companies own internal data.


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
