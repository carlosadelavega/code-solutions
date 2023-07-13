# HackerRank SQL Challenges
### [HackerRank](https://www.hackerrank.com) is a popular code challenge website hosting hundreds of interview questions across several competencies and languages. You can use it to practice and improve your skills before applying to positions, and many companies even use its platform as the interview environment or take home test.
### Problems are grouped by difficulty and listed in the order I solved them.

## Easy

### 1. [Revising the Select Query I](https://www.hackerrank.com/challenges/revising-the-select-query/problem)

```sql
SELECT *
  FROM city
 WHERE population > 100000 AND countrycode = 'USA'
```

### 2. [Revising the Select Query II](https://www.hackerrank.com/challenges/revising-the-select-query-2/problem)

```sql
SELECT name
  FROM city
 WHERE population > 120000 AND countrycode = 'USA'
```

### 3. [Select All](https://www.hackerrank.com/challenges/select-all-sql/problem)

```sql
SELECT *
  FROM city
```
### 4. [Select by ID](https://www.hackerrank.com/challenges/select-by-id/problem)

```sql
SELECT *
  FROM city
 WHERE id = 1661
```

### 5. [Japanese Cities' Attributes](https://www.hackerrank.com/challenges/japanese-cities-attributes/problem)

```sql
SELECT *
  FROM city
 WHERE countrycode = 'JPN'
```

### 6. [Japanese Cities' Names](https://www.hackerrank.com/challenges/japanese-cities-name/problem)

```sql
SELECT name
  FROM city
 WHERE countrycode = 'JPN'
```

### 7. [Weather Observation Station 1](https://www.hackerrank.com/challenges/weather-observation-station-1/problem)

```sql
SELECT city, state
  FROM station
```

### 8. [Weather Observation Station 3](https://www.hackerrank.com/challenges/weather-observation-station-3/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE id % 2 = 0
```

### 9. [Weather Observation Station 4](https://www.hackerrank.com/challenges/weather-observation-station-4/problem)

```sql
SELECT (total_records - unique_cities)
  FROM (
       SELECT COUNT(*) AS total_records, COUNT(DISTINCT city) AS unique_cities
         FROM station) AS t1
```

### 10. [Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5/problem)

```sql
SELECT city, city_length
  FROM (
       SELECT city, LENGTH(city) AS city_length
         FROM station
        WHERE LENGTH(city) IN (
                              SELECT MIN(LENGTH(city))
                                FROM station)
        ORDER BY city) AS shortest_city
 LIMIT 1;
 
SELECT city, city_length
  FROM (
       SELECT city, LENGTH(city) AS city_length
         FROM station
        WHERE LENGTH(city) IN (
                              SELECT MAX(LENGTH(city))
                                FROM station) 
        ORDER BY city) AS longest_city
 LIMIT 1;
```

### 11. [Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE SUBSTR(city,1,1) IN ('A', 'E', 'I', 'O', 'U');
```

### 12. [Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE RIGHT(city,1) in ('A', 'E', 'I', 'O', 'U')
```

### 13. [Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) IN ('A', 'E', 'I', 'O', 'U')) AND
        (RIGHT(city,1) IN ('A', 'E', 'I', 'O', 'U')))
```

### 14. [Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')
```

### 15. [Weather Observation Station 10](https://www.hackerrank.com/challenges/weather-observation-station-10/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')
```

### 16. [Weather Observation Station 11](https://www.hackerrank.com/challenges/weather-observation-station-11/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')) OR
        (RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')))
```

### 17. [Weather Observation Station 12](https://www.hackerrank.com/challenges/weather-observation-station-12/problem)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')) AND
        (RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')))
```


### 18. [Higher Than 75 Marks](https://www.hackerrank.com/challenges/more-than-75-marks/problem)

```sql
SELECT name
  FROM (
       SELECT name, id
         FROM students
        WHERE marks > 75) AS t1
 ORDER BY RIGHT(name,3), id;
```

### 19. [Employee Names](https://www.hackerrank.com/challenges/name-of-employees/problem)

```sql
SELECT name
  FROM employee
 ORDER BY name
```

### 20. [Employee Salaries](https://www.hackerrank.com/challenges/salary-of-employees/problem)

```sql
SELECT name
  FROM employee
 WHERE (salary > 2000) AND months < 10
 ORDER BY employee_id
```

### 21. [Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle/problem)

```sql
SELECT CASE
       WHEN a=b AND b=c THEN "Equilateral"
       WHEN (a+b) <= c OR (a+c) <= b OR (b+c) <= a THEN "Not A Triangle"
       WHEN NOT (a=b OR a=c OR b=c) THEN "Scalene"
       ELSE "Isosceles"
       END
  FROM triangles
```

### 22. [Revising Aggregations - The Count Function](https://www.hackerrank.com/challenges/revising-aggregations-the-count-function/problem)

```sql
SELECT COUNT(*)
  FROM city
 WHERE population > 100000
```

### 23. []()

```sql

```

### 24. []()

```sql

```

### 25. []()

```sql

```


## Medium

### 1. [The PADS](https://www.hackerrank.com/challenges/the-pads/problem)

```sql
SELECT CONCAT(name, '(', SUBSTR(occupation,1,1), ')')
  FROM occupations
  ORDER BY name;

SELECT CONCAT ("There are a total of ", occupation_count, ' ', LOWER(occupation), "s.")
  FROM (
       SELECT occupation, COUNT(occupation) AS occupation_count
         FROM occupations
        GROUP BY occupation
       ) as t1
 ORDER BY occupation_count, occupation;
```

### 2. []()

```sql

```

### 3. []()

```sql

```

### 4. []()

```sql

```

### 5. []()

```sql

```
## Hard
