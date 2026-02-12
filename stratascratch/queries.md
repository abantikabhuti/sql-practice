## Difficulty
- [Easy](#easy)
- [Medium](#medium)
- [Hard](#hard)
## Easy
Calculates the difference between the highest salaries in the marketing and engineering departments. Output just the absolute difference in salaries. Tables are db_employee and db_dept.
```sql
select abs(
    (select max(db_employee.salary)
    from db_employee
    join db_dept
    on db_employee.department_id = db_dept.id
    where db_dept.department = 'marketing')
    -
    (select max(db_employee.salary)
    from db_employee
    join db_dept
    on db_employee.department_id = db_dept.id
    where db_dept.department = 'engineering')
) as salary_diff;
```
## Medium
## Hard
