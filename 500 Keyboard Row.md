# 500. Keyboard Row

---

Easy

Given an array of strings `words`, return *the words that can be typed using letters of the alphabet on only one row of American keyboard like the image below*.

In the **American keyboard**:

- the first row consists of the characters `"qwertyuiop"`,
- the second row consists of the characters `"asdfghjkl"`, and
- the third row consists of the characters `"zxcvbnm"`.

![https://assets.leetcode.com/uploads/2018/10/12/keyboard.png](https://assets.leetcode.com/uploads/2018/10/12/keyboard.png)

**Example 1:**

```
Input: words = ["Hello","Alaska","Dad","Peace"]
Output: ["Alaska","Dad"]

```

**Example 2:**

```
Input: words = ["omk"]
Output: []

```

**Example 3:**

```
Input: words = ["adsdf","sfd"]
Output: ["adsdf","sfd"]

```

**Constraints:**

- `1 <= words.length <= 20`
- `1 <= words[i].length <= 100`
- `words[i]` consists of English letters (both lowercase and uppercase).

# Python

```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        # 定义键盘的三行字母为三个集合
        source = [
            set('qwertyuiop'),
            set('asdfghjkl'),
            set('zxcvbnm')
        ]

        output = []  # 初始化输出列表，用于存放结果

        for word in words:  # 遍历每个单词
            word_set = set(word.lower())  # 将单词转换为小写，并转换为集合，以便进行集合操作
            # 检查单词的字母是否全部位于键盘的同一行中
            # any函数用于检查是否至少有一个条件为真
            # issubset方法检查word_set是否为source中某一行的子集
            if any(word_set.issubset(row) for row in source):
                output.append(word)  # 如果是，将单词添加到输出列表中

        return output  # 返回结果列表
```