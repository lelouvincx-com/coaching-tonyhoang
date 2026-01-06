# 3.Big Countries

## Problem
https://leetcode.com/problems/big-countries/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select name, population, area 
from World
where area >= 3000000
or population >= 25000000
```
list name, population and area of all countries that are big countries, where area > 3000000 or population >= 25000000