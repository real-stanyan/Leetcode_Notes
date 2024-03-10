# 414. Third Maximum Number

---

Easy

Given an integer array `nums`, return *the **third distinct maximum** number in this array. If the third maximum does not exist, return the **maximum** number*.

**Example 1:**

```
Input: nums = [3,2,1]
Output: 1
Explanation:
The first distinct maximum is 3.
The second distinct maximum is 2.
The third distinct maximum is 1.

```

**Example 2:**

```
Input: nums = [1,2]
Output: 2
Explanation:
The first distinct maximum is 2.
The second distinct maximum is 1.
The third distinct maximum does not exist, so the maximum (2) is returned instead.

```

**Example 3:**

```
Input: nums = [2,2,3,1]
Output: 1
Explanation:
The first distinct maximum is 3.
The second distinct maximum is 2 (both 2's are counted together since they have the same value).
The third distinct maximum is 1.

```

**Constraints:**

- `1 <= nums.length <= 104`
- `231 <= nums[i] <= 231 - 1`

# Python

```python
class Solution:
    def thirdMax(self, nums: List[int]) -> int:
        num_arr = sorted(list(set(nums)))  # 首先，将输入的列表转换为集合以去除重复元素，然后将其转换回列表并进行排序。

        if len(num_arr) < 3:
            return max(num_arr)  # 如果排序后的列表长度小于3，说明没有第三大的数，此时直接返回最大的数。
        else:
            return num_arr[-3]  # 如果列表长度大于等于3，返回从后往前数的第三个元素，即第三大的数。
```