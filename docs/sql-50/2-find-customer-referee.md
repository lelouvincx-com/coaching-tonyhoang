# 2. Find Customer Referee

## Problem
https://leetcode.com/problems/find-customer-referee/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select name
from Customer 
where referee_id != 2 or referee_id is null 
```

Find all customer names where there referee_id is null or !=2.