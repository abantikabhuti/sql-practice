## Difficulty
- [Hard](#hard)
- [Medium](#medium)
- [Easy](#easy)
## Hard
## Medium
1. Generate the following two result sets:

- Query an alphabetically ordered list of all names in **OCCUPATIONS**, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: `AnActorName(A)`, `ADoctorName(D)`, `AProfessorName(P)`, and `ASingerName(S)`.
- Query the number of ocurrences of each occupation in **OCCUPATIONS**. Sort the occurrences in ascending order, and output them in the following format:
  
   `There are a total of [occupation_count] [occupation]s.`

    where `[occupation_count]` is the number of occurrences of an occupation in **OCCUPATIONS** and `[occupation]` is the lowercase occupation name. If more than one Occupation has the same `[occupation_count]`, they should be ordered alphabetically.
```sql
SELECT CONCAT(name, '(', LEFT(occupation,1), ')')
AS new_column
FROM OCCUPATIONS
ORDER BY name;

SELECT CONCAT('There are a total of ', COUNT(*), ' ', LOWER(Occupation), 's.')
FROM OCCUPATIONS
GROUP BY occupation
ORDER BY COUNT(*) ASC, occupation ASC;
```
## Easy
1. Query the list of CITY names from **STATION** that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```mysql
SELECT distinct city 
FROM STATION 
WHERE city NOT REGEXP '^[aeiouAEIOU]'
AND city NOT REGEXP '[aeiouAEIOU]$';
```
2. Query the list of CITY names from **STATION** that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```mysql
SELECT distinct city
FROM STATION
WHERE city NOT REGEXP '^[aeiouAEIOU].*[aeiouAEIOU]$';
```
3. Query the Name of any student in **STUDENTS** who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
```mysql
SELECT name FROM STUDENTS 
WHERE marks>75
ORDER BY right (name,3), id;
```
4. Write a query identifying the type of each record in the **TRIANGLES** table using its three side lengths. Output one of the following statements for each record in the table:

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
5. Samantha was tasked with calculating the average monthly salaries for all employees in the **EMPLOYEES** table, but did not realize her keyboard's 0 key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error and round it up to the next integer.
```sql
SELECT ceil(avg(salary) - avg(REPLACE(salary, '0', '')))
FROM EMPLOYEES;
```
6. We define an employee's total earnings to be their monthly salary X months worked, and the maximum total earnings to be the maximum total earnings for any employee in the **Employee** table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.
```sql
SELECT max(salary*months), count(*)
FROM Employee
WHERE salary*months = (
    SELECT max(salary*months) 
    FROM Employee
    );
```
7. Given the **CITY** and **COUNTRY** tables, query the sum of the populations of all cities where the **CONTINENT** is 'Asia'.

**Note:** CITY.CountryCode and COUNTRY.Code are matching key columns.
```sql
SELECT sum(CITY.population)
FROM CITY
JOIN COUNTRY
ON CITY.countrycode = COUNTRY.code
WHERE COUNTRY.continent='Asia';
```
8. Given the **CITY** and **COUNTRY** tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
```sql
SELECT COUNTRY.continent, floor(avg(CITY.population))
FROM COUNTRY
JOIN CITY
ON COUNTRY.code = CITY.countrycode
GROUP BY COUNTRY.continent;
```
