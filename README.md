
# AtliQ Sales Insights Dashboard

This is a project I replicated from Codebasics PowerBi Youtube playlist. You can find the link of the playlist below.

[Codebasics Youtube Playlist](https://youtube.com/playlist?list=PLeo1K3hjS3uva8pk1FI3iK9kCOKQdz1I9)


## Problem statement

AtliQ hardware is a company which delivers computer hardware & peripheral 
Manufacturers to his clients, which has several branches throughout India. The sales director of the company is facing a lot of
issues in terms of understanding how the business is performing and what are all the problem company is
facing currently as the sales are not as expected and declining gradually. And whenever he calls the regional managers
to get the current status of the sales and market, as a human behaviour, these people 
sugar cote the truth and send tons of Excel files instead of disclosing the truth, which made the sales director more frustrated.
Humans are not comfortable in consuming numbers from excel files, which is obvious reason for the frustration.

## Solution 

Sales director of the AltiQ hardware, decided to build a PowerBI Dashboard for converting the data into 
visual representation to make data driven decisions. So, he hired a team of data people to complete this task.


### AIMS Grid

---
By using the AIMS grid project management tool, we made sure what are the purpose, stakeholder, end result 
and success criteria  of our project.

SQL database dump is in db_dump.sql file above. Download `db_dump.sql` file to your local computer and import it as per instructions given in the tutorial video

![image](https://github.com/devrajmuni143/Sales-Insights-Dashboard/assets/100869651/4c18cc59-cb5d-42b3-a9f3-0bb8fc8bd1e1)

### Data Analysis Using SQL

Show all customer records

    `SELECT * FROM customers;`

Show total number of customers

    `SELECT count(*) FROM customers;`

Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis Using Power BI
============================

1. Formula to create norm_amount column

`= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`





## Steps Followed in this project

1. Performed a High level analysis of data in SQL to get better understanding over the data.
2. Connected the SQL data set to PowerBI.
3. Performed ETL and data cleaning on the imported data.
4. In the currency there were two types of currencies in transactions, performed currency conversion to make all the currency type same
5. Created measure for needs and used them for creating visuals in PowerBi.
6. After the initial report reviewed by the stakeholders, made changes to the report based on the review commends.

## Final result 

#### Initial Dashboard
![Initial Dashboard](https://github.com/devrajmuni143/Sales-Insights-Dashboard/assets/100869651/67ffaf80-b18c-486c-9830-569b4b4702ca)
#### Final Dashboard
![Updated Dashboard](https://github.com/devrajmuni143/Sales-Insights-Dashboard/assets/100869651/66b5df08-474f-4984-a4dd-7bad3df42c8d)
