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
