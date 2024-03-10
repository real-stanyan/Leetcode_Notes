# 217. Contains Duplicate

---

Easy

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

```
Input: nums = [1,2,3,1]
Output: true

```

**Example 2:**

```
Input: nums = [1,2,3,4]
Output: false

```

**Example 3:**

```
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

```

**Constraints:**

- `1 <= nums.length <= 105`
- `109 <= nums[i] <= 109`

# Python

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        dic = {}  # 创建一个空字典用于存储每个数字出现的次数

        for num in nums:
            if num in dic:
                dic[num] += 1  # 如果数字已经在字典中，增加其计数
            else:
                dic[num] = 1  # 如果数字不在字典中，添加到字典并设置计数为1
        
        for value in dic.values():
            if value > 1:
                return True  # 如果任何一个数字的计数大于1，返回True表示找到了重复元素
        
        return False  # 如果遍历完字典后没有找到计数大于1的元素，返回False表示没有重复元素
```