# Microsoft Fabric Stock Market Pipeline

## Introduction

This project involves fetching historical and daily stock data for the top 10 companies in India (by market cap) using the Alpha Vantage API. The data spans from January 1, 2020, to May 31, 2024. The goal is to extract specific columns (Date, Company, Open, Close, High, Low, Volume) and perform certain analyses. The project is divided into two main scripts: one for an initial historical data dump and another for daily updates.

## Requirements

- **API Integration**: Utilize the Alpha Vantage API to fetch stock data.
- **Data Processing**: Clean, transform, and store the data using PySpark.
- **Data Storage**: Efficiently store the data in a format suitable for querying using Delta Lake.
- **Automation**: Automate the daily data update process.
- **Indexing**: Optimize data storage for efficient querying.

## Solution Overview

The solution is implemented using Microsoft Fabric with the Synapse Data Engineering module and Apache Spark with PySpark in the notebooks. Two Jupyter notebooks are used:
1. **RAW to SILVER Layer**: This notebook handles the initial historical data extraction and transformation using PySpark.
2. **Daily Dump Script**: This notebook is scheduled to run daily to fetch and update the previous day's data using PySpark.

## Concepts Used

### 1. Data Extraction
- **API Integration**: Fetch data from the Alpha Vantage API.
- **Libraries Used**: `requests` for API calls, `pandas` for initial data manipulation, `pyspark.sql` for further processing.

### 2. Data Processing
- **Cleaning and Transformation**: Parse and clean the fetched data, extract relevant columns, and convert data types using PySpark.
- **Saving Data**: Save the processed data to CSV files using `pandas`.

### 3. Data Storage and Optimization
- **Schema Definition**: Use PySpark to define and set schemas for the data.
- **File Format Conversion**: Read CSV files and convert them to Parquet format for efficient storage using PySpark.
- **Delta Tables**: Create Delta tables from Parquet files for efficient data management and querying using PySpark.
- **Optimizations**:
  - **Partitioning**: Organize data into partitions for faster reads and writes.
  - **Z-Ordering**: Optimize data layout for faster query performance.
  - **V-Ordering**: Further optimize the layout for even better performance.

### 4. Automation
- **Scheduling**: Automate the daily data update using scheduled tasks (cron jobs).

### 5. Indexing
- **Creating Indexes**: Index data to support efficient querying for:
  - Company-Wise Daily Variation of Prices
  - Company-Wise Daily Volume Change
  - Median Daily Variation

### Why Use Delta Tables?
- **ACID Transactions**: Ensures reliable data processing with Atomicity, Consistency, Isolation, and Durability.
- **Time Travel**: Allows querying previous versions of data.
- **Scalability**: Efficiently handles large datasets.
- **Performance**: Optimized for fast reads and writes with partitioning and indexing.

## Tasks Performed

1. **Historical Dump Script**:
    - Fetch historical data from Alpha Vantage API.
    - Clean and transform the data using PySpark.
    - Save data to CSV files.
    - Convert CSV files to Parquet format using PySpark.
    - Create Delta tables from Parquet files using PySpark.
    - Optimize Delta tables with partitioning, Z-ordering, and V-ordering using PySpark.

2. **Daily Dump Script**:
    - Fetch the previous day's data from Alpha Vantage API.
    - Clean and transform the data using PySpark.
    - Append the new data to the Delta tables using PySpark.
    - Update Delta tables for daily variations and volume changes using PySpark.

## Deliverables

1. **Jupyter Notebooks**:
    - **RAW to SILVER Layer**: Handles the initial historical data extraction and transformation using PySpark.
    - **Daily Dump Script**: Handles daily data updates using PySpark.

2. **SQL DB/DW Credentials**:
    - Connection details for the SQL Data Warehouse for data storage and querying.

3. **Indexed Delta Tables**:
    - Delta tables optimized for the following regular queries:
        1. Company-Wise Daily Variation of Prices
        2. Company-Wise Daily Volume Change
        3. Median Daily Variation

## Achievements

The implementation successfully automates the extraction, transformation, and loading (ETL) process for historical and daily stock data. The data is stored in a structured format in Delta Lake tables, enabling efficient querying and analysis. The use of Microsoft Fabric and the Synapse Data Engineering module ensures a scalable and maintainable solution.

## Conclusion

This project demonstrates a robust solution for automated stock data collection and analysis. By leveraging API integration, data engineering with PySpark, and scheduling, the process is streamlined and efficient. The indexing ensures that regular queries can be executed swiftly, providing valuable insights into stock price and volume variations.

