# Just-some-SQL-Querries
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
