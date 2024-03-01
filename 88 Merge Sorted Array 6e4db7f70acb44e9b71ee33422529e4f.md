# 88. Merge Sorted Array

---

Easy

You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be *stored inside the array* `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

**Example 1:**

```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```

**Example 2:**

```
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]
Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].
```

**Example 3:**

```
Input: nums1 = [0], m = 0, nums2 = [1], n = 1
Output: [1]
Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
```

**Constraints:**

- `nums1.length == m + n`
- `nums2.length == n`
- `0 <= m, n <= 200`
- `1 <= m + n <= 200`
- `109 <= nums1[i], nums2[j] <= 109`

# Python

```python
"""
    Do not return anything, modify nums1 in-place instead.
"""
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        # 删除 nums1 中 m 之后的元素，即移除用于合并的额外空间部分。
        del nums1[m:]
        # 将 nums2 的全部元素添加到 nums1 中，此时 nums1 包含了所有待排序的元素。
        nums1 += nums2
        # 对 nums1 进行排序，以确保合并后的数组是有序的。
        nums1.sort()

```

![Screenshot 2024-03-01 at 3.26.17 pm.png](/assets/88%20Merge%20Sorted%20Array%206e4db7f70acb44e9b71ee33422529e4f/Screenshot_2024-03-01_at_3.26.17_pm.png)

# Javascript

```jsx
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function (nums1, m, nums2, n) {
  // 从nums1的第m个元素开始，删除后面所有的元素
  nums1.splice(m, nums1.length - m);
  // 将nums2的所有元素添加到nums1的末尾
  nums1.push(...nums2);
  // 对nums1进行排序，确保合并后的数组是有序的
  nums1.sort((a, b) => a - b);
};
```

![Screenshot 2024-03-01 at 3.25.38 pm.png](/assets/88%20Merge%20Sorted%20Array%206e4db7f70acb44e9b71ee33422529e4f/Screenshot_2024-03-01_at_3.25.38_pm.png)
