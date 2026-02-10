## Easy
Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```mysql
SELECT distinct city 
FROM STATION 
WHERE city NOT REGEXP '^[aeiouAEIOU]'
AND city NOT REGEXP '[aeiouAEIOU]$';
```
Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```mysql
SELECT distinct city
FROM STATION
WHERE city NOT REGEXP '^[aeiouAEIOU].*[aeiouAEIOU]$';
```
Query the Name of any student in **STUDENTS** who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
```mysql
SELECT name FROM STUDENTS 
WHERE marks>75
ORDER BY right (name,3), id;
```
