# 35-Product Price At A Given Date
## Problem
https://leetcode.com/problems/product-price-at-a-given-date/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with before_16 as (
    select *
    from Products p
    where p.change_date <= '2019-08-16'
),
max_date as(
    select b16.product_id, max(b16.change_date) as latest_date
    from before_16 b16
    group by b16.product_id
),
product_before_16 as(
select p.product_id, 
    coalesce(p.new_price,10) as price
from max_date md
right join Products p on md.latest_date= p.change_date
    and md.product_id= p.product_id
where md.product_id is not null 
),
product_after_16 as(
    select p.product_id,
        10 as price
    from max_date md
    right join Products p on md.latest_date= p.change_date
    and md.product_id= p.product_id
    where md.product_id is null 
        and p.product_id not in (select product_id from product_before_16)

)
select *
from product_before_16
union 
select * 
from product_after_16

```
first cte we use to get all the product with the date before 16/8, and get max date of each product before 16 in the second cte.
the next two is we get both product that has the max date before 16 and maxdate after 16. for the before_16. with the after, because the date is after 16 so we need add 10 to every product because before 16 it does not appear. finally, we union the two cte to get the final result of all the products' price before 16/8.