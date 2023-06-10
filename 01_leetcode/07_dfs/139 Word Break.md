# 139 Word Break
[https://leetcode.com/problems/word-break/](https://leetcode.com/problems/word-break/)

## solution

- dfs
```python

```

- 动态规划
```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        l = len(s)
        dp = [True] + [False] * l

        for i in range(1, l+1):
            for j in range(i):
                if dp[j] and s[j:i] in wordDict:
                    dp[i] = True
        return dp[-1]
```

## follow up
[140. Word Break II](https://leetcode.com/problems/word-break-ii/)

- DFS枚举每次切词的位置，使用Memorization优化，每个字符串只用求一遍
```python

```
