# Sales Insights Analysis Dashboard

## Overview
This project focuses on building a **Power BI Sales Insights Dashboard** that empowers business stakeholders with data-driven decision-making.  

The dashboard helps the **Sales Director** and management team to:
- Track **overall sales performance** across different time periods  
- Identify **top-performing customers, products, and markets**  
- Analyze **revenue trends** and growth opportunities  

### Project Highlights
- Worked with a **large dataset** containing sales transactions, customer details, product data, and market information.  
- Imported raw data from **MySQL into Power BI** for analysis.  
- Performed **ETL (Extract, Transform, Load)** operations including data cleaning, transformation, handling invalid values, duplicate entries, negative amounts, and currency conversions.
- Developed an **interactive dashboard** to visualize:  
  - Revenue and sales trends  
  - Top customers & key markets  
  - KPIs for strategic business insights  

## Data Analysis using MySQL :
Completed the Data discovery and then used mySQL for data analysis.

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer

 - Importing Data to MySQL workbench
<img width="1000" height="700" alt="image" src="https://github.com/user-attachments/assets/f2aac803-8aeb-40f0-922d-2009bddb71a6" />


<img width="1000" height="700" alt="image" src="https://github.com/user-attachments/assets/4093d49d-b6c7-4239-8fb1-515654c2cff6" />

The import of data is done from an already existing MySQL file. This file has to be loaded into MySQL workbench for further data analysis.

 - Analysis of data by looking into different tables and reflecting garbage values

  We can see that garbage value that the table market cantains certain values which are incorrect.

  `SELECT * FROM sales.market;`

  And then we can check that transacation table we can see that ceratin negative value in amount which is not possible. and we can see that certain transactions are in USD. Hence, filtration of that is also needed by converting into INR.

  `SELECT * FROM sales.transactions;`

 - Analysis of different SQL statement on data base

  1. To find of all customers records

  `SELECT * FROM sales.customers;`

  2. To find total number of customers
  
  `SELECT count(*) From sales.customers;`
  
  3. To find transactions for Chennai market (market code for chennai is Mark001
  
  `SELECT * FROM sales.transactions where market_code='Mark001';`

  4. To find distrinct product codes that were sold in chennai
  
  `SELECT distinct product_code FROM sales.transactions where market_code='Mark001';`
  
  5. To find transactions for Chennai market (market code for chennai is Mark002
  
  `SELECT * FROM sales.transactions where market_code='Mark002';`
  
  6. To find distrinct product codes that were sold in mumbai
  
  `SELECT distinct product_code FROM sales.transactions where market_code='Mark002';`
  
  7. To find transactions where currency is US dollars
  
  `SELECT * from sales.transactions where currency="USD";`
  
  8. To find transactions in 2020 join by date table
  
  `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;`
  
  9. To find transactions in 2019 join by date table
  
  `SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;`
  
  10. To find total revenue in year 2020,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`
  
  11. To find total revenue in year 2019,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`
  
  12. To find total revenue in year 2020, January Month,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`
  
  13. To find total revenue in year 2020, February Month,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`
  
  14. To find total revenue in year 2019, January Month,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`
  
  15. To find total revenue in year 2019, February Month,
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`
  
  16. To find total revenue in year 2020 in Chennai
  
  `SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";`
  
  17. To find total revenue in year 2020 in Mumbai
  
  SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where `sales.date.year=2020 and sales.transactions.market_code="Mark002";`

Similarly, if we want different of any other particular city the market code of that city is used on the mysql workbench.

## Data Cleaning and ETL (Extract, Transform, Load):
In this process, we are work on data cleaning and ETL.

Step 1: Connect the MySQL database with the PowerBI desktop.

Step 2: Loading data into the Power BI deskstop. This step load all the tables and created in the data base. This load option will connect with the SQL and pull all the records into power BI environment.

In that model view looking up for model which form the star schema.

<img width="1000" height="700" alt="image" src="https://github.com/user-attachments/assets/4be5f472-5561-458e-b30b-0bc04cde79dc" />


Setp 3: Transform data with the help of Power Query

Perform filtration in market’s table: In the tables perform when we click on the transform data option, we are directed to Power query editor. Power query editor is where we perform out ETL.and then we can perform data transformation i.e. Data Cleaning, Data Wrangling, Data Munging. we need to filter the rows where the values are null and filtering the data and deselecting the blank option.

Perform filtration in Transaction’s table: In the table perform when we check the query in the MySQL to filter some negative values and also 0 values that appears in the table, the desired output is received.and we will perform the similar filtration in PowerBI. we have deselecting the values, don’t want in the table. The result after filtration. the zero values represent some garbage values which is not possible so we need to clean that data.

Convert USD into INR in the transaction’s table: the AtliQ Hardware only works in India so the USD values are not possible. we need to convert those USD values into INR by using some formulas. Add new column - Conditional column - normalized currency where sales amount will be in INR

In power query editor finding the total values having USD as currency.

 `=Table.AddColumn(#"Filtered Rows", "norm_sales_amount",each if [currency] = "USD" then [sales_amount]*87 else [sales_amount]`
using this correct formula of the conversion,and converted the USD currency into INR.

In MySQL Workbench find that there are duplicates of USD and INR

 `SELECT count(*) from sales.transactions where sales.transactions.currency="INR\r";` 
 150000 - can't removed as it is large amount

 `SELECT count(*) from sales.transactions where sales.transactions.currency="INR";` 
 279 - we can remove it as it is small record and can be considered as bad data

 `SELECT count(*) from sales.transactions where sales.transactions.currency="USD\r";` 

 `SELECT count(*) from sales.transactions where sales.transactions.currency="USD";`

 `SELECT * from sales.transactions where sales.transactions.currency='USD\r' or sales.transactions.currency='USD';`
we can see that it is duplicate and for analysis its better to delete anyone of them so lets delete USD and keep USD/r. finally we will keep data with INR/r and USD/r

## Data Modeling:
And then dataset was cleaned and transformed, it was ready to the data modeled.

The sales insights data tables as show below:

<img width="1000" height="700" alt="image" src="https://github.com/user-attachments/assets/00111c44-a7b0-4e11-81ba-c82c89596daa" />


## Data Analysis (DAX):
Measures used in all visualization are:

Key Measures:

Profit Margin % = `DIVIDE([Total Profit Margin],[Revenue],0)`

Profit Margin Contribution % = `DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))`

Revenue = `SUM('sales transactions'[sales_amount])`

Revenue Contribution % = `DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))`

Revenue LastYear = `CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))`

Sales Qty = `SUM('sales transactions'[sales_qty])`

Total Profit Margin = `SUM('Sales transactions'[Profit_Margin])`

Profit Target:

Profit Target1 = `GENERATESERIES(-0.05, 0.15, 0.01)`

Profit Target Value = `SELECTEDVALUE('Profit Target1'[Profit Target])`

Target Difference = `[Profit Margin %]-'Profit Target1'[Profit Target Value]`

## Build Dashboard Or a Report:
Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop:

Shows visualizations from Sales insights :

| Key Insights | Profit Analysis |
|-------------|-------------|
| <img width="400" alt="Screenshot 2025-08-28 172529" src="https://github.com/user-attachments/assets/d7d90a6b-23be-47a3-b5bc-ab547d19deaa" /> | <img width="400" alt="Screenshot 2025-08-28 172600" src="https://github.com/user-attachments/assets/410af12c-47af-4d69-b22b-8e4b231cd859" /> |

| Performance Insights | Revenue and Sales Insights |
|-------------|-------------|
| <img width="400" alt="Screenshot 2025-08-28 172622" src="https://github.com/user-attachments/assets/eb7ef5c7-4265-4876-b8c1-48689cb3c12b" /> | <img width="400" alt="Screenshot 2025-08-28 172655" src="https://github.com/user-attachments/assets/43840e18-a8cc-45db-b76f-9d52088ebe30" /> |

## Tools, Software and Libraries :
  1.MySQL
  
  2.Microsoft Power BI
  
  3.Power Query Editor
  
  4.DAX Language
