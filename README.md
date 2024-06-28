# Credit_card_Financial_dashboard
Developed a comprehensive credit card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.
Convert the csv file(customer.csv, credit_card.csv) into a SQL database and import the dataset into the power BI application.
design the dashboard according to your requirements for efficient analysis of the dataset.
their are addtional files(cc_add, cust_add), these files are add-ons to the main dataset and I uploaded them for future analysis.
after creating the dashboard, you can use the additional files to add its data into the dashboard.
import the files into the sql database(table) and refresh the dashboard your new data will be added. In organizations, employees use various pipelines for importing new data and refresh their data.
Below is the SQL statements to convert the csv files into SQL database.

-- SQL Query to create and import data from csv files:

-- 0. Create a database 
CREATE DATABASE ccdb;

-- 1. Create cc_detail table

CREATE TABLE cc_detail (
    Client_Num INT,
    Card_Category VARCHAR(20),
    Annual_Fees INT,
    Activation_30_Days INT,
    Customer_Acq_Cost INT,
    Week_Start_Date DATE,
    Week_Num VARCHAR(20),
    Qtr VARCHAR(10),
    current_year INT,
    Credit_Limit DECIMAL(10,2),
    Total_Revolving_Bal INT,
    Total_Trans_Amt INT,
    Total_Trans_Ct INT,
    Avg_Utilization_Ratio DECIMAL(10,3),
    Use_Chip VARCHAR(10),
    Exp_Type VARCHAR(50),
    Interest_Earned DECIMAL(10,3),
    Delinquent_Acc VARCHAR(5)
);


-- 2. Create cc_detail table

CREATE TABLE cust_detail (
    Client_Num INT,
    Customer_Age INT,
    Gender VARCHAR(5),
    Dependent_Count INT,
    Education_Level VARCHAR(50),
    Marital_Status VARCHAR(20),
    State_cd VARCHAR(50),
    Zipcode VARCHAR(20),
    Car_Owner VARCHAR(5),
    House_Owner VARCHAR(5),
    Personal_Loan VARCHAR(5),
    Contact VARCHAR(50),
    Customer_Job VARCHAR(50),
    Income INT,
    Cust_Satisfaction_Score INT
);


-- 3. Copy csv data into SQL (remember to update the file name and file location in below query)

-- copy cc_detail table

COPY cc_detail
FROM 'D:\credit_card.csv' 
DELIMITER ',' 
CSV HEADER;


-- copy cust_detail table

COPY cust_detail
FROM 'D:\customer.csv' 
DELIMITER ',' 
CSV HEADER;



-- If you are getting below error, then use the below point:  
   -- ERROR:  date/time field value out of range: "0"
   -- HINT:  Perhaps you need a different "datestyle" setting.

-- Check the Data in Your CSV File: Ensure date column values are formatted correctly and are in a valid format that PostgreSQL can recognize (e.g., YYYY-MM-DD). And correct any incorrect or missing date values in the CSV file. 
   -- or
-- Update the Datestyle Setting: Set the datestyle explicitly for your session using the following command:
SET datestyle TO 'ISO, DMY';

-- Now, try to COPY the csv files!


-- 4. Insert additional data into SQL, using same COPY function

-- copy additional data (week-53) in cc_detail table

COPY cc_detail
FROM 'D:\cc_add.csv' 
DELIMITER ',' 
CSV HEADER;


-- copy additional data (week-53) in cust_detail table (remember to update the file name and file location in below query)

COPY cust_detail
FROM 'D:\cust_add.csv' 
DELIMITER ',' 
CSV HEADER;






Data Insights:
Week on week change:
•
Revenue increased by 28.8%,
•
Total Transaction Amt & Count increased by xx% & xx%
•
Customer count increased by xx%
Overview YTD:
•
Overall revenue is 57M
•
Total interest is 8M
•
Total transaction amount is 46M
•
Male customers are contributing more in revenue 31M, female 26M
•
Blue & Silver credit card are contributing to 93% of overall transactions
•
TX, NY & CA is contributing to 68%
•
Overall Activation rate is 57.5%
•
Overall Delinquent rate is 6.06%


