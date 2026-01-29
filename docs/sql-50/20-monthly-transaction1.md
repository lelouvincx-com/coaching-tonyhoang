# 20. Monthly Transaction I
## Problem
https://leetcode.com/problems/monthly-transactions-i/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select to_char(date_trunc('month',trans_date)::date, 'YYYY-MM') as month,
    t.country,
    count(*) as trans_count,
    sum(case when t.state = 'approved' then 1 else 0 end) as approved_count,
    sum(t.amount) as trans_total_amount,
    sum(case when t.state = 'approved' then t.amount else 0 end) as  approved_total_amount           
from Transactions t
group by month, t.country
```
In this case, we use date_trunct to group the data by month, and we use to_char so the ouput column only show month and year, no day. we use case when  in approved_count to add 1 if the state is approved, else it will stay 0, same for the total approved amount.