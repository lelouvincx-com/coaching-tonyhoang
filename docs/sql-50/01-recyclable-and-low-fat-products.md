# 6.Replace Employees With Unique Identifier

## Problem

https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select eu.unique_id, e.name
from EmployeeUNI eu
right join Employees e on eu.id = e.id
```

Left join: get all values in left table, including null when join with the right table. For the right table, only get matching values with the left one.

Right join: opposite with Left join

Full join: get all values including nulls in both left and right table and match them with each other.

Inner join: only get non-null values in both tables 
