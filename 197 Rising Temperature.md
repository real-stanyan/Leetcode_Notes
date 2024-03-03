# 197. Rising Temperature

---

Easy

Table: `Weather`

```
+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| id            | int     |
| recordDate    | date    |
| temperature   | int     |
+---------------+---------+
id is the column with unique values for this table.
There are no different rows with the same recordDate.
This table contains information about the temperature on a certain day.

```

Write a solution to find all dates' `Id` with higher temperatures compared to its previous dates (yesterday).

Return the result table in **any order**.

The result format is in the following example.

**Example 1:**

```
Input:
Weather table:
+----+------------+-------------+
| id | recordDate | temperature |
+----+------------+-------------+
| 1  | 2015-01-01 | 10          |
| 2  | 2015-01-02 | 25          |
| 3  | 2015-01-03 | 20          |
| 4  | 2015-01-04 | 30          |
+----+------------+-------------+
Output:
+----+
| id |
+----+
| 2  |
| 4  |
+----+
Explanation:
In 2015-01-02, the temperature was higher than the previous day (10 -> 25).
In 2015-01-04, the temperature was higher than the previous day (20 -> 30).
```

# MySQL

```sql
SELECT 
    w1.id                 -- 选择天气记录的ID，其中温度比前一天高
FROM 
    Weather w1, Weather w2  -- 从Weather表进行自连接，创建两个别名w1和w2
WHERE 
    DATEDIFF(w1.recordDate, w2.recordDate) = 1  -- 确保w1的记录日期比w2晚一天
    AND w1.temperature > w2.temperature;       -- 并且w1的温度高于w2的温度
```