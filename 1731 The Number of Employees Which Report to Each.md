# 1731. The Number of Employees Which Report to Each Employee

---

Easy

Table: `Employees`

```
+-------------+----------+
| Column Name | Type     |
+-------------+----------+
| employee_id | int      |
| name        | varchar  |
| reports_to  | int      |
| age         | int      |
+-------------+----------+
employee_id is the column with unique values for this table.
This table contains information about the employees and the id of the manager they report to. Some employees do not report to anyone (reports_to is null).

```

For this problem, we will consider a **manager** an employee who has at least 1 other employee reporting to them.

Write a solution to report the ids and the names of all **managers**, the number of employees who report **directly** to them, and the average age of the reports rounded to the nearest integer.

Return the result table ordered by `employee_id`.

The result format is in the following example.

**Example 1:**

```
Input:
Employees table:
+-------------+---------+------------+-----+
| employee_id | name    | reports_to | age |
+-------------+---------+------------+-----+
| 9           | Hercy   | null       | 43  |
| 6           | Alice   | 9          | 41  |
| 4           | Bob     | 9          | 36  |
| 2           | Winston | null       | 37  |
+-------------+---------+------------+-----+
Output:
+-------------+-------+---------------+-------------+
| employee_id | name  | reports_count | average_age |
+-------------+-------+---------------+-------------+
| 9           | Hercy | 2             | 39          |
+-------------+-------+---------------+-------------+
Explanation: Hercy has 2 people report directly to him, Alice and Bob. Their average age is (41+36)/2 = 38.5, which is 39 after rounding it to the nearest integer.
```

# MySQL

```sql
-- 选择员工ID、姓名、直接下属数量和下属的平均年龄
SELECT
    e1.employee_id, -- 员工ID
    e1.name, -- 员工姓名
    count(e2.employee_id) as reports_count, -- 计算直接报告给该员工的下属数量
    round(avg(e2.age)) as average_age -- 计算所有直接下属的平均年龄，并进行四舍五入
FROM
    Employees e1 -- 从员工表中选择员工（作为管理者）
INNER JOIN 
    Employees e2 -- 再次从员工表中选择员工（作为下属）
ON
    e1.employee_id = e2.reports_to -- 通过员工的上级ID与其他员工的ID进行内连接
GROUP BY
    e1.employee_id -- 根据员工ID分组
ORDER BY
    e1.employee_id -- 根据员工ID进行升序排序
```