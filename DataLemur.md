# DataLemur SQL Challenges
### [DataLemur](https://datalemur.com) is a code challenge website made by Nick Singh. It hosts SQL and DS interview questions you can practice to improve your skills before applying to positions (or just to keep yourself sharp). Problems are grouped by difficulty and listed in the order I solved them.

## Easy

### 1. Data Science Skills [LinkedIn SQL Interview Question]

Given a table of candidates and their skills, you're tasked with finding the candidates best suited for an open Data Science job. You want to find candidates who are proficient in Python, Tableau, and PostgreSQL.

Write a query to list the candidates who possess all of the required skills for the job. Sort the output by candidate ID in ascending order.

Assumption:

- There are no duplicates in the candidates table.

```sql
SELECT candidate_id
  FROM candidates
 WHERE skill IN ('Python', 'Tableau', 'PostgreSQL')
 GROUP BY candidate_id
HAVING COUNT(skill) = 3
 ORDER BY candidate_id

```

### 2. Page With No Likes [Facebook SQL Interview Question]

Assume you're given two tables containing data about Facebook Pages and their respective likes (as in "Like a Facebook Page").

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

Tesla is investigating production bottlenecks and they need your help to extract the relevant data. Write a query that determines which parts with the assembly steps have initiated the assembly process but remain unfinished.

Assumptions:

- parts_assembly table contains all parts currently in production, each at varying stages of the assembly process.
- An unfinished part is one that lacks a finish_date.

```sql
SELECT part, assembly_step
  FROM parts_assembly 
 WHERE finish_date is NULL;
```

### 4. Laptop vs. Mobile Viewership [New York Times SQL Interview Question]

Assume you're given the table on user viewership categorised by device type where the three types are laptop, tablet, and phone.

Write a query that calculates the total viewership for laptops and mobile devices where mobile is defined as the sum of tablet and phone viewership. Output the total viewership for laptops as laptop_reviews and the total viewership for mobile devices as mobile_views.

```sql
SELECT
       COUNT(*) FILTER (WHERE device_type = 'laptop') AS laptop_views,
       COUNT(*) FILTER (WHERE device_type IN ('phone', 'tablet')) AS mobile_views
  FROM viewership
```

### 5. Cities With Completed Trades [Robinhood SQL Interview Question]

Assume you're given the tables containing completed trade orders and user details in a Robinhood trading system.

Write a query to retrieve the top three cities that have the highest number of completed trade orders listed in descending order. Output the city name and the corresponding number of completed trade orders

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
### 6. Histogram of Tweets [Twitter SQL Interview Question]

Assume you're given a table Twitter tweet data, write a query to obtain a histogram of tweets posted per user in 2022. Output the tweet count per user as the bucket and the number of Twitter users who fall into that bucket.

In other words, group the users by the number of tweets they posted in 2022 and count the number of users in each group.

```sql
SELECT
       tweets_per_user AS tweet_bucket,
       COUNT(user_id) AS users_num
  FROM (
       SELECT 
              COUNT(tweet_id) AS tweets_per_user,
              user_id
         FROM tweets
        WHERE tweet_date BETWEEN '2022-01-01' AND '2022-12-31'
        GROUP BY user_id) AS totals_by_user
 GROUP BY tweets_per_user
```

## Medium

## Hard
