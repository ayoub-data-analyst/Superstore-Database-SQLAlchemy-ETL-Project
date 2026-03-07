🗄 Superstore Data Warehouse & Analytics
📌 Project Overview

This project transforms the Superstore CSV dataset into a normalized PostgreSQL database and prepares the data for analytical queries and business intelligence.

The workflow follows a complete ETL process:

Extract data from CSV

Transform and normalize the dataset

Load the data into PostgreSQL

Create analytical SQL views for reporting and dashboarding

The final database structure enables efficient analysis of sales performance, profitability, and regional trends.

⚙️ Technologies Used

Python

Pandas

SQLAlchemy

PostgreSQL

SQL

Jupyter Notebook

🔄 Project Workflow
1️⃣ Database Creation

A PostgreSQL database named superstore_db was created to store structured sales data.

Python was connected to PostgreSQL using SQLAlchemy to execute queries and load data.

2️⃣ Data Modeling & Normalization

The original dataset contained all information in a single table.

The data was transformed into a normalized relational schema including the following tables:

Locations

Customers

Products

Orders

Order Details

Primary and foreign keys were defined to maintain relationships and ensure data integrity.

The schema follows 1NF, 2NF, and 3NF normalization rules to reduce redundancy.

3️⃣ ETL Data Loading

The dataset was split into multiple tables using Pandas.

Data preparation included:

Removing duplicates

Renaming columns

Fixing data types

Creating clean datasets for each table

The cleaned data was then loaded into PostgreSQL.

4️⃣ Analytical SQL Transformations

Several analytical SQL views were created directly in the database to simplify analysis.

These views generate key business metrics such as:

Total Sales per Product

Total Sales per Category

Total Sales per Region

Average Profit per Customer

Using views allows BI tools to query aggregated data efficiently.

📊 Business Metrics Generated

The database supports analysis of:

Sales performance by product

Category-level revenue

Regional sales distribution

Customer profitability

These metrics are essential for business decision-making and dashboard reporting.

📂 Project Structure
superstore-data-warehouse
│
├── data
│   └── superstore.csv
│
├── etl
│   └── etl_pipeline.ipynb
│
├── sql
│   └── views.sql
│
├── docs
│   └── project_documentation.pdf
│
└── README.md
🎯 Project Objective

The objective of this project is to demonstrate how raw transactional data can be transformed into a structured analytical database that supports reporting, analytics, and business intelligence tools such as Power BI.

🚀 Future Improvements

Possible improvements for the project include:

Building an interactive Power BI dashboard

Automating the ETL pipeline

Adding more advanced analytical queries

Creating a star schema for data warehousing
