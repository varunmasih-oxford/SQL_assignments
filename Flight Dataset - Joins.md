# SQL Practice – Flight Dataset (Advanced Concepts)

This section adds more datasets and covers:
- JOIN (INNER, LEFT, RIGHT)
- UNION / UNION ALL
- INTERSECT
- EXCEPT

---

## Additional Tables

### Table 1: `airlines_info`

| Column Name | Data Type | Description |
|------------|----------|-------------|
| airline    | VARCHAR  | Airline name |
| country    | VARCHAR  | Country of origin |
| rating     | INT      | Airline rating (1–5) |

---

### Table 2: `airports`

| Column Name | Data Type | Description |
|------------|----------|-------------|
| city       | VARCHAR  | City name |
| airport_name | VARCHAR | Airport name |

---

## Sample Data

```sql
CREATE TABLE airlines_info (
    airline VARCHAR(50),
    country VARCHAR(50),
    rating INT
);

INSERT INTO airlines_info VALUES
('IndiGo', 'India', 4),
('Air India', 'India', 3),
('Vistara', 'India', 5),
('Emirates', 'UAE', 5),
('Qatar Airways', 'Qatar', 5);


CREATE TABLE airports (
    city VARCHAR(50),
    airport_name VARCHAR(100)
);

INSERT INTO airports VALUES
('Delhi', 'Indira Gandhi International Airport'),
('Mumbai', 'Chhatrapati Shivaji Airport'),
('Bangalore', 'Kempegowda International Airport'),
('Dubai', 'Dubai International Airport'),
('London', 'Heathrow Airport');
````

---

# 8. JOIN Queries

### Question 26

Write a query to display flight details along with airline country.

### Question 27

Write a query to display airline name and its rating for each flight.

### Question 28

Write a query to display flights along with their source airport name.

### Question 29

Write a query to display all flights even if airline details are missing.

### Question 30

Write a query to display all airlines and their flights (even if no flights exist).

---

# 9. UNION & UNION ALL

### Question 31

Create a query to list all **source cities** and **destination cities** in one column (remove duplicates).

### Question 32

Create a query to list all cities (including duplicates).

---

# 10. INTERSECT

### Question 33

Write a query to find cities that are both **source cities** and **destination cities**.

---

# 11. EXCEPT

### Question 34

Write a query to find cities that are **source cities but not destination cities**.

---

# 12. Mixed Advanced Questions

### Question 35

Write a query to find airlines that operate flights **and** have a rating of 5.

### Question 36

Write a query to find flights where the airline is from **India**.

### Question 37

Write a query to display all unique cities involved in flights using UNION.

---

# Solutions

```sql
-- Q26 INNER JOIN
SELECT f.*, a.country
FROM flights f
INNER JOIN airlines_info a
ON f.airline = a.airline;

-- Q27 JOIN with rating
SELECT f.airline, a.rating
FROM flights f
JOIN airlines_info a
ON f.airline = a.airline;

-- Q28 JOIN with airports
SELECT f.*, ap.airport_name
FROM flights f
JOIN airports ap
ON f.source_city = ap.city;

-- Q29 LEFT JOIN
SELECT f.*, a.country
FROM flights f
LEFT JOIN airlines_info a
ON f.airline = a.airline;

-- Q30 RIGHT JOIN
SELECT a.*, f.flight_id
FROM flights f
RIGHT JOIN airlines_info a
ON f.airline = a.airline;

-- Q31 UNION
SELECT source_city AS city FROM flights
UNION
SELECT destination_city FROM flights;

-- Q32 UNION ALL
SELECT source_city FROM flights
UNION ALL
SELECT destination_city FROM flights;

-- Q33 INTERSECT
SELECT source_city FROM flights
INTERSECT
SELECT destination_city FROM flights;

-- Q34 EXCEPT
SELECT source_city FROM flights
EXCEPT
SELECT destination_city FROM flights;

-- Q35 Rating 5 airlines
SELECT DISTINCT f.airline
FROM flights f
JOIN airlines_info a
ON f.airline = a.airline
WHERE a.rating = 5;

-- Q36 Indian airlines
SELECT f.*
FROM flights f
JOIN airlines_info a
ON f.airline = a.airline
WHERE a.country = 'India';

-- Q37 Unique cities
SELECT source_city FROM flights
UNION
SELECT destination_city FROM flights;
```
