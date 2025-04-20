# MySQL Datawarehouse Project
This is a data engineering project focused on building a modern data warehouse using MySQL. I'm consolidating Excel exports from our CRM and ERP systems into a structured MySQL database. The goal is to transform scattered operational data into a centralized, queryable format to support reporting, analysis, and data-driven decision-making.

This project involves setting up and managing a sample CRM and ERP system using MySQL. We created six relational tables distributed across two schemas (crm and erp) using simple CREATE TABLE commands.

🗂️ Schemas and Tables

CRM Schema (crm)
1. cust_info – Contains customer information.
2. prd_info – Contains product details.
3. sales_details – Contains sales transactions and customer purchase data.

ERP Schema (erp)
1. cust_az12 – Stores extended customer information for ERP processes.
2. loca101 – Stores location-specific data (e.g., branches, warehouses).
3. px_cat_g1v2 – Stores product category and classification information.
 
Bronze Table: bronze.crm_cust_info
The bronze table stores raw CSV data. All fields are imported as VARCHAR(50) to ensure flexibility during the initial data load.

Schema:
Column Name	Data Type
cst_id	VARCHAR(50)
cst_key	VARCHAR(50)
cst_firstname	VARCHAR(50)
cst_lastname	VARCHAR(50)
cst_marital_status	VARCHAR(50)
cst_gndr	VARCHAR(50)
cst_create_date	VARCHAR(50)

We use the LOAD DATA INFILE command to load cust_info.csv into the bronze table.

LOAD DATA INFILE 'C:/ProgramData/MySQL/MySQL Server 8.0/Uploads/cust_info.csv'
INTO TABLE bronze.crm_cust_info
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 LINES
(
  cst_id,
  cst_key,
  cst_firstname,
  cst_lastname,
  cst_marital_status,
  cst_gndr,
  @cst_create_date
)
SET
  cst_id             = NULLIF(cst_id, ''),
  cst_key            = NULLIF(cst_key, ''),
  cst_firstname      = NULLIF(cst_firstname, ''),
  cst_lastname       = NULLIF(cst_lastname, ''),
  cst_marital_status = NULLIF(cst_marital_status, ''),
  cst_gndr           = NULLIF(cst_gndr, ''),
  cst_create_date    = NULLIF(
                         TRIM(REPLACE(@cst_create_date, '"', '')),
                         ''
                       );
