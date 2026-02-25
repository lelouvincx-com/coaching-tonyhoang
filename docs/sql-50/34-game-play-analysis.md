# 34- game play analysis
## Problem
https://leetcode.com/problems/game-play-analysis-iv/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with first_day as(
    select a.player_id, min(a.event_date) as first_login_day
    from Activity a
    group by a.player_id
),
second_day as(
    select a.player_id, 
        fd.first_login_day, 
        a.event_date
    from first_day fd
    left join Activity a on fd.player_id = a.player_id
)
select round(sum(case 
when sd.first_login_day = sd.event_date - interval '1 day' then 1
else 0 
end)::numeric/count(distinct sd.player_id),2) as fraction
from second_day sd
```
first we get the first cte to get all first log in day group by player id, after that we join using player id to have second day with first day in one row. then we use case when to get the nominator: +1 if first login day is one day b4 the event date els 0, then divide by countitn all distinct player_id.