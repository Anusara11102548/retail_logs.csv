# Retail Store ETL Pipeline

## Project Overview

This project demonstrates an ETL (Extract, Transform, Load) process for converting retail sales logs into a Data Warehouse using a Star Schema. The data is extracted from a CSV file, transformed into one Fact Table and three Dimension Tables, and loaded into a SQLite database.

---

## Objective

- Design a Star Schema
- Create 1 Fact Table (Fact_Sales)
- Create 3 Dimension Tables
  - Dim_Location
  - Dim_Product
  - Dim_Date
- Implement an ETL pipeline using Python
- Store the processed data in SQLite

---

## Dataset

**Input File**

```
retail_logs.csv
```

The dataset contains:

- Sale ID
- Store Code
- Branch
- Province
- Region
- Product Name
- Category
- Sale Date
- Quantity
- Unit Price
- Discount Percent

---

## Star Schema

```
                  Dim_Location
                        |
                        |
Dim_Product ------ Fact_Sales ------ Dim_Date
```

### Fact Table

**Fact_Sales**

| Column |
|---------|
| Sales_Key |
| Sale_ID |
| Date_Key |
| Product_Key |
| Location_Key |
| Quantity |
| Unit_Price |
| Discount_Percent |
| Total_Sales |

---

### Dimension Tables

#### Dim_Location

- Location_Key
- Store_Code
- Branch
- Province
- Region

#### Dim_Product

- Product_Key
- Product_Name
- Category

#### Dim_Date

- Date_Key
- Sale_Date
- Day
- Month
- Year

---

## ETL Process

### Extract

Read data from

```
retail_logs.csv
```

### Transform

- Convert mixed date formats
- Calculate Total Sales
- Remove duplicate dimension records
- Generate surrogate keys
- Build Fact Table

Formula

```
Total_Sales =
Quantity × Unit_Price × (1 - Discount_Percent / 100)
```

### Load

Load all tables into

```
retail_warehouse.db
```

---

## Technologies Used

- Python 3
- Pandas
- SQLite

---

## Project Structure

```
Retail-ETL/
│
├── retail_logs.csv
├── etl_pipeline.py
├── retail_warehouse.db
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Installation

Install the required package

```bash
pip install pandas
```

---

## Run the Project

```bash
python etl_pipeline.py
```

---

## Output

The script generates

```
retail_warehouse.db
```

Database Tables

- Fact_Sales
- Dim_Location
- Dim_Product
- Dim_Date

---

## Example Result

```
========== ETL SUCCESS ==========
Database : retail_warehouse.db
---------------------------------
Dim_Location : 77
Dim_Product  : 69
Dim_Date     : 113
Fact_Sales   : 325
=================================
```

---

## Author

Anusara Klamsawat

Burapha University
