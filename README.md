# MySQL Datawarehouse Project
This is a data engineering project focused on building a modern data warehouse using MySQL. I'm consolidating Excel exports from our CRM and ERP systems into a structured MySQL database. The goal is to transform scattered operational data into a centralized, queryable format to support reporting, analysis, and data-driven decision-making.

This project involves setting up and managing a sample CRM and ERP system using MySQL. We created six relational tables distributed across two schemas (crm and erp) using simple CREATE TABLE commands.

🗂️ Schemas and Tables
CRM Schema (crm):
cust_info – Stores customer information.

prd_info – Stores product details.

sales_details – Stores information about customer purchases and sales transactions.

ERP Schema (erp):
cust_az12 – Extended customer information used for ERP operations.

loca101 – Location-related data, such as branches or warehouses.

px_cat_g1v2 – Product category and classification details.
