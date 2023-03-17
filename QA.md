## What are your risk areas? Identify and describe them.

-The tables contained similar data

-There were a lot of missing values and duplicate values

-Missing terms in country and city names

-Had to Adjusting prices

## QA Process:

-Validation by running sections of code in isolation

-Checking SKUs are consistent

```SQL
select count(product_price), product_price, product_sku 
from all_sessions group by product_sku, product_price 
order by product_sku desc
```

-determining whether there are any missing values 

```SQL
SELECT productsku 
FROM sales_report
WHERE productsku IS NULL
```

-Checking my results and ensuring they added up to the appropriate count
