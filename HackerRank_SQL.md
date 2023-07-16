# HackerRank SQL Challenges
### [HackerRank](https://www.hackerrank.com) is a popular code challenge website hosting hundreds of interview questions across several competencies and languages. You can use it to practice and improve your skills before applying to positions, and many companies even use its platform as the interview environment or take home test.
### Problems are grouped by difficulty and listed in the order I solved them.

## Easy

### 1. [Revising the Select Query I](https://www.hackerrank.com/challenges/revising-the-select-query/)

```sql
SELECT *
  FROM city
 WHERE population > 100000 AND countrycode = 'USA'
```

### 2. [Revising the Select Query II](https://www.hackerrank.com/challenges/revising-the-select-query-2/)

```sql
SELECT name
  FROM city
 WHERE population > 120000 AND countrycode = 'USA'
```

### 3. [Select All](https://www.hackerrank.com/challenges/select-all-sql/)

```sql
SELECT *
  FROM city
```
### 4. [Select by ID](https://www.hackerrank.com/challenges/select-by-id/)

```sql
SELECT *
  FROM city
 WHERE id = 1661
```

### 5. [Japanese Cities' Attributes](https://www.hackerrank.com/challenges/japanese-cities-attributes/)

```sql
SELECT *
  FROM city
 WHERE countrycode = 'JPN'
```

### 6. [Japanese Cities' Names](https://www.hackerrank.com/challenges/japanese-cities-name/)

```sql
SELECT name
  FROM city
 WHERE countrycode = 'JPN'
```

### 7. [Weather Observation Station 1](https://www.hackerrank.com/challenges/weather-observation-station-1/)

```sql
SELECT city, state
  FROM station
```

### 8. [Weather Observation Station 3](https://www.hackerrank.com/challenges/weather-observation-station-3/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE id % 2 = 0
```

### 9. [Weather Observation Station 4](https://www.hackerrank.com/challenges/weather-observation-station-4/)

```sql
SELECT (total_records - unique_cities)
  FROM (
       SELECT COUNT(*) AS total_records, COUNT(DISTINCT city) AS unique_cities
         FROM station) AS t1
```

### 10. [Weather Observation Station 5](https://www.hackerrank.com/challenges/weather-observation-station-5/)

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

### 11. [Weather Observation Station 6](https://www.hackerrank.com/challenges/weather-observation-station-6/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE SUBSTR(city,1,1) IN ('A', 'E', 'I', 'O', 'U');
```

### 12. [Weather Observation Station 7](https://www.hackerrank.com/challenges/weather-observation-station-7/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE RIGHT(city,1) in ('A', 'E', 'I', 'O', 'U')
```

### 13. [Weather Observation Station 8](https://www.hackerrank.com/challenges/weather-observation-station-8/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) IN ('A', 'E', 'I', 'O', 'U')) AND
        (RIGHT(city,1) IN ('A', 'E', 'I', 'O', 'U')))
```

### 14. [Weather Observation Station 9](https://www.hackerrank.com/challenges/weather-observation-station-9/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')
```

### 15. [Weather Observation Station 10](https://www.hackerrank.com/challenges/weather-observation-station-10/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')
```

### 16. [Weather Observation Station 11](https://www.hackerrank.com/challenges/weather-observation-station-11/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')) OR
        (RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')))
```

### 17. [Weather Observation Station 12](https://www.hackerrank.com/challenges/weather-observation-station-12/)

```sql
SELECT DISTINCT city
  FROM station
 WHERE ((SUBSTR(city,1,1) NOT IN ('A', 'E', 'I', 'O', 'U')) AND
        (RIGHT(city,1) NOT IN ('A', 'E', 'I', 'O', 'U')))
```


### 18. [Higher Than 75 Marks](https://www.hackerrank.com/challenges/more-than-75-marks/)

```sql
SELECT name
  FROM (
       SELECT name, id
         FROM students
        WHERE marks > 75) AS t1
 ORDER BY RIGHT(name,3), id;
```

### 19. [Employee Names](https://www.hackerrank.com/challenges/name-of-employees/)

```sql
SELECT name
  FROM employee
 ORDER BY name
```

### 20. [Employee Salaries](https://www.hackerrank.com/challenges/salary-of-employees/)

```sql
SELECT name
  FROM employee
 WHERE (salary > 2000) AND months < 10
 ORDER BY employee_id
```

### 21. [Type of Triangle](https://www.hackerrank.com/challenges/what-type-of-triangle/)

```sql
SELECT CASE
       WHEN a=b AND b=c THEN "Equilateral"
       WHEN (a+b) <= c OR (a+c) <= b OR (b+c) <= a THEN "Not A Triangle"
       WHEN NOT (a=b OR a=c OR b=c) THEN "Scalene"
       ELSE "Isosceles"
       END
  FROM triangles
```

### 22. [Revising Aggregations - The Count Function](https://www.hackerrank.com/challenges/revising-aggregations-the-count-function/)

```sql
SELECT COUNT(*)
  FROM city
 WHERE population > 100000
```

### 23. [Revising Aggregations - The Sum Function](https://www.hackerrank.com/challenges/revising-aggregations-sum/)

```sql
SELECT SUM(population)
  FROM city
 WHERE district = 'California'
```

### 24. [Revising Aggregations - Averages](https://www.hackerrank.com/challenges/revising-aggregations-the-average-function/)

```sql
SELECT AVG(population)
  FROM city
 WHERE district = 'California'
```

### 25. [Average Population](https://www.hackerrank.com/challenges/average-population/)

```sql
SELECT ROUND(AVG(population), 0)
  FROM city
```

### 26. [Japan Population](https://www.hackerrank.com/challenges/japan-population/)

```sql
SELECT SUM(population)
  FROM city
 WHERE countrycode = 'JPN'
```

### 27. [Population Density Difference](https://www.hackerrank.com/challenges/population-density-difference/)

```sql
SELECT (MAX(population) - MIN(population))
  FROM city
```

### 28. [Weather Observation Station 2](https://www.hackerrank.com/challenges/weather-observation-station-2/)

```sql
SELECT ROUND(SUM(lat_n), 2), ROUND(SUM(long_w), 2)
  FROM station
```

### 29. [The Blunder](https://www.hackerrank.com/challenges/the-blunder/)

```sql
SELECT CEIL(AVG(salary) - AVG(REPLACE(salary, '0','')))
  FROM employees
```

### 30. [Top Earners](https://www.hackerrank.com/challenges/earnings-of-employees/)

```sql
SELECT salary*months AS earnings, COUNT(*)
  FROM employee
 GROUP BY earnings
 ORDER BY earnings DESC
 LIMIT 1
```

### 31. [Weather Observation Station 13](https://www.hackerrank.com/challenges/weather-observation-station-13/)

```sql
SELECT ROUND(SUM(lat_n), 4)
  FROM station
 WHERE lat_n BETWEEN 38.7880 AND 137.2345
```

### 32. [Weather Observation Station 14](https://www.hackerrank.com/challenges/weather-observation-station-14/)

```sql
SELECT ROUND(MAX(lat_n), 4)
  FROM station
 WHERE lat_n < 137.2345
```

### 33. [Weather Observation Station 15](https://www.hackerrank.com/challenges/weather-observation-station-15/)

```sql
SELECT ROUND(long_w, 4)
  FROM station
 WHERE lat_n < 137.2345
 ORDER BY lat_n DESC
 LIMIT 1
```

### 34. [Weather Observation Station 16](https://www.hackerrank.com/challenges/weather-observation-station-16/)

```sql
SELECT ROUND(lat_n, 4)
  FROM station
 WHERE lat_n > 38.7780
 ORDER BY lat_n ASC
 LIMIT 1
```

### 35. [Weather Observation Station 17](https://www.hackerrank.com/challenges/weather-observation-station-17/)

```sql
SELECT ROUND(long_w, 4)
  FROM station
 WHERE lat_n > 38.7780
 ORDER BY lat_n
 LIMIT 1
```

### 36. [Population Census](https://www.hackerrank.com/challenges/asian-population/)

```sql
SELECT SUM(a.population)
  FROM city a
 INNER JOIN country b
    ON a.countrycode = b.code
 WHERE b.continent = 'Asia'
```

### 37. [African Cities](https://www.hackerrank.com/challenges/african-cities/)

```sql
SELECT a.name
  FROM city a
 INNER JOIN country b
    ON a.countrycode = b.code
 WHERE b.continent = 'Africa'
```

### 38. [Average Population of Each Continent](https://www.hackerrank.com/challenges/average-population-of-each-continent/)

```sql
SELECT a.continent, FLOOR(AVG(b.population))
  FROM country a
 INNER JOIN city b
    ON a.code = b.countrycode
 GROUP BY a.continent
```

## Medium

### 1. [The PADS](https://www.hackerrank.com/challenges/the-pads/)

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

### 2. [Weather Observation Station 18](https://www.hackerrank.com/challenges/weather-observation-station-18/)

```sql
SELECT ROUND(MAX(lat_n) - MIN(lat_n) + MAX(long_w) - MIN(long_w),4)
  FROM station
```

### 3. [Weather Observation Station 19](https://www.hackerrank.com/challenges/weather-observation-station-19/)

```sql
SELECT ROUND(SQRT(POW(MAX(lat_n)-MIN(lat_n), 2) + POW(MAX(long_w)-MIN(long_w), 2)), 4)
  FROM station
```

### 4. [The Report](https://www.hackerrank.com/challenges/the-report/)

```sql
SELECT s.name, g.grade, s.marks
  FROM students s
 INNER JOIN grades g
    ON s.marks BETWEEN g.min_mark AND g.max_mark
 WHERE g.grade >= 8
 ORDER BY g.grade DESC, s.name ASC;
 
SELECT REPLACE(s.name, s.name, 'NULL'),  g.grade, s.marks
  FROM students s
 INNER JOIN grades g
    ON s.marks BETWEEN g.min_mark AND g.max_mark
 WHERE g.grade < 8
 ORDER BY g.grade DESC, s.marks ASC;
```

### 5. []()

```sql

```
## Hard
