# 32- exhange seats
## Problem
https://leetcode.com/problems/exchange-seats/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select s1.id,
case 
    when s1.id % 2 != 0 then coalesce(s3.student,s1.student)
    when s1.id %2 = 0 then s2.student
end as student
from Seat s1
left join Seat s2 on s1.id = s2.id +1
left join Seat s3 on s1.id = s3.id -1
```
we self join s1 with s2 and 3 to get 3 consecutive id in a row and their name also, wih odd number, we get student naame in s3 table which is the bigger id, and with even number we get in s2 which is the smaller id number compare to s1. the coalesce is used for the odd id that is the biggest one, which we will keep the same name, no swapping id.