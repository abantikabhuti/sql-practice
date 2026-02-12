## Difficulty
- [Easy](#easy)
- [Medium](#medium)
- [Hard](#hard)
## Easy
1. Calculates the difference between the highest salaries in the marketing and engineering departments. Output just the absolute difference in salaries. Tables are db_employee and db_dept.
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
2. Management wants to analyze only employees with official job titles. Find the job titles of the employees with the highest salary. If multiple employees have the same highest salary, include all their job titles. Tables are worker and title.
```sql
select title.worker_title as best_paid_title
from title
join worker
on title.worker_ref_id = worker.worker_id
where worker.salary = (
    select max(worker.salary)
    from worker
    join title
    on worker.worker_id = title.worker_ref_id
    where title.worker_title is not null
)
order by best_paid_title;
```
## Medium
## Hard
