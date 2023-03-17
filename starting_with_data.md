## Question 1: Question 1: What is the total number of unique visitors by referring sites?

SQL Queries:
```SQL
SELECT COUNT(DISTINCT fullvisitorid) FROM all_sessions;
```

### Answer:
14223

## Question 2: What countries are visiting the website from outside of the USA ?

SQL Queries:
```SQL
SELECT country
FROM all_sessions
WHERE country != 'United States'
GROUP BY country
order by country;
```

### Answer:
134 countries.

## Question 3: How many users spent less than 1 minute seconds on the site? 

SQL Queries:
```SQL
SELECT COUNT(timeonsite) FROM all_sessions
WHERE timeonsite < 60;
```

### Answer:
3729 visitors spent less than 1 minute on the site.
