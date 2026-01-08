# 10.Employee Bonus 

## Problem
https://leetcode.com/problems/employee-bonus/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select e.name, b.bonus
from Employee e
left join Bonus b on e.empId = b.empId
where b.bonus < 1000 or b.bonus is null
```

we use left join in this case because we get all record in emploee table to join with bonus, even if the employee does not have bonus, it will be shown as null for the row. so at that time we can get all employee with bonus < 1000 or bonus is null.