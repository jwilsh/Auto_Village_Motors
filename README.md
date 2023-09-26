# Auto_Village_Motors
Portfolio Project - This is a project which follows a 2nd Hand Car Dealership looking into their own data which has been collected about the vehicles that have passed through their business.

# Scenario
Auto Village Motors is a 2nd hand car dealership in Manchester UK. Their performance over recent years has dropped drastically. They have lots of competition from other local car dealerships in the area and the arrival of a new dealership on the same street means that the business owner Clive has been looking into ways in which he can improve his business. He wants to look into the companies past data to look for any potential ways to improve company performance.

# 1.0 Ask

### 1.1 Business Task:
Use the internal data provided by Auto Village Motors to gain insights into the vehicles that the company has sold in previous years. Use these insights to help guide some new strategies for the company.

### 1.2 Business Objectives:
- How many cars will be available in 2023?
- How many cars will be available in 2020, 2021, 2022?
- Show the total number of cars by year.
- How many diesel cars were there in 2020?
- How many petrol cars were there in 2020?
- Which years had more than 100 cars?
- Complete list of all car details between 2015 and 2023.

### 1.3 Deliverables:
- A clear summary of the business task
- A description of all data sources used
- Documentation of any cleaning or manipulation of data
- A summary of your analysis
- Supporting visualizations and key findings
- Your top high-level content recommendations based on your analysis

### 1.4 Key Stakeholders:
- **Clive Warren:** Auto Village Motors owner and founder
- **Auto Village Motors Sales team:** A team of sales representatives which dictate the companies sales.

# 2.0 Prepare

### 2.1 Information on Data Source:
- Data has been provided by the company owner with his permission to use and share it. The data is stored on a .csv file.
- The data has been stored manually by employees between 1994 and 2023.
- Data collected includes information about the vehicles sold such as the model, price, milage and fuel type.

### 2.2 Limitations of Data Set:
- The dataset doesn't have a primary key so there is no way of recognising each row as a unique entry.
- As data is collected by employees and entered manually, its difficult to calculate the amount of human error within the data.
- The data only includes information about the sale price and not the buy price which will limit the amount of calculations that can be made.

### 2.3 Is Data ROCCC?

Reliable — LOW — Data was entered manually by employees

Original — HIGH — Original Company Internal Data

Comprehensive — MED — All important information about the vehicles are included.

Current — HIGH — Data has been collected from the opening of the business until now.

Cited — LOW — Companies own internal data.


### 2.4 Data Selection
The following file has been provided and will be used for all analysis.

car_dekho.csv

### 2.5 Tool
We are using SQL and MySQL for data cleaning and transformation. Tableau is being used for the visualizations.

# 3.0 Process

### 3.1 Setting-Up the Environment
A new schema is created with MySQL called 'cars'.
```
CREATE SCHEMA 'cars';
```

### 3.2 Importing the Dataset
The .cvs files from earlier were uploaded onto this newly created dataset.

### 3.3 Preview the Data and it's Structure
The .cvs files from earlier were uploaded onto this newly created dataset. Here you can see a preview of the dataset.

![Preview 1](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/8a28f246-4960-416f-8d15-5ff37579dfba)

You can check the details of the data here

![Preview 2](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/f5ffbe58-66e7-42e5-be79-c26759750cc5)

The data contains 7927 entries.
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

FROM car_dekho

WHERE * is null;
```

### 3.3.2 Check If Correct Data Types are Applied
- The dataset contains no primary key so the first step is to create one.
- Several columns such as the sale price, mileage and engine size are labeled with the 'text' data type. They will be changed to 'integer' data type instead.

### 3.4 Data Manipulation & Transformation
After checking for dirty data it's now time for some data manipulation to get it ready for some analysis. Below are the steps I took in order to transform the data ready to create some visualizations with.

- Create primary key

- Change data types of several columns such as sale price, milage, engine size.

- Rearrange and rename columns.

```
--  Add new Column for Primary Key --
SELECT *,
ROW_NUMBER() OVER (ORDER BY year, Name) AS ID
FROM car_dekho
ORDER BY year, Name;

-- Set column as Primary Key --
ALTER TABLE car_dekho ADD PRIMARY KEY (ID);

-- rearrange columns so that primary key is on the far left --
ALTER TABLE car_dekho
MODIFY COLUMN ID TEXT FIRST;
```

# 4.0 Analyze

### 4.1 Answering Business Questions

Using the cleaned and transformed data, we will now answer the business questions asked by the company owner.


- How many cars will be available in 2023?
```
SELECT COUNT(*)

FROM car_dekho

WHERE year = 2023;
```
6 cars were available in the dealership in 2023.


- How many cars will be available in 2020, 2021, 2022?
```
SELECT 
(SELECT COUNT(*) FROM car_dekho WHERE year = 2020) AS '2020',
(SELECT COUNT(*) FROM car_dekho WHERE year = 2021) AS '2021',
(SELECT COUNT(*) FROM car_dekho WHERE year = 2022) AS '2022'
FROM car_dekho
LIMIT 1;
```
74 cars were available in the dealership in 2020, 7 in 2021 and 7 in 2022.


- Show the total number of cars by year from 2015-2023.
```
SELECT year, COUNT(*) AS Total_Cars 

FROM car_dekho 

WHERE year IN(2015, 2016, 2017, 2018, 2019, 2020, 2021, 2022, 2023) 

GROUP BY year;
```

![table 1](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/9fa4db6b-6634-43c0-9c24-92b1112189f9)


- How many diesel cars were there in 2020?
```
SELECT COUNT(*) 

FROM car_dekho 

WHERE year = 2020 AND fuel = 'Diesel';
```

20 cars were Diesel in 2020.


- How many petrol cars were there in 2020?
```
SELECT COUNT(*) 

FROM car_dekho 

WHERE year = 2020 AND fuel = 'Petrol';
```

20 cars were Diesel in 2020.


- Which years had more than 100 cars?
```
SELECT year, COUNT(*) AS 'Quantity'

FROM car_dekho 

GROUP BY year

HAVING COUNT(*) > 100;
```

![table 2](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/872ae682-17b2-48ce-8a3c-2df5c3d23815)

14 years had a total of more than 100 cars.


- How many cars were at the dealership between 2015 and 2023.
```
SELECT COUNT(*)

FROM car_dekho 

WHERE year BETWEEN 2015 AND 2023;
```

4124 cars were at the dealership between 2015 and 2023.

# 5.0 Share
After exploring and analyzing the data we were able to answer the questions asked by the business owner. In this section we will share some of the insights that we have gained whilst working with the dataset.

The .csv files from MySQL have been uploaded into Tableau ready to create some visualizations.

![Chart 1](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/a032858b-1afc-4c87-b6d8-b17adeff9a5c)

This first chart shows the total number of cars sold each year. The graph demonstrates that the company was expanding and performing gradually better each year from when it started right up until 2017. This shows that the difference in how the company was run prior to 2017 and afterwards has had a significant impact on how the company has been performing. This is something that the owner will need to look into.

![Chart 2](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/6dfb2332-6448-4c4b-87fb-196b1de49699)

The next graph shows the gross profit from car sales each year. From this visualization we can see that it also exponentially improves over time  but this time right up until 2018 before having a sharp decline ever since.

![Chart 3](https://github.com/jwilsh/Auto_Village_Motors/assets/98908958/8d87f508-9196-411e-9ce7-76a441052c39)

This comparison chart shows how the 2 different graphs correlate with each other since selling more cars will generally mean more gross profit. However as we can see from the 2017 to 2018 period, it is possible to sell less cars and still make more profit if more expensive cars are sold at a higher selling price.

# 6.0 Act
Conclusions after working with this dataset:
- Between 2009-2017 was when the company performed at its best. The company needs to review how their business operated during this period and compare it to now and see what has changed.
- Selling more expensive cars for a higher profit margin is the best way to improve overall profit. The sales team should focus on this instead of trying to sell a large amount of cheaper cars.
- Petrol cars bring in the most profit for the company, the sales team should focus mainly on trying to sell petrol vehicles.
