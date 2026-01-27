# 15. Percentage Of User Attend A Contest
## Problem
https://leetcode.com/problems/percentage-of-users-attended-a-contest/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with nominator as (
    select r.contest_id, count(r.user_id) as count1
    from Register r 
    left join Users u on r.user_id = u.user_id
    group by r.contest_id
),
denominator as(
    select count(distinct u.user_id) as count2
    from Users u
)
select n.contest_id, round(count1::numeric/count2* 100, 2) as percentage
from nominator n
cross join denominator d
order by percentage desc, contest_id asc
```
we use cte for each denominator and nominator independently, because if we use it in one query, we need to group by contest, so then the amount of percentage for all contest will 100%, since the denominator always must be total user_id, but it will equal nominaotr if we group by like htat, and the result will always be 100%



we use cte to get nominator and denominator and cross join to have an extra column called count2 with total number of all contest, so in that case we could query the percentage for user attending in every contest