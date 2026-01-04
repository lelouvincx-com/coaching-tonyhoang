# 4. Find Customer Referee

## Problem
https://leetcode.com/problems/article-views-i/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select distinct author_id as id
from Views
where viewer_id = author_id
order by author_id
```

Find all author who viewd their own article at least once 