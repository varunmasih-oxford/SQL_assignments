# Weather Dataset – SQL Answer Key

Assume table name: `weather_data`

---

## Beginner Level Answers

### 1. Display all records for the city "Delhi"

```sql
SELECT *
FROM weather_data
WHERE location = 'Delhi';
```

### 2. Date, time, and temperature where temperature > 35°C

```sql
SELECT date_ist, time_ist, temp_c
FROM weather_data
WHERE temp_c > 35;
```

### 3. List distinct locations

```sql
SELECT DISTINCT location
FROM weather_data;
```

### 4. Records where humidity > 80%

```sql
SELECT *
FROM weather_data
WHERE humidity > 80;
```

### 5. Weather condition is "Rain"

```sql
SELECT *
FROM weather_data
WHERE condition_text = 'Rain';
```

### 6. Top 10 hottest records

```sql
SELECT *
FROM weather_data
ORDER BY temp_c DESC
LIMIT 10;
```

### 7. Wind speed > 20 kph

```sql
SELECT *
FROM weather_data
WHERE windspeed_kph > 20;
```

### 8. Total number of records

```sql
SELECT COUNT(*) AS total_records
FROM weather_data;
```

---

## Intermediate Level Answers

### 9. Average temperature for each location

```sql
SELECT location, AVG(temp_c) AS avg_temp
FROM weather_data
GROUP BY location;
```

### 10. Maximum and minimum temperature for each city

```sql
SELECT location,
       MAX(temp_c) AS max_temp,
       MIN(temp_c) AS min_temp
FROM weather_data
GROUP BY location;
```

### 11. AQI greater than 300

```sql
SELECT *
FROM weather_data
WHERE aqi_index > 300;
```

### 12. Cities where PM2.5 > 60

```sql
SELECT DISTINCT location
FROM weather_data
WHERE pm2_5 > 60;
```

### 13. Number of records per date

```sql
SELECT date_ist, COUNT(*) AS record_count
FROM weather_data
GROUP BY date_ist;
```

### 14. City with highest average AQI

```sql
SELECT location, AVG(aqi_index) AS avg_aqi
FROM weather_data
GROUP BY location
ORDER BY avg_aqi DESC
LIMIT 1;
```

### 15. CO level higher than NO2 level

```sql
SELECT *
FROM weather_data
WHERE co > no2;
```

### 16. Average humidity by weather condition

```sql
SELECT condition_text, AVG(humidity) AS avg_humidity
FROM weather_data
GROUP BY condition_text;
```

### 17. Dates where average temperature > 30°C

```sql
SELECT date_ist, AVG(temp_c) AS avg_temp
FROM weather_data
GROUP BY date_ist
HAVING AVG(temp_c) > 30;
```

---

## Advanced Level Answers

### 18. Hour with highest temperature for each city

```sql
SELECT location, time_ist, temp_c
FROM weather_data w1
WHERE temp_c = (
    SELECT MAX(temp_c)
    FROM weather_data w2
    WHERE w1.location = w2.location
);
```

### 19. Rank cities by average AQI

```sql
SELECT location,
       AVG(aqi_index) AS avg_aqi,
       RANK() OVER (ORDER BY AVG(aqi_index) DESC) AS aqi_rank
FROM weather_data
GROUP BY location;
```

### 20. Locations worse than overall average AQI

```sql
SELECT location, AVG(aqi_index) AS avg_aqi
FROM weather_data
GROUP BY location
HAVING AVG(aqi_index) > (
    SELECT AVG(aqi_index) FROM weather_data
);
```

### 21. Days when PM10 increased compared to previous day

```sql
SELECT date_ist, location, pm10
FROM (
    SELECT date_ist, location, pm10,
           LAG(pm10) OVER (PARTITION BY location ORDER BY date_ist) AS prev_pm10
    FROM weather_data
) t
WHERE pm10 > prev_pm10;
```

### 22. Most common weather condition for each city

```sql
SELECT location, condition_text
FROM (
    SELECT location, condition_text,
           COUNT(*) AS cnt,
           RANK() OVER (PARTITION BY location ORDER BY COUNT(*) DESC) AS rnk
    FROM weather_data
    GROUP BY location, condition_text
) t
WHERE rnk = 1;
```

### 23. Daily temperature difference for each city

```sql
SELECT location, date_ist,
       MAX(temp_c) - MIN(temp_c) AS temp_difference
FROM weather_data
GROUP BY location, date_ist;
```

### 24. Cities with above-average wind speed

```sql
SELECT location, AVG(windspeed_kph) AS avg_wind
FROM weather_data
GROUP BY location
HAVING AVG(windspeed_kph) > (
    SELECT AVG(windspeed_kph) FROM weather_data
);
```

### 25. Report: city, date, avg temp, avg AQI (AQI > 200 and temp > 32°C)

```sql
SELECT location, date_ist,
       AVG(temp_c) AS avg_temp,
       AVG(aqi_index) AS avg_aqi
FROM weather_data
GROUP BY location, date_ist
HAVING AVG(aqi_index) > 200
   AND AVG(temp_c) > 32;
