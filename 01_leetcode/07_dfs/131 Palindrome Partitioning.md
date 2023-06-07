# 131 Palindrome Partitioning
[https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)

Given a string s, partition s such that every substring of the partition is a palindrome. Return all possible palindrome partitioning of s.

## solution

- 切割问题其实是一种组合问题
- 为了不重复切割同一位置，start_index来做标记下一轮递归的起始位置(切割线)

```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        path = []
        res = []
        self.dfs(s, path, res, start=0)
        return res
    
    def dfs(self, s, path, res, start):
        if start >= len(s):
            res.append(path[:])
            return
        
        for i in range(start, len(s)):
            temp = s[start:i+1]
            if temp == temp[::-1]:
                path.append(temp)
                self.dfs(s, path, res, i+1)
                path.pop()
            else:
                continue
```

## follow up
[132. Palindrome Partitioning II](https://leetcode.com/problems/palindrome-partitioning-ii/description/)

```python

```
