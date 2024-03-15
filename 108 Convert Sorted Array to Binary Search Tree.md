# 108. Convert Sorted Array to Binary Search Tree

---

Easy

Given an integer array `nums` where the elements are sorted in **ascending order**, convert *it to a*

***height-balanced** binary search tree*.

**Example 1:**

![https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg](https://assets.leetcode.com/uploads/2021/02/18/btree1.jpg)

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:

```

![https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg](https://assets.leetcode.com/uploads/2021/02/18/btree2.jpg)

**Example 2:**

![https://assets.leetcode.com/uploads/2021/02/18/btree.jpg](https://assets.leetcode.com/uploads/2021/02/18/btree.jpg)

```
Input: nums = [1,3]
Output: [3,1]
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.

```

**Constraints:**

- `1 <= nums.length <= 104`
- `104 <= nums[i] <= 104`
- `nums` is sorted in a **strictly increasing** order.

# Python

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        # 定义一个内部函数build，用于递归构建二叉搜索树
        def build(node, vals) -> TreeNode:
            if vals:  # 如果vals数组不为空
                mid = len(vals) // 2  # 找到中间元素的索引，作为当前子树的根节点
                node.val = vals[mid]  # 设置当前节点的值为中间元素的值
                # 递归构建左子树，使用中间元素左边的元素数组
                node.left = build(TreeNode(), vals[:mid])
                # 递归构建右子树，使用中间元素右边的元素数组
                node.right = build(TreeNode(), vals[mid + 1:])
                return node  # 返回构建好的当前节点
            else:
                return None  # 如果vals数组为空，则返回None
        # 使用build函数从整个nums数组开始构建BST，并返回根节点
        return build(TreeNode(), nums)
```