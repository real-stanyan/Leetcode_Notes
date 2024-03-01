# 26. Remove Duplicates from Sorted Array

---

Easy

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates **[in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**. Then return *the number of unique elements in* `nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}

```

If all assertions pass, then your solution will be **accepted**.

**Example 1:**

```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

```

**Example 2:**

```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

```

**Constraints:**

- `1 <= nums.length <= 3 * 104`
- `100 <= nums[i] <= 100`
- `nums` is sorted in **non-decreasing** order.

# Python

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        # 使用set去除nums中的重复元素，然后将结果转换为列表，并进行排序
        dummy = sorted(list(set(nums)))
        # 清空原列表
        nums.clear() 
        # 将去重且排序后的列表元素扩展到原列表中
        nums.extend(dummy)  

        # 返回处理后的列表长度
        return len(nums)
```

# Javascript

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var removeDuplicates = function(nums) {
    // 使用Set去重，然后用扩展操作符(...)转换为数组，并对数组进行排序
    const dummy = [...new Set(nums)].sort((a, b) => a - b);
    // 清空原数组
    nums.length = 0;
    // 将去重且排序后的数组元素推入原数组
    nums.push(...dummy);

    // 返回处理后的数组长度
    return nums.length;
};
```