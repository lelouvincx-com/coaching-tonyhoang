# 29- TriangleJudgement
## Problem
https://leetcode.com/problems/triangle-judgement/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select t.x,
    t.y,
    t.z,
    case 
        when x + y > z and x + z > y and y + z > x then 'Yes'
        else 'No'
    end as triangle
from Triangle t
```
we use and for three case because all two random line must always be bigger than the other to form a triangle.