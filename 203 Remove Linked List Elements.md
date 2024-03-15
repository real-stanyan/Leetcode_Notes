# 203. Remove Linked List Elements

---

Easy

Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return *the new head*.

**Example 1:**

![https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg](https://assets.leetcode.com/uploads/2021/03/06/removelinked-list.jpg)

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]

```

**Example 2:**

```
Input: head = [], val = 1
Output: []

```

**Example 3:**

```
Input: head = [7,7,7,7], val = 7
Output: []

```

**Constraints:**

- The number of nodes in the list is in the range `[0, 104]`.
- `1 <= Node.val <= 50`
- `0 <= val <= 50`

# Python

```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        # 创建一个哑节点，它的下一个节点是原链表的头节点
        dummy = ListNode(next=head)
        current = dummy
        
        # 遍历链表
        while current.next:
            if current.next.val == val:
                # 跳过值为val的节点
                current.next = current.next.next
            else:
                current = current.next
        
        # 返回哑节点的下一个节点，即新链表的头节点
        return dummy.next
```