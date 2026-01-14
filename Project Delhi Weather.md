# Weather Dataset – Column Explanation & SQL Competition

---

## Column-wise Explanation

| Column Name    | Explanation                                        |
| -------------- | -------------------------------------------------- |
| date_ist       | Date of the record in Indian Standard Time (IST).  |
| time_ist       | Time of observation in IST.                        |
| location       | Name of the city or place where data was recorded. |
| lat            | Latitude of the location (north–south position).   |
| lon            | Longitude of the location (east–west position).    |
| temp_c         | Temperature measured in degrees Celsius.           |
| humidity       | Percentage of moisture present in the air.         |
| pressure_mb    | Atmospheric pressure in millibars.                 |
| windspeed_kph  | Wind speed measured in kilometers per hour.        |
| condition_text | Short weather condition (Clear, Rain, Fog, etc.).  |
| description    | Detailed description of weather condition.         |
| aqi_index      | Overall Air Quality Index value.                   |
| pm2_5          | Fine particulate matter (PM2.5) level in air.      |
| pm10           | Particulate matter (PM10) level in air.            |
| co             | Carbon Monoxide level.                             |
| no2            | Nitrogen Dioxide level.                            |

---

## SQL Competition Questions

Assume table name: `weather_data`

---

### Beginner Level

1. Display all records for the city "Delhi".
2. Show date, time, and temperature where temperature is above 35°C.
3. List distinct locations available in the dataset.
4. Find all records where humidity is greater than 80%.
5. Display records where weather condition is "Rain".
6. Show top 10 hottest records based on temperature.
7. Find all records where wind speed is more than 20 kph.
8. Count total number of records in the dataset.

---

### Intermediate Level

9. Find the average temperature for each location.
10. Find the maximum and minimum temperature for each city.
11. Show records where AQI is greater than 300.
12. Find cities where PM2.5 level exceeds 60.
13. Count number of weather records per date.
14. Find the city with the highest average AQI.
15. Show records where CO level is higher than NO2 level.
16. Display average humidity for each weather condition.
17. Find dates where average temperature was above 30°C.

---

### Advanced Level

18. For each city, find the hour with the highest temperature.
19. Rank cities based on average AQI (highest first).
20. Find locations where air quality is worse than the overall average AQI.
21. Identify days when PM10 increased compared to the previous day.
22. Find the most common weather condition for each city.
23. Calculate daily temperature difference (max minus min) for each city.
24. Find cities where average wind speed is above overall average wind speed.
25. Create a report showing city, date, average temperature, and average AQI for days where AQI is above 200 and temperature is above 32°C.

