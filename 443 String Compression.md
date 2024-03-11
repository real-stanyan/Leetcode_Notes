# 443. String Compression

---

Medium

Given an array of characters `chars`, compress it using the following algorithm:

Begin with an empty string `s`. For each group of **consecutive repeating characters** in `chars`:

- If the group's length is `1`, append the character to `s`.
- Otherwise, append the character followed by the group's length.

The compressed string `s` **should not be returned separately**, but instead, be stored **in the input character array `chars`**. Note that group lengths that are `10` or longer will be split into multiple characters in `chars`.

After you are done **modifying the input array,** return *the new length of the array*.

You must write an algorithm that uses only constant extra space.

**Example 1:**

```
Input: chars = ["a","a","b","b","c","c","c"]
Output: Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]
Explanation: The groups are "aa", "bb", and "ccc". This compresses to "a2b2c3".

```

**Example 2:**

```
Input: chars = ["a"]
Output: Return 1, and the first character of the input array should be: ["a"]
Explanation: The only group is "a", which remains uncompressed since it's a single character.

```

**Example 3:**

```
Input: chars = ["a","b","b","b","b","b","b","b","b","b","b","b","b"]
Output: Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].
Explanation: The groups are "a" and "bbbbbbbbbbbb". This compresses to "ab12".
```

**Constraints:**

- `1 <= chars.length <= 2000`
- `chars[i]` is a lowercase English letter, uppercase English letter, digit, or symbol.

# Python

```python
class Solution:
    def compress(self, chars: List[str]) -> int:
        init = chars[0]  # 初始化为第一个字符
        arr = []  # 用于存储分段的字符数组
        cuts = []  # 记录每个不同字符的分割点
        output = []  # 最终输出的压缩后字符数组

        for i in range(len(chars)):
            if chars[i] != init:  # 当字符改变时
                cuts.append(i)  # 在改变点记录位置
                init = chars[i]  # 更新当前字符为新字符
        cuts.append(len(chars))  # 添加最后一个字符的位置

        if len(cuts) != 0:
            arr.append(chars[:cuts[0]])  # 添加第一段字符

            for i in range(1, len(cuts)):
                arr.append(chars[cuts[i - 1]:cuts[i]])  # 根据分割点添加后续字符段
            
        for i in arr:
            if len(i) == 1:
                output.append(i[0])  # 如果字符段长度为1，只添加字符本身
            else:
                output.append(i[0])  # 添加字符
                if len(i) >= 10:
                    for letter in list(str(len(i))):  # 如果字符长度大于等于10，逐个添加数字字符
                        output.append(letter)
                else:
                    output.append(str(len(i)))  # 如果字符长度小于10，直接添加表示长度的数字字符

        chars.clear()  # 清空原字符数组
        chars.extend(output)  # 将压缩后的数组覆盖原数组
```