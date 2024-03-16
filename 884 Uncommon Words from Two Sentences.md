# 884. Uncommon Words from Two Sentences

---

Easy

A **sentence** is a string of single-space separated words where each word consists only of lowercase letters.

A word is **uncommon** if it appears exactly once in one of the sentences, and **does not appear** in the other sentence.

Given two **sentences** `s1` and `s2`, return *a list of all the **uncommon words***. You may return the answer in **any order**.

**Example 1:**

```
Input: s1 = "this apple is sweet", s2 = "this apple is sour"
Output: ["sweet","sour"]
```

**Example 2:**

```
Input: s1 = "apple apple", s2 = "banana"
Output: ["banana"]
```

**Constraints:**

- `1 <= s1.length, s2.length <= 200`
- `s1` and `s2` consist of lowercase English letters and spaces.
- `s1` and `s2` do not have leading or trailing spaces.
- All the words in `s1` and `s2` are separated by a single space.

# Python

```python
class Solution:
    def uncommonFromSentences(self, s1: str, s2: str) -> List[str]:
        # 将两个句子分割成单词列表
        s1, s2 = list(s1.split(' ')), list(s2.split(' '))
        map1, map2 = {}, {}  # 初始化两个字典用于存储两个句子中单词出现的次数

        output = []  # 初始化输出列表，用于存储结果中的不常见单词

        # 遍历第一个句子中的单词，计数并存入map1
        for word in s1:
            if word in map1:
                map1[word] += 1
            else:
                map1[word] = 1
        
        # 遍历第二个句子中的单词，计数并存入map2
        for word in s2:
            if word in map2:
                map2[word] += 1
            else:
                map2[word] = 1
            
        # 检查第一个句子中的不常见单词
        for k, v in map1.items():
            if v == 1 and k not in map2:
                output.append(k)
                
        # 检查第二个句子中的不常见单词
        for k, v in map2.items():
            if v == 1 and k not in map1:
                output.append(k)
        
        return output  # 返回不常见单词列表
```