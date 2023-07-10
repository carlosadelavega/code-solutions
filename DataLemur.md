# DataLemur SQL Challenges
### [DataLemur](https://datalemur.com) is a code challenge website made by Nick Singh. It hosts SQL and DS interview questions you can practice to improve your skills before applying to positions (or just to keep yourself sharp).

## Easy

### 1. Data Science Skills [LinkedIn SQL Interview Question]
Write a query to list the candidates who possess all of the required skills for the job. Sort the output by candidate ID in ascending order.
```sql
SELECT candidate_id
  FROM candidates
 WHERE skill IN ('Python', 'Tableau', 'PostgreSQL')
 GROUP BY candidate_id
HAVING COUNT(skill) = 3
 ORDER BY candidate_id

```

### 2. Page With No Likes [Facebook SQL Interview Question]

Write a query to return the IDs of the Facebook pages that have zero likes. The output should be sorted in ascending order based on the page IDs.

Using EXCEPT
```sql
SELECT page_id
  FROM pages
EXCEPT
SELECT page_id
  FROM page_likes
```

Using NOT IN
```sql
SELECT page_id
  FROM pages
 WHERE page_id NOT IN(
       SELECT page_id
         FROM page_likes
        WHERE page_id IS NOT NULL)
```

### 3. Unfinished Parts [Tesla SQL Interview Question]
```sql
SELECT part, assembly_step
  FROM parts_assembly 
 WHERE finish_date is NULL;
```

### 4. Laptop vs. Mobile Viewership [New York Times SQL Interview Question]
```sql
SELECT
       COUNT(*) FILTER (WHERE device_type = 'laptop') AS laptop_views,
       COUNT(*) FILTER (WHERE device_type IN ('phone', 'tablet')) AS mobile_views
  FROM viewership
```

### 5. Cities With Completed Trades [Robinhood SQL Interview Question]
```sql
SELECT
       users.city,
       COUNT(trades.order_id) AS total_orders
  FROM trades
 INNER JOIN users
    ON trades.user_id = users.user_id
 WHERE trades.status = 'Completed'
 GROUP BY users.city
 ORDER BY total_orders DESC
 LIMIT 3
```

## Medium

## Hard
