# 19. Confirmation Rate
## Problem
https://leetcode.com/problems/confirmation-rate/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with getNominator as(
    select c.user_id, count(c.user_id) as confirmedNum
    from Confirmations c
    where c.action = 'confirmed'
    group by 1
)
select s.user_id, COALESCE(round(gn.confirmedNum::numeric/count(*),2), 0) as confirmation_rate
from Signups s
left join Confirmations c on s.user_id = c.user_id
left join getNominator gn on s.user_id= gn.user_id
group by s.user_id, gn.confirmedNum


```
we use cte to get the nominator of confirmation rate
we use left join for signup table because it will keep the id of member who did not even sign up or being confirmed, so that we could use coalesce to turn it from null to 0 in the output.