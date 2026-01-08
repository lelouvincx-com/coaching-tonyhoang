# 11.Students and examinations

## Problem
https://leetcode.com/problems/students-and-examinations/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select s.student_id, s.student_name, sub.subject_name, count(e.subject_name) as attended_exams
from Students s 
CROSS JOIN Subjects sub
left join Examinations e on s.student_id = e.student_id
AND e.subject_name = sub.subject_name
group by s.student_id, s.student_name, sub.subject_name
order by s.student_id, sub.subject_name
```
we use cross join so that the output can still show results of every subject of each student, even they did not attend it and the row will jave a value of 0. next, we use left join because you will go through all columns in student table, and count all examinations they attend. we use e.subject_name = sub.subject_name to remove duplicates count 