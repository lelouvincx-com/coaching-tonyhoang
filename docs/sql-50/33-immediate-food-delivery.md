# 33- immediate food delivery II
## Problem
https://leetcode.com/problems/immediate-food-delivery-ii/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with cus_first_order as(
    select d.customer_id, min(order_date) as first_order_date
    from Delivery d
    group by d.customer_id
),
all_first_order as(
    select *
    from cus_first_order cfo
    join Delivery d on cfo.first_order_date = d.order_date
    and cfo.customer_id = d.customer_id 
),
nominator as(
select sum(CASE
        WHEN afo.first_order_date= afo.customer_pref_delivery_date then 1
        ELSE 0
       END) as nominator
from all_first_order afo
)
SELECT 
    ROUND(
        SUM(CASE 
                WHEN afo.first_order_date = afo.customer_pref_delivery_date THEN 1 
                ELSE 0 
            END)::numeric *100
        / COUNT(*), 2
    ) AS immediate_percentage
from all_first_order afo


```
we make the first cte cus_first_orderto list all the first order group by customer, then we can see that with customer_id + first_order_date, it is a composite and unique key, so we join with Delivery table to get all customer first orderdate + its perfered_deliverydate so we can get the nominator at the next step. for the nominator, if if first order date is the same with prefered date, it will  plus 1 else it will stay 0.
Finally on the main query, we just need to round it to 2 decimal places, but the difference is we dont *100 after rounding , we round the nominator first.
for example, the result of percentage is 0.375. if we mutiply before rounding, the result will be 37.5. However, if we multiply after rounding, the result is 38, and it is not correct with the instruction of the excercise.