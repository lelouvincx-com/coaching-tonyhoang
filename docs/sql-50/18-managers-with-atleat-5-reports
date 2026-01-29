# 18. Managers with at least 5 reports 
## Problem
https://leetcode.com/problems/managers-with-at-least-5-direct-reports/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with getManagerId as(
    select e.managerId, count(e.id) as countId
    from Employee e
    group by e.managerId
    having count(e.id) >=5
)
select e.name
from Employee e
join getManagerId gmi on e.id = gmi.managerId
```
we use a cte to get Manager Id distinct, and count to get manager that has more than 5 employees.
in the main query, we join the cte with employee , we must use id for employee because if we join by managerId, the result we select name will return all disitnct employees name, not manager. also, we do not use distinct on select name in case we have two different manager but with similar name.
