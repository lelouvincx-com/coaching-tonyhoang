# 26. Product Sales Analysis III
## Problem
https://leetcode.com/problems/product-sales-analysis-iii/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with get_earliest_year as(
    select s.product_id, min(s.year) as first_year
    from Sales s 
    group by s.product_id
)
select s.product_id,
    gey.first_year,
    s.quantity,
    s.price
from Sales s
inner join get_earliest_year gey on s.product_id= gey.product_id and
s.year= gey.first_year
```
we use a cte to get the earliest year of each product.
in the main query, because the instruction requires to output earliest year for each sale, not product and since same products could be sale multiple times, we will not group by product to keep the data raw.