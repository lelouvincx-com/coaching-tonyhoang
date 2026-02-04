# 21.classes with at least 5 students
## Problem
https://leetcode.com/problems/classes-with-at-least-5-students/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select c.class
from Courses c
group by c.class
having count(student) >= 5
```
we group by class and select having class that have more than 5 students