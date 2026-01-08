# 9. Average time of process per machine

## Problem
https://leetcode.com/problems/average-time-of-process-per-machine/?envType=study-plan-v2&envId=top-sql-50

## Solution

```sql
WITH per_process AS (
  SELECT
    machine_id,
    process_id,
    MAX(CASE WHEN activity_type = 'end'   THEN timestamp END)
    - MAX(CASE WHEN activity_type = 'start' THEN timestamp END) AS duration
  FROM Activity
  GROUP BY machine_id, process_id
)
SELECT
  machine_id,
  ROUND(AVG(duration)::numeric, 3) AS processing_time
FROM per_process
GROUP BY machine_id;


```
we use a cte at the beginning to get all the duration of all process specifically, we group by process+machine first in this case. for the timestamp part, on each row, the start row will have start time but the end time will be null, and the opposite goes for end time row too. so if you do not use aggregate function, you will subtract null values with eachother, so to get the start value for start time and end for end, you need an aggregate to avoid getting null values subtract eachother . that is to get duration of each process

after that, we group all by machine_id, get the average process time of each machine , round up by three decimal places.