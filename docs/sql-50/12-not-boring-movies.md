# 12. Not Boring Movies 

## Problem
https://leetcode.com/problems/not-boring-movies/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select c.id, c.movie, c.description, c.rating 
from Cinema c
where c.id %2 =1
and  c.description != 'boring'
order by c.rating desc;
```
find movies that has id odd and dscription different from boring