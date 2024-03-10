# 349. Intersection of Two Arrays

---

Easy

Given two integer arrays `nums1` and `nums2`, return *an array of their intersection*. Each element in the result must be **unique** and you may return the result in **any order**.

**Example 1:**

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]

```

**Example 2:**

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.

```

**Constraints:**

- `1 <= nums1.length, nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 1000`

# Python

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        set1 = set(nums1)  # 将第一个数组转换为集合，以消除重复元素并提高搜索效率
        set2 = set(nums2)  # 将第二个数组也转换为集合，同样消除重复元素并提高搜索效率

        return list(set1 & set2)  # 返回两个集合的交集
```