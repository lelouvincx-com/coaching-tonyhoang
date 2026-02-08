# 30. Consecutive Numbers
## Problem
https://leetcode.com/problems/consecutive-numbers/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select distinct l1.num as ConsecutiveNums
from Logs l1 
left join Logs l2 on l1.num=l2.num 
            and l1.id +1= l2.id
left join Logs l3 on l1.num = l3.num
            and l1.id +1 = l2.id
            and l2.id+ 1 =l3.id
where l1.id is not null 
    and l2.id is not null
    and l3.id is not null
```
we get all id rows into columns that identical with the number by self left join the table three times, so we can get null values to get numbers that have three consecutive id.
after that, we use where query to filter out the null
if we do not use left join, all the null values are avoided and we do not know which number has three consecutive ids.