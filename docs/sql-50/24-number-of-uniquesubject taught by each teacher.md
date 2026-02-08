# 24. number of unique subjcet taught by each teacher 
## Problem
https://leetcode.com/problems/number-of-unique-subjects-taught-by-each-teacher/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select t.teacher_id, count(distinct t.subject_id) as cnt
from Teacher t
group by t.teacher_id
```
count distinct to not duplicate the subjects count 