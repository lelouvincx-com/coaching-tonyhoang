# 17. Customers Who Bought All Products
## Problem
https://leetcode.com/problems/customers-who-bought-all-products/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with get_total_product as(
    select count(p.product_key) as total
    from Product p 
)
select c.customer_id
from Customer c
cross join get_total_product gtp
group by c.customer_id, gtp.total
having count(distinct c.product_key)= gtp.total
```
we get the cte to get total distinct products
in the main query, we cross join with customer table to able to compare the number of products bought by the customers and the total products to see if that customer bought all of them.
also, in the having query we need to count distinct because one custmer can buy one product multiple times, so you need distinct to remove duplicates.