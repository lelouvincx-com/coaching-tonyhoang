# 23. Primary department for each employee
## Problem
https://leetcode.com/problems/primary-department-for-each-employee/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with one_dep as(
    select e.employee_id
    from Employee e
    group by e.employee_id
    having count(e.department_id) =1
),
more_dep as(
    select e.employee_id, e.department_id
    from Employee e
    where e.primary_flag = 'Y'

)
select e.employee_id, e.department_id
from one_dep od
join Employee e on od.employee_id = e.employee_id
union 
select * 
from more_dep
```
we use to cte, one to get employee with one department with N status, and one to get the others employee wih more than one department and status Y . after that, we get the result my union two query of onedep and moredep together to get the full result 