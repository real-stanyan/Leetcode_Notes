# 1211. Queries Quality and Percentage

---

Easy

Table: `Queries`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| query_name  | varchar |
| result      | varchar |
| position    | int     |
| rating      | int     |
+-------------+---------+
This table may have duplicate rows.
This table contains information collected from some queries on a database.
Theposition column has a value from1 to500.
Therating column has a value from1 to5. Query withrating less than 3 is a poor query.

```

We define query `quality` as:

> The average of the ratio between query rating and its position.
> 

We also define `poor query percentage` as:

> The percentage of all queries with rating less than 3.
> 

Write a solution to find each `query_name`, the `quality` and `poor_query_percentage`.

Both `quality` and `poor_query_percentage` should be **rounded to 2 decimal places**.

Return the result table in **any order**.

The result format is in the following example.

**Example 1:**

```
Input:
Queries table:
+------------+-------------------+----------+--------+
| query_name | result            | position | rating |
+------------+-------------------+----------+--------+
| Dog        | Golden Retriever  | 1        | 5      |
| Dog        | German Shepherd   | 2        | 5      |
| Dog        | Mule              | 200      | 1      |
| Cat        | Shirazi           | 5        | 2      |
| Cat        | Siamese           | 3        | 3      |
| Cat        | Sphynx            | 7        | 4      |
+------------+-------------------+----------+--------+
Output:
+------------+---------+-----------------------+
| query_name | quality | poor_query_percentage |
+------------+---------+-----------------------+
| Dog        | 2.50    | 33.33                 |
| Cat        | 0.66    | 33.33                 |
+------------+---------+-----------------------+
Explanation:
Dog queries quality is ((5 / 1) + (5 / 2) + (1 / 200)) / 3 = 2.50
Dog queries poor_ query_percentage is (1 / 3) * 100 = 33.33

Cat queries quality equals ((2 / 5) + (3 / 3) + (4 / 7)) / 3 = 0.66
Cat queries poor_ query_percentage is (1 / 3) * 100 = 33.33
```

# MySQL

```sql
-- 选择查询名称和计算每个查询的质量得分及差评百分比
SELECT
    query_name, -- 查询名称
    ROUND(
				SUM(rating / position) / COUNT(*)
		, 2) AS quality, -- 计算每个查询的质量得分，平均每个位置的评分，保留两位小数
    ROUND(
        COUNT(CASE WHEN rating < 3 THEN 1 ELSE NULL END) / COUNT(*) * 100
    , 2) AS poor_query_percentage -- 计算评分低于3的查询占总查询的百分比，保留两位小数
FROM
    Queries -- 从查询表中
WHERE
    query_name IS NOT NULL -- 只包括查询名称非空的记录
GROUP BY
    query_name -- 根据查询名称分组
```