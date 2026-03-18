# 32- exhange seats
## Problem
https://leetcode.com/problems/movie-rating/description/?envType=study-plan-v2&envId=top-sql-50
## Solution

```sql
with count_total_rate as(
    select mr.user_id, count(movie_id) as rate_count
    from MovieRating mr
    group by mr.user_id
),
user_name as(
    select u.name as results
    from MovieRating mr 
    join Users u on mr.user_id = u.user_id
    join count_total_rate ctr on mr.user_id= ctr.user_id
    where rate_count =(select max(ctr.rate_count)
        from count_total_rate ctr)
    group by mr.user_id,u.name
    order by u.name
    limit 1
),
average_rate as (
    select mr.movie_id, avg(mr.rating) as avg_rating
    from MovieRating mr 
    where EXTRACT(YEAR FROM mr.created_at) = 2020
        and EXTRACT(MONTH FROM mr.created_at) = 02
    group by mr.movie_id
),
highest_rate as(
    select m.title
    from average_rate ar 
    join Movies m on ar.movie_id = m.movie_id
    where avg_rating = (select max(avg_rating)
        from average_rate 
        )
    order by m.title
    limit 1

)
select *
from user_name

union all

select *
from highest_rate



```
- the query is divided into two parts
-the first part find the user who rate most movies by count ratings for each user
-if multiple users has the same count, we use order by and limt 1 to get lexicographically smallest letter 
-the second part find the movies with highest rating in feburary 2020
-union the two part together for the final output