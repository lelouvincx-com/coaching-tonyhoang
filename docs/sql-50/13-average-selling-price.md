# 13. Average Selling Price

## Problem
https://leetcode.com/problems/average-selling-price/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
select p.product_id,
coalesce(round(sum(p.price*us.units)/sum(us.units)::numeric,2),0) as average_price
from Prices p
left join UnitsSold us on p.product_id = us.product_id 
                and p.start_date <= us.purchase_date
                and p.end_date >= us.purchase_date
group by p.product_id
```
first, we use left join to make sure that all product id will be kept in the result even if it is not sold , and it will appear as null, so we use coalesce to show the result as 0 instead of null. the average selling price is : sum(price*unit)/sum(units)