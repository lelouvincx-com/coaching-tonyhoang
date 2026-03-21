# 32- exhange seats
## Problem
https://leetcode.com/problems/restaurant-growth/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with seperate as(
    select c.visited_on,
    sum(c.amount) as amount
    from Customer c
    group by c.visited_on
),
row_number as(
select c.visited_on,
sum(c.amount) over (order by c.visited_on
                    rows between 6 preceding and current row) as amount,
round(avg(c.amount) over (order by c.visited_on
                    rows between 6 preceding and current row),2) as average_amount,
ROW_NUMBER() OVER (ORDER BY c.visited_on) AS rn
from seperate c
)
select rn.visited_on, rn.amount, rn.average_amount
from row_number rn
where rn >6
```
- use the first cte to group the table by distinct day
-the second table use moving average and sum to calculate total and average on current day and 6 days before
- on the main query, show output with only days that have enough 6 preceding days.