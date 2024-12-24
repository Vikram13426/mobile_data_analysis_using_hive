 **Mobile Data Analysis Using Hive & R**

This project leverages Big Data tools like Hive and R programming to analyze mobile phone market trends. It focuses on product features, pricing structures, and brand performance. The dataset was extracted from a MySQL database, loaded into Hive for querying, and insights were visualized using R.

 **Features**
- Analyzes key attributes like pricing, 5G adoption, and battery capacity.
- Uses Hive Query Language (HQL) for efficient querying of large datasets.
- Provides actionable insights through R-based data visualizations.

**Prerequisites**
1. **Hive:** Ensure Hive is installed and configured on your system.
2.** R Programming:** Install R and required libraries (e.g., `ggplot2`).
3. **MySQL:** Ensure the database containing the mobile data is accessible.
4. **Java:** Install Java as Hive depends on it.

**Import the dataset into MySQL:**

mysql -u <username> -p < database_name> < dataset.sql


**Load the dataset into Hive:**



CREATE DATABASE mobile_data_analysis;
USE mobile_data_analysis;
CREATE TABLE mobile_data (
    Phone_Name STRING,
    Brand STRING,
    Price FLOAT,
    Country_Of_Origin STRING,
    Operating_System_Type STRING,
    RAM_Storage INT,
    Battery_Capacity INT,
    FiveG_Availability STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

LOAD DATA INPATH '<path_to_csv>' INTO TABLE mobile_data;


**Execute Hive queries for analysis:**


SELECT Operating_System_Type, AVG(Price) AS avg_price
FROM mobile_data
WHERE Operating_System_Type IN ('Android', 'iOS')
GROUP BY Operating_System_Type;
