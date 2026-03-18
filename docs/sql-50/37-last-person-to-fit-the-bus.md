# 32- exhange seats
## Problem
https://leetcode.com/problems/last-person-to-fit-in-the-bus/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with running_total as (
    select q.turn,
    q.person_id,
    q.person_name,
    q.weight,
    sum(q.weight) over (order by q.turn) as total_weight 
    from Queue q
),
all_in_bus as(
    select rt.turn,
    rt.person_name
    from running_total rt 
    where rt.total_weight <= 1000
)
select aib.person_name
from all_in_bus aib
order by aib.turn desc
limit 1
```
- we use running total method to create a new column that add weight to total people in bus order by the turn that each person enter the bus
-we select all people in the bus then order by their turn limit 1 to get the last person that enter the bus.