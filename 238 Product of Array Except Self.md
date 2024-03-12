# 238. Product of Array Except Self

---

Medium

Given an integer array `nums`, return *an array* `answer` *such that* `answer[i]` *is equal to the product of all the elements of* `nums` *except* `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**

```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]

```

**Example 2:**

```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]

```

**Constraints:**

- `2 <= nums.length <= 105`
- `30 <= nums[i] <= 30`
- The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

# Python

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        output = []  # 初始化输出数组
        pros = prod(nums)  # 计算输入数组所有元素的乘积

        for i in range(len(nums)):
            if nums[i] == 0:
                # 如果当前元素为0，计算除当前元素外的所有元素的乘积
                # 这是因为0除以任何数都是0，因此我们需要重新计算乘积，不包括这个0
                output.append(prod(nums[0:i] + nums[i+1:len(nums)]))
            else:
                # 如果当前元素不是0，直接用总乘积除以当前元素得到除自身外的乘积
                output.append(pros // nums[i])

        return output  # 返回输出数组
```