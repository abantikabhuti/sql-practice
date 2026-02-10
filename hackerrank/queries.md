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
Write a query identifying the type of each record in the **TRIANGLES** table using its three side lengths. Output one of the following statements for each record in the table:

- Equilateral: It's a triangle with 3 sides of equal length.
- Isosceles: It's a triangle with 2 sides of equal length.
- Scalene: It's a triangle with 3 sides of differing lengths.
- Not A Triangle: The given values of A, B, and C don't form a triangle.
```sql
SELECT
CASE
when a+b<=c or a+c<=b or b+c<=a
    then 'Not A Triangle'
when a=b and b=c
    then 'Equilateral'
when a=b or a=c or b=c
    then 'Isosceles'
else 'Scalene'
end as triangle_type
from TRIANGLES;

```
