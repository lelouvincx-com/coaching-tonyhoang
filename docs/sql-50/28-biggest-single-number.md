# 28.Biggest Single Number
## Problem
https://leetcode.com/problems/biggest-single-number/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with get_single as(
    select num
    from MyNumbers mn
    group by mn.num
    having count(mn.num) = 1
)
select max(num) as num
from get_single

```
