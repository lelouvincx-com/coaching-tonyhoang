# 22. The number of emploee which report to each employee
## Problem
https://leetcode.com/problems/the-number-of-employees-which-report-to-each-employee/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select e.reports_to as employee_id,
        e2.name,
        count(e.employee_id) as reports_count,
        round(avg(e.age)) as average_age
from Employees e
inner join Employees e2 on e.reports_to = e2.employee_id
where e.reports_to is not null
group by e.reports_to, e2.name
order by e.reports_to
```
we group by report count, and eliminate the nulls, we get the name by self join the employee with reports-to and employee_id to get the name of the manager, not the employee name.