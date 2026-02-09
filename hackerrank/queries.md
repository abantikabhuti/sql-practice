Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```sql
SELECT distinct city 
FROM STATION 
WHERE city NOT REGEXP '^[aeiouAEIOU]'
AND city NOT REGEXP '[aeiouAEIOU]$';
```
Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```sql
SELECT distinct city
FROM STATION
WHERE city NOT REGEXP '^[aeiouAEIOU].*[aeiouAEIOU]$';
```

