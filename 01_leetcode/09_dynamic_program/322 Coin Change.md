# 322 Coin Change
[https://leetcode.com/problems/coin-change/](https://leetcode.com/problems/coin-change/)

## solution

- 完全背包
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        # 获得amount为i需要的最少硬币数
        dp = [float('inf') for _ in range(amount+1)]
        dp[0] = 0

        for i in coins:  # 物品
            for j in range(i, amount+1):  # 背包
                if dp[j-i] != float('inf'):
                    dp[j] = min(dp[j], dp[j-i]+1)
        
        if dp[amount] == float('inf'):
            return -1
        return dp[amount]

```
