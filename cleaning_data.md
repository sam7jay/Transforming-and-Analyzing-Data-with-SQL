## What issues will you address by cleaning the data?

Removing the columns that only have null values

Removing columns containing duplicate data

Adjusting prices






## Queries:
Below, provide the SQL queries you used to clean your data.

### 1. Remove unneccessary columns that only have null values
```SQL
ALTER TABLE all_sessions DROP COLUMN transactionrevenue;
```
### 2. Remove columns with duplicate data
```SQL
ALTER TABLE all_sessions DROP COLUMN transactionrevenue;
```
### 3. Adjusting prices
```SQL
UPDATE all_sessions
 SET totaltransactionrevenue = totaltransactionrevenue/1000000
 WHERE totaltransactionrevenue IS NOT NULL;
 ```
### 4. Round to two decimal places
 ```SQL
UPDATE all_sessions
SET product_price = ROUND(product_price::NUMERIC, 2)
WHERE product_price IS NOT NULL;
 ```
### 5. Removing columns with only NULL values
```SQL
ALTER TABLE all_sessions
DROP COLUMN product_refund_amount,
DROP COLUMN item_quantity,
DROP COLUMN item_revenue,
DROP COLUMN search_keyword
```
```SQL
ALTER TABLE analytics
DROP COLUMN user_id
```
