# BM_finance_project
PROJECT DOCUMENTATION:-
-------------------------------------------------------------------------------------------------------------------------
👨‍💻 Developed by: Rajesh Kumar Rout
 Platform: Microsoft Fabric
 Tools & Technologies: PySpark, Delta Lake, Lakehouse, Data Warehouse, Power BI
________________________________________
 Project Overview
This project focuses on analyzing financial data for a banking system to generate actionable insights regarding:
•	 Transaction trends
•	Customer spending behavior
•	 Risk assessment
The data flows from raw ingestion to a gold layer star schema, and finally into a Power BI dashboard, via Microsoft Fabric Lakehouse and Warehouse.
________________________________________
Architecture Overview
Importing data into MSSQL-
•	Imported data from three Excel files into a Microsoft SQL Server database in tabular format.

Bronze layer- 
•	Connected on-premises SQL Server to Microsoft Fabric using the On-premises Data Gateway, enabling secure and reliable data transfer without exposing the source directly.
•	Configured the data pipeline to ingest data into the Bronze layer of a Fabric Lakehouse, ensuring the raw data was stored efficiently for further transformation.
•	Utilized OneLake storage to manage the ingested data centrally, setting the stage for building a structured multi-layered data architecture.

 Silver Layer(using pyspark notebook):
•	Cleaned data stored in Delta format tables.
•	Perform operations like Drop duplicates, fill the null values
•	Tables: customer_data, transaction_data, bank_data.

⭐ Gold Layer (Star Schema):
        Built using PySpark with the following structure:
       Apply Bussiness logic to transform silver layer data to gold layer (BI consumable data) 
       <img src="image/Screenshot (31).png" alt="Dashboard" width="900"/>

Dimension Tables:
•	bankbranch_table: Customer details (Customer_ID, Age, Region, etc.)
•	customer_table: Bank branch financials (Branch_ID, Revenue, Profit, etc.)
•	datedata_table: Date-based hierarchy (Year, Month, Day)
Fact Table:
facttransaction_table: Transactional and investment facts (amounts, types, balances)

🔄 Gold Layer to Fabric Data Warehouse
To support Power BI connectivity and faster querying, gold layer tables were moved from Lakehouse to Warehouse using Pipeline:
________________________________________



📊 Power BI Reports
Using Fabric's Direct Lake connection, the following insights were visualized:
1. Transaction Trends
•	Monthly volume of transactions
•	Total transaction by customer
2. Customer Spending Behavior
•	Average spending by age group
•	Customer distribution by account type 
3. Risk Assessment
•	Branches with low profit margins
•	Customers with high withdrawals vs balance
•	City and region wise analysis of branch performance
 Power BI report 1-👇
 -----------------------------------------------------------------------------------------------------------------
   <img src="image/Screenshot (32).png" alt="Dashboard" width="900"/>
-----------------------------------------------------------------------------------------------------------------

 Power BI report 2-👇
  -----------------------------------------------------------------------------------------------------------------
   <img src="image/Screenshot (33).png" alt="Dashboard" width="800"/>
-----------------------------------------------------------------------------------------------------------------
The hole pipeline overview:-👇
====================================================================================================
<img src="image/Screenshot (34).png" alt="Dashboard" width="900"/>