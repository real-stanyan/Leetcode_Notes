# 705. Design HashSet

---

Easy

Design a HashSet without using any built-in hash table libraries.

Implement `MyHashSet` class:

- `void add(key)` Inserts the value `key` into the HashSet.
- `bool contains(key)` Returns whether the value `key` exists in the HashSet or not.
- `void remove(key)` Removes the value `key` in the HashSet. If `key` does not exist in the HashSet, do nothing.

**Example 1:**

```
Input
["MyHashSet", "add", "add", "contains", "contains", "add", "contains", "remove", "contains"]
[[], [1], [2], [1], [3], [2], [2], [2], [2]]
Output
[null, null, null, true, false, null, true, null, false]

Explanation
MyHashSet myHashSet = new MyHashSet();
myHashSet.add(1);      // set = [1]
myHashSet.add(2);      // set = [1, 2]
myHashSet.contains(1); // return True
myHashSet.contains(3); // return False, (not found)
myHashSet.add(2);      // set = [1, 2]
myHashSet.contains(2); // return True
myHashSet.remove(2);   // set = [1]
myHashSet.contains(2); // return False, (already removed)
```

**Constraints:**

- `0 <= key <= 106`
- At most `104` calls will be made to `add`, `remove`, and `contains`.

# Python

```python
class MyHashSet:
    # 初始化方法
    def __init__(self):
        self.map = set()  # 使用Python内置的集合类型set来存储元素

    # 添加元素方法
    def add(self, key: int) -> None:
        self.map.add(key)  # 将给定的key添加到集合中

    # 移除元素方法
    def remove(self, key: int) -> None:
        if self.contains(key):  # 首先检查集合中是否包含这个key
            self.map.remove(key)  # 如果包含，则从集合中移除这个key

    # 检查集合中是否包含某个元素的方法
    def contains(self, key: int) -> bool:
        return key in self.map  # 返回一个布尔值，表示集合中是否包含指定的key

# Your MyHashSet object will be instantiated and called as such:
# obj = MyHashSet()
# obj.add(key)
# obj.remove(key)
# param_3 = obj.contains(key)
```