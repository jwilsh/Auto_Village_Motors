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
The following file has been provided and will be ued for all analysis.

car_dekho.csv

### 2.5 Tool
We are using SQL and MySQL for data cleaning and transformation. Tableau is being used for the visualisations.

# 3.0 Process

### 3.1 Setting-Up the Environement
A new schema is created with MySQL called 'cars'.
```
NEW SCHEMA 'cars';
```

### 3.2 Importing the Dataset
The .cvs files from ealrier were uploaded onto this newly created dataset.

### 3.3 Preview the Data and it's Structure
The .cvs files from ealrier were uploaded onto this newly created dataset. Here you can see a preview of the dataset.

![Preview 1]()

You can check the details of the data here

![Preview 2]()

The data contains 7927 entires.
```
SELECT COUNT(*) AS total_entries
 FROM car_dekho;
```

### 3.3 Data Cleaning and Manipulation
Now that we are familiar with the structure of the data we can clean the data by checking for any errors.

### 3.3.1 Check Data for null or Missing Values
All columns were checked for Null data or missing values. However none were found.
```
SELECT *

FROM Data_cars

WHERE * is null
```

### 3.3.2 Check If Correct Datatypes are Applied
- The dataset contains no primary key so the first step is to create one.
- Several columns such as the sale price, milage and engine size are labbeled with the 'text' datatype. They will be changed to 'integer' datatype instead.

### 3.4 Data Manipulation & Transformation
After checking for dirty data its now time for some data manipultion to get it ready for some analysis. Below are the steps I took in order to transform the data ready to create some visualisations with.

- Create primary key

- Change datatypes of several columns such as sale price, milage, engine size.

- Rearrange and rename columns.

```
ALTER TABLE `bellebeat-capstone-case-study.FitBit_Fitness_Tracker_Data.dailyActivity` 
ADD COLUMN DayOfTheWeek DATE;
```

# 4.0 Analyse

# 5.0 Share

# 6.0 Act
