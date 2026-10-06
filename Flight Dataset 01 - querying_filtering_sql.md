# SQL Practice – Flight Dataset (All Concepts)

This practice set uses a **Flight dataset** and covers all the concepts shown:
- SELECT
- Column selection
- Aliasing (AS)
- ORDER BY (ASC / DESC)
- LIMIT
- DISTINCT
- WHERE (numeric & text)
- BETWEEN
- IN
- LIKE
- Aggregate functions (COUNT, SUM, AVG)
---

## Flight Dataset Structure

Assume a table named **`flights`** with the following columns:

| Column Name        | Data Type | Description |
|--------------------|----------|-------------|
| flight_id          | INT      | Unique flight ID |
| airline            | VARCHAR  | Airline name |
| source_city        | VARCHAR  | Departure city |
| destination_city   | VARCHAR  | Arrival city |
| departure_year     | INT      | Year of departure |
| ticket_price       | INT      | Ticket price in USD |
| aircraft_type      | VARCHAR  | Aircraft model |
| flight_duration    | INT      | Duration in minutes |

---

## 1. Basic SELECT Queries

### Question 1
Write a query to fetch **all columns** from the `flights` table.

---

### Question 2
Write a query to fetch only the `airline` column from the table.

---

### Question 3
Write a query to fetch `airline`, `source_city`, and `destination_city`.

---

---

## 2. Column Aliasing & Sorting

### Question 4
Write a query to display `airline` and `departure_year`, but rename  
`departure_year` as **`year_of_departure`**.

---

### Question 5
Write a query to display `airline` and `ticket_price` ordered by  
`ticket_price` in **ascending order**.

---

### Question 6
Write a query to display `airline` and `flight_duration` ordered by  
`flight_duration` in **descending order**.

---

---

## 3. LIMIT & DISTINCT

### Question 7
Write a query to display **only the first 5 flights**.

---

### Question 8
Write a query to fetch **unique airline names**.

---

---

## 4. Filtering Numeric Data

### Question 9
Write a query to fetch flights with a ticket price **greater than 500**.

---

### Question 10
Write a query to fetch flights with a ticket price **greater than or equal to 300**.

---

### Question 11
Write a query to fetch flights with a ticket price **less than 200**.

---

### Question 12
Write a query to fetch flights that departed **in the year 2022**.

---

### Question 13
Write a query to fetch flights that **did not depart in 2020**.

---

### Question 14
Write a query to fetch flights that departed **between 2018 and 2023** (inclusive).

---

---

## 5. Filtering Text Data

### Question 15
Write a query to fetch flights where the `airline` is **'IndiGo'**.

---

### Question 16
Write a query to fetch flights where the airline is either  
**'Air India'** or **'Emirates'**.

---

### Question 17
Write a query to fetch flights where the `aircraft_type` contains  
the word **"Boeing"**.

---

---

## 6. Aggregate Functions

### Question 18
Write a query to find the **total number of flights**.

---

### Question 19
Write a query to calculate the **total ticket revenue** of all flights.

---

### Question 20
Write a query to calculate the **average ticket price**.

---

### Question 21
Write a query to find the **average flight duration**.

---

### Question 22
Write a query to count how many flights are operated by **each airline**.

---

---

## 7. Mixed Concept Questions

### Question 23
Write a query to fetch the **top 3 most expensive flights**.

---

### Question 24
Write a query to fetch flights from **Delhi to Mumbai** ordered by  
ticket price (lowest to highest).

---

### Question 25
Write a query to fetch flights whose duration is **more than 180 minutes**
and ticket price is **less than 600**.

---


```sql
CREATE TABLE flights (
    flight_id INT,
    airline VARCHAR(50),
    source_city VARCHAR(50),
    destination_city VARCHAR(50),
    departure_year INT,
    ticket_price INT,
    aircraft_type VARCHAR(50),
    flight_duration INT
);


---


INSERT INTO flights VALUES
(1, 'IndiGo', 'Delhi', 'Mumbai', 2022, 450, 'Airbus A320', 130),
(2, 'Air India', 'Mumbai', 'Delhi', 2021, 520, 'Boeing 787', 140),
(3, 'Vistara', 'Delhi', 'Bangalore', 2023, 610, 'Airbus A321', 165),
(4, 'IndiGo', 'Chennai', 'Delhi', 2020, 390, 'Airbus A320', 155),
(5, 'Emirates', 'Delhi', 'Dubai', 2019, 1200, 'Boeing 777', 210),
(6, 'Qatar Airways', 'Mumbai', 'Doha', 2018, 1100, 'Airbus A350', 200),
(7, 'Air India', 'Delhi', 'London', 2022, 1500, 'Boeing 787', 480),
(8, 'IndiGo', 'Bangalore', 'Hyderabad', 2023, 320, 'ATR 72', 90),
(9, 'Vistara', 'Mumbai', 'Singapore', 2021, 980, 'Boeing 737', 300),
(10, 'Emirates', 'Delhi', 'New York', 2020, 1800, 'Airbus A380', 900);



