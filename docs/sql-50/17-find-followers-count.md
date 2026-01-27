# 17. Find Followers Count
## Problem
https://leetcode.com/problems/find-followers-count/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select f.user_id, count(distinct f.follower_id) as followers_count
from Followers f
group by f.user_id
order by f.user_id
```
group by user_id to have distinct user id in the output