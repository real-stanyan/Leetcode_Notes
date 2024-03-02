# 584. Find Customer Referee

---

Easy

Table: `Customer`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| name        | varchar |
| referee_id  | int     |
+-------------+---------+
In SQL, id is the primary key column for this table.
Each row of this table indicates the id of a customer, their name, and the id of the customer who referred them.

```

Find the names of the customer that are **not referred by** the customer with `id = 2`.

Return the result table in **any order**.

The result format is in the following example.

**Example 1:**

```
Input:
Customer table:
+----+------+------------+
| id | name | referee_id |
+----+------+------------+
| 1  | Will | null       |
| 2  | Jane | null       |
| 3  | Alex | 2          |
| 4  | Bill | null       |
| 5  | Zack | 1          |
| 6  | Mark | 2          |
+----+------+------------+
Output:
+------+
| name |
+------+
| Will |
| Jane |
| Bill |
| Zack |
+------+
```

# MySQL

```sql
SELECT name            -- 选择或检索'name'列
FROM Customer          -- 从'Customer'表中
WHERE referee_id IS NULL  -- 条件1: 'referee_id'列的值必须是NULL，
                          -- 表示这些顾客没有推荐人
OR referee_id != 2;    -- 条件2: 或者'referee_id'列的值不等于2，
                          -- 表示这些顾客的推荐人不是ID为2的顾客
```