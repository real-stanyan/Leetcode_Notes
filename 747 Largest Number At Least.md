# 747. Largest Number At Least Twice of Others

---

Easy

You are given an integer array `nums` where the largest integer is **unique**.

Determine whether the largest element in the array is **at least twice** as much as every other number in the array. If it is, return *the **index** of the largest element, or return* `-1` *otherwise*.

**Example 1:**

```
Input: nums = [3,6,1,0]
Output: 1
Explanation: 6 is the largest integer.
For every other number in the array x, 6 is at least twice as big as x.
The index of value 6 is 1, so we return 1.

```

**Example 2:**

```
Input: nums = [1,2,3,4]
Output: -1
Explanation: 4 is less than twice the value of 3, so we return -1.

```

**Constraints:**

- `2 <= nums.length <= 50`
- `0 <= nums[i] <= 100`
- The largest element in `nums` is unique.

# Python

```python
class Solution:
    def dominantIndex(self, nums: List[int]) -> int:
        bigNum = max(nums)  # 找到数组中的最大值

        for num in nums:
            if num == bigNum:
                continue  # 如果当前元素是最大值，继续下一个迭代
            elif bigNum - (num*2) < 0:
                return -1  # 如果最大值小于任一元素的两倍，返回-1
        
        return nums.index(bigNum)  # 如果最大值至少是每个其他元素的两倍，返回最大值的索引
```