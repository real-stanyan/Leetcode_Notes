# 577. Employee Bonus

---

Easy

Table: `Employee`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| empId       | int     |
| name        | varchar |
| supervisor  | int     |
| salary      | int     |
+-------------+---------+
empId is the column with unique values for this table.
Each row of this table indicates the name and the ID of an employee in addition to their salary and the id of their manager.

```

Table: `Bonus`

```
+-------------+------+
| Column Name | Type |
+-------------+------+
| empId       | int  |
| bonus       | int  |
+-------------+------+
empId is the column of unique values for this table.
empId is a foreign key (reference column) to empId from the Employee table.
Each row of this table contains the id of an employee and their respective bonus.

```

Write a solution to report the name and bonus amount of each employee with a bonus **less than** `1000`.

Return the result table in **any order**.

The result format is in the following example.

**Example 1:**

```
Input:
Employee table:
+-------+--------+------------+--------+
| empId | name   | supervisor | salary |
+-------+--------+------------+--------+
| 3     | Brad   | null       | 4000   |
| 1     | John   | 3          | 1000   |
| 2     | Dan    | 3          | 2000   |
| 4     | Thomas | 3          | 4000   |
+-------+--------+------------+--------+
Bonus table:
+-------+-------+
| empId | bonus |
+-------+-------+
| 2     | 500   |
| 4     | 2000  |
+-------+-------+
Output:
+------+-------+
| name | bonus |
+------+-------+
| Brad | null  |
| John | null  |
| Dan  | 500   |
+------+-------+
```

# MySQL

```sql
SELECT
    E.name,  -- 选择员工的姓名
    B.bonus  -- 选择员工的奖金
FROM 
    Employee E LEFT JOIN Bonus B  -- 从Employee表进行左连接到Bonus表
ON
    E.empId = B.empId  -- 连接条件是两个表中的empId字段相匹配
WHERE
    B.bonus < 1000  -- 筛选出奖金小于1000的记录
OR 
    B.bonus IS NULL  -- 或者奖金为NULL的记录
```