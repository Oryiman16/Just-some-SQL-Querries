# SQL-Querries/ Data Quality Test Query
Trying out some SQL querries!

  --Case Statement to categorize profit margin from a sales shop

select retailer, city, product, operating_profit, sales_method,
case
when operating_profit = 0 then 'No Profit'
when operating_profit > 0 and operating_profit < 500 then 'marginal profit'
when operating_profit > 500 and operating_profit < 1000 then 'very low profit'
when operating_profit > 1000 and operating_profit < 5000 then 'low profit'
when operating_profit > 5000 and operating_profit < 10000 then 'medium profit'
when operating_profit > 10000 and operating_profit < 20000 then 'high profit'
when operating_profit > 20000 and operating_profit < 30000 then 'high profit'
else 'exceptional profit'
end
from addidas_sales


--How do you return the cumulative sum (running total) in SQL?
SELECT 
 date,
 sales,
 SUM(sales) OVER (PARTITION BY MONTH(date) ORDER BY date) AS cumulative_monthly_sales
FROM yourTable

- SUM() calculates a running total sum 
- PARTITION BY splits the data by month
- ORDER BY sorts the rows chronologically 

The resultset will contain the original daily sales data, plus a new cumulative_monthly_sales column calculating the running total.

--SQL QUERIES--

--CHARINDEX--
--E.G Select CHARINDEX ('substring', column name), column name from table name--

--SUBSTRING--
--Use to select substring within a string eg select substring 'man' from string 'Oryiman'--
--E.g Select substring (column name, 1, CHARINDEX ('substring', column name)) from table name--

--DATA QUALITY TESTS--
--1 Row Count test: 
	Select count (*) from table name--

--2 Column count test: 
	select count * as column_count 
		from information_schema.columns
		where table name ='table name'
    
--3 Data Type test: 
	select column_name, data_type
		from information_schema_columns
        where table name = 'table name'
        
--4 Duplicate count test: 
	select  column name, count (*) as duplicate_count
		from table name
		Group by column name
		Having count (*) >1
