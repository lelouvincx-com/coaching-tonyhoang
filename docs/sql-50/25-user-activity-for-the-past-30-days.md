# 25.User Activity For The Past 30 Days
## Problem
https://leetcode.com/problems/user-activity-for-the-past-30-days-i/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
select a.activity_date as day,
    count(distinct a.user_id) as active_users
from Activity a
where a.activity_date between '2019-07-27'::date - INTERVAL '29 days' and '2019-07-27'::date
group by a.activity_date

```
we user -interval to get 30days ear the required days, and use ::date to turn string into date.
in the slect phase we get distinct to not duplicate the userid count