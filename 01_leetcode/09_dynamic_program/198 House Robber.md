# 198 House Robber
[https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

## solution

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        if len(nums) <= 2:
            return max(nums)
        
        dp = [0 for _ in range(len(nums)+1)]
        dp[1] = nums[0]
        
        for i in range(2, len(nums)+1):
            dp[i] = max(nums[i-1] + dp[i-2], dp[i-1])
        return dp[-1]
```
