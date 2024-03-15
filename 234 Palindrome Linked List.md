# 234. Palindrome Linked List

---

Easy

Given the `head` of a singly linked list, return `true` *if it is a palindrome or* false *otherwise*.

**Example 1:**

![https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg](https://assets.leetcode.com/uploads/2021/03/03/pal1linked-list.jpg)

```
Input: head = [1,2,2,1]
Output: true
```

**Example 2:**

![https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg](https://assets.leetcode.com/uploads/2021/03/03/pal2linked-list.jpg)

```
Input: head = [1,2]
Output: false
```

**Constraints:**

- The number of nodes in the list is in the range `[1, 105]`.
- `0 <= Node.val <= 9`

# Python

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        arr = []  # 初始化一个空数组，用于存储链表的值

        while head != None:
            arr.append(head.val)  # 遍历链表，将每个节点的值添加到数组中
            head = head.next  # 移动到下一个节点
        
        # 计算前半部分数组，使用ceil函数确保中间的元素在奇数长度的链表中被包括
        front = arr[:ceil(len(arr)/2)]
        # 计算后半部分数组，并将其反转，以便于和前半部分进行比较
        back = arr[ceil(-len(arr)//2):][::-1]

        for i in range(len(front)):
            if front[i] != back[i]:
                return False  # 如果前半部分和后半部分的任一元素不相同，则链表不是回文

        return True  # 如果所有对应元素都相同，则链表是回文
```