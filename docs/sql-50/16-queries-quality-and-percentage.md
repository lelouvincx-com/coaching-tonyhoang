# 16. queries quality and percentage
## Problem
https://leetcode.com/problems/queries-quality-and-percentage/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with get_poor_rating as(
    select q0.query_name, count(q0.rating) as poor_rating
    from Queries q0
    where q0.rating <3
    group by q0.query_name
)
select q.query_name, round(avg(q.rating::numeric/q.position),2) as quality,
COALESCE(round(poor_rating::numeric/count(q.rating) *100,2),0) as poor_query_percentage
from Queries q
left join get_poor_rating gpr on q.query_name = gpr.query_name
group by q.query_name, gpr.poor_rating
```
we use a cte to count all the query that has poor quality , group by query name, because if you get both denominator and nominator in one query, it the denominator will not work. you need to use left join so that the query that does not have poor rating will be note as nul and turn it to 0.