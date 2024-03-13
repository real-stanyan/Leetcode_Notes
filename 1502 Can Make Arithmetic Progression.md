# 1502. Can Make Arithmetic Progression From Sequence

---

Easy

A sequence of numbers is called an **arithmetic progression** if the difference between any two consecutive elements is the same.

Given an array of numbers `arr`, return `true` *if the array can be rearranged to form an **arithmetic progression**. Otherwise, return* `false`.

**Example 1:**

```
Input: arr = [3,5,1]
Output: true
Explanation:We can reorder the elements as [1,3,5] or [5,3,1] with differences 2 and -2 respectively, between each consecutive elements.
```

**Example 2:**

```
Input: arr = [1,2,4]
Output: false
Explanation:There is no way to reorder the elements to obtain an arithmetic progression.
```

**Constraints:**

- `2 <= arr.length <= 1000`
- `106 <= arr[i] <= 106`

# Python

```python
class Solution:
    def canMakeArithmeticProgression(self, arr: List[int]) -> bool:
        arr.sort()  # 首先对数组进行排序

        diff = arr[1] - arr[0]  # 计算数组中第一个和第二个元素之间的差值，作为等差数列的公差

        for i in range(len(arr) - 1):  # 遍历排序后的数组
            if arr[i+1] - arr[i] != diff:  # 如果相邻两个元素之间的差值不等于公差
                return False  # 则数组不能形成等差数列，返回False
        
        return True  # 如果所有相邻元素之间的差值都等于公差，则数组可以形成等差数列，返回True
```