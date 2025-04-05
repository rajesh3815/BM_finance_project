# BM_finance_project
PROJECT DOCUMENTATION:-
-------------------------------------------------------------------------------------------------------------------------
👨‍💻 Developed by: Rajesh Kumar Rout <br>
 Platform: Microsoft Fabric <br>
 Tools & Technologies: PySpark, Delta Lake, Lakehouse, Data Warehouse, Power BI <br>
________________________________________
 Project Overview <br>
This project focuses on analyzing financial data for a banking system to generate actionable insights regarding:<br>
•	 Transaction trends <br>
•	Customer spending behavior<br>
•	 Risk assessment<br>
The data flows from raw ingestion to a gold layer star schema, and finally into a Power BI dashboard, via Microsoft Fabric Lakehouse and Warehouse.<br>
________________________________________
Architecture Overview<br>
Importing data into MSSQL-<br>
•	Imported data from three Excel files into a Microsoft SQL Server database in tabular format.<br>

Bronze layer- <br>
•	Connected on-premises SQL Server to Microsoft Fabric using the On-premises Data Gateway, enabling secure and reliable data transfer without exposing the source directly.<br>
•	Configured the data pipeline to ingest data into the Bronze layer of a Fabric Lakehouse, ensuring the raw data was stored efficiently for further transformation.<br>
•	Utilized OneLake storage to manage the ingested data centrally, setting the stage for building a structured multi-layered data architecture.<br>

 Silver Layer(using pyspark notebook):<br>
•	Cleaned data stored in Delta format tables.<br>
•	Perform operations like Drop duplicates, fill the null values<br>
•	Tables: customer_data, transaction_data, bank_data.<br>

⭐ Gold Layer (Star Schema):<br>
        Built using PySpark with the following structure:<br>
       Apply Bussiness logic to transform silver layer data to gold layer (BI consumable data) <br>
       <img src="image/Screenshot (31).png" alt="Dashboard" width="900"/><br>

Dimension Tables:<br>
•	bankbranch_table: Customer details (Customer_ID, Age, Region, etc.)<br>
•	customer_table: Bank branch financials (Branch_ID, Revenue, Profit, etc.)<br>
•	datedata_table: Date-based hierarchy (Year, Month, Day)<br>
Fact Table:<br>
facttransaction_table: Transactional and investment facts (amounts, types, balances)<br>

🔄 Gold Layer to Fabric Data Warehouse<br>
To support Power BI connectivity and faster querying, gold layer tables were moved from Lakehouse to Warehouse using Pipeline:<br>
________________________________________



📊 Power BI Reports<br>
Using Fabric's Direct Lake connection, the following insights were visualized:<br>
1. Transaction Trends<br>
•	Monthly volume of transactions<br>
•	Total transaction by customer<br>
2. Customer Spending Behavior<br>
•	Average spending by age group<br>
•	Customer distribution by account type <br>
3. Risk Assessment<br>
•	Branches with low profit margins<br>
•	Customers with high withdrawals vs balance<br>
•	City and region wise analysis of branch performance<br>
 Power BI report 1-👇<br>
 -----------------------------------------------------------------------------------------------------------------
   <img src="image/Screenshot (32).png" alt="Dashboard" width="900"/><br>
-----------------------------------------------------------------------------------------------------------------

 Power BI report 2-👇<br>
  -----------------------------------------------------------------------------------------------------------------
   <img src="image/Screenshot (33).png" alt="Dashboard" width="800"/><br>
-----------------------------------------------------------------------------------------------------------------
The hole pipeline overview:-👇<br>
====================================================================================================
<img src="image/Screenshot (34).png" alt="Dashboard" width="900"/><br>