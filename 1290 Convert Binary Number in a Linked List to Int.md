# 1290. Convert Binary Number in a Linked List to Integer

---

Easy

Given `head` which is a reference node to a singly-linked list. The value of each node in the linked list is either `0` or `1`. The linked list holds the binary representation of a number.

Return the *decimal value* of the number in the linked list.

The **most significant bit** is at the head of the linked list.

**Example 1:**

![https://assets.leetcode.com/uploads/2019/12/05/graph-1.png](https://assets.leetcode.com/uploads/2019/12/05/graph-1.png)

```
Input: head = [1,0,1]
Output: 5
Explanation: (101) in base 2 = (5) in base 10
```

**Example 2:**

```
Input: head = [0]
Output: 0
```

**Constraints:**

- The Linked List is not empty.
- Number of nodes will not exceed `30`.
- Each node's value is either `0` or `1`.

# Python

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def getDecimalValue(self, head: ListNode) -> int:
        output = ''  # 初始化一个空字符串，用来拼接链表中的节点值

        while head != None:  # 当链表不为空时循环
            output += str(head.val)  # 将当前节点的值转换为字符串并拼接到output字符串
            head = head.next  # 移动到链表的下一个节点
        
        return int(output, 2)  # 将拼接好的二进制字符串转换成十进制整数并返回
```