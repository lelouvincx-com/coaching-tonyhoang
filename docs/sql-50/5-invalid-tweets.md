# 4. Find Customer Referee

## Problem
https://leetcode.com/problems/invalid-tweets/description/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15;
```

Find all tweet id where content has a length of >15 cahracters, so we can get the invalids.