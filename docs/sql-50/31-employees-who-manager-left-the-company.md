# 31- Employees whose manager left the company 
## Problem
https://leetcode.com/problems/employees-whose-manager-left-the-company/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select e1.employee_id
from Employees e1
left join Employees e2 on e1.manager_id = e2.employee_id
where e1.salary <30000
and e2.employee_id is null
and e1.manager_id is not null
order by e1.employee_id
```
we use self left join to keep all the employee who used to be the manager, even if they have left the company. after that, we filter the query using where to get employees salary <30000 and not an employee anymore, also, they must appear in the manager column so e1.manager_id cannot be null