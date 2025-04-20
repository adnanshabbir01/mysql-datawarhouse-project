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
 
