# 7.Product Sales Analysis

## Problem
https://leetcode.com/problems/product-sales-analysis-i/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select p.product_name , s.year, s.price
from Sales s
join Product p on s.product_id = p.product_id
group by s.sale_id,1,2,3
```
group by saleid first to remove duplicates of salesid, because the instruction rquire to analayse info for each sale_id