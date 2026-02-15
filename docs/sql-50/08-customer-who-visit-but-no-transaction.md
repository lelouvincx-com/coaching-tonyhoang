# 8. Customer who visit but did not make any transaction

## Problem
https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select v.customer_id, count(*) as count_no_trans
from Visits v
left join Transactions t on v.visit_id = t.visit_id
where t.transaction_id is null
group by 1
```
we use left join in this table to give priority to the Visit table, which will scan all row in the left to get the matching value with row in Transaction, and if there is no matching transaction_id, it will be null in that column, which help us to find custiomer who visit but did not make any transaction. 