Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**

**SQL Queries:**
```SQL
SELECT sum(totaltransactionrevenue) as total, city, country
FROM all_sessions
where totaltransactionrevenue is not null and city != 'N/A'
group by city, country
order by total desc
```

Answer:
highest countries: United State, Israel, Australia
highest cities: San Fransisco, Sunnyvale, Tel Aviv-Yafo

**Question 2: What is the average number of products ordered from visitors in each city and country?**

**SQL Queries:**
```SQL
SELECT round (avg(totaltransactionrevenue/productprice),2) as avg_prod_ordered, city, country
From all_sessions
where city !='N/A'AND city !='(not set)'
GROUP BY city,country
order by avg_prod_ordered DESC
LIMIT 5;
```

Answer:
116.98	"Sunnyvale"	"United States"
36.09	"Atlanta"	"United States"
16.73	"Chicago"	"United States"
7.62	"Tel Aviv-Yafo"	"Israel"
5.81	"Austin"	"United States"

**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**

**SQL Queries:**
```SQL:
SELECT count(*) as numOfProductPerCat, v2productcategory, city, country
FROM all_sessions
where city !='N/A'AND city !='(not set)'
GROUP BY v2productcategory,country, city
order by  Country desc, numOfProductPerCat desc, city desc
```

Answer:
USA orderd the most
The Most purchased categories in USA Home/Apparels category is the most ordered.

**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**

**SQL Queries:**
```SQL:
SELECT DISTINCT v2productname, country, city, SUM(totaltransactionrevenue) AS SUM_total_transaction_revenue
FROM all_sessions
WHERE totaltransactionrevenue IS NOT NULL
GROUP BY country, city, v2productname
ORDER BY SUM_total_transaction_revenue DESC;
```

Answer:
In all Google Alpine Style Backpack
In all Canada Android Stretch Fit Hat Black
Youtube Bottle Infuser in San Bruno
Nest Cam Indoor Security Camera in Mountain View
Google Men's Convertible Vest-Jacket Pewter in Sunnyvale
Google Laptop Tech Backpack in Jersey City
Google Lunch Bag in Charlotte
Collapsible Shopping Bag in New York

**Question 5: Can we summarize the impact of revenue generated from each city/country?**

**SQL Queries:**
```SQL:
SELECT sum(totalTransactionRevenue) as rev , city, country
FROM all_sessions
where city !='N/A'AND city !='(not set)'AND totalTransactionRevenue is not NULL
GROUP BY city,country
order by country desc, city desc
```

Answer:

Most of the revenue is coming from the United States.





