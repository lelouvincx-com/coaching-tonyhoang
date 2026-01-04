# 1. Recyclable and Low Fat Products

## Problem

https://leetcode.com/problems/recyclable-and-low-fat-products

## Solution

```sql
select
    product_id
from Products
where low_fats = 'Y' and recyclable = 'Y'
```

Find all product ids where both low_fats and recyclable columns have the value 'Y'.
