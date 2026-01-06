# 6. Replace EmployeeID with Unique Identifier

## Problem
https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select eu.unique_id, e.name
from EmployeeUNI eu
right join Employees e on eu.id = e.id
```
Left Join : get all values in left table , including nulls and join wiht matching values only in right table\

Right Join: opposite with left join

Inner Join: onl get non-null values in both

Full Join: get null values in both tables