# 14. Project employees
## Problem
https://leetcode.com/problems/project-employees-i/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select p.project_id, round(avg(e.experience_years),2) as average_years
from Project p
left join Employee e on p.employee_id = e.employee_id
group by p.project_id
```
we use left join to keep all the row of project id, for the round average, we dont need to use ::numeric because the avg() will reurn numeric value even when the column inside it is different, unlike sum(), will return the datatype depend on the column inside it.round() same as sum
