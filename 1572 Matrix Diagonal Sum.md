# 1572. Matrix Diagonal Sum

---

Easy

Given a square matrix `mat`, return the sum of the matrix diagonals.

Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.

**Example 1:**

![https://assets.leetcode.com/uploads/2020/08/14/sample_1911.png](https://assets.leetcode.com/uploads/2020/08/14/sample_1911.png)

```
Input: mat = [[1,2,3],
              [4,5,6],
              [7,8,9]]
Output: 25
Explanation:Diagonals sum: 1 + 5 + 9 + 3 + 7 = 25
Notice that element mat[1][1] = 5 is counted only once.

```

**Example 2:**

```
Input: mat = [[1,1,1,1],
              [1,1,1,1],
              [1,1,1,1],
              [1,1,1,1]]
Output: 8

```

**Example 3:**

```
Input: mat = [[5]]
Output: 5

```

**Constraints:**

- `n == mat.length == mat[i].length`
- `1 <= n <= 100`
- `1 <= mat[i][j] <= 100`

# Python

```python
class Solution:
    def diagonalSum(self, mat: List[List[int]]) -> int:
        sum = 0  # 初始化总和为0

        if len(mat) == 1:
            return mat[0][0]  # 如果矩阵只有一个元素，则直接返回该元素

        for i in range(len(mat)):
            sum += mat[i][i]  # 加上主对角线上的元素
            sum += mat[i][-(i+1)]  # 加上副对角线上的元素
        
        if len(mat) % 2 != 0:
            # 如果矩阵的大小为奇数，中心的元素会被重复计算，因此需要减去一次
            sum -= mat[len(mat) // 2][len(mat) // 2]

        return sum  # 返回对角线元素的总和
```