# 46 Permutation
[https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

## solution


```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        path = []
        res = []
        used = [False] * len(nums)
        self.dfs(nums, path, res, used)
        return res

    def dfs(self, nums, path, res, used):
        if len(path) == len(nums):
            res.append(path[:])
            return
        
        for i in range(0, len(nums)):
            if used[i]:
                continue
            path.append(nums[i])
            used[i] = True
            self.dfs(nums, path, res, used)
            path.pop()
            used[i] = False
```

## follow up

[47. Permutations II](https://leetcode.com/problems/permutations-ii/)

```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        path = []
        res = []
        nums.sort()
        used = [False] * len(nums)
        self.dfs(nums, path, res, used)
        return res

    def dfs(self, nums, path, res, used):
        if len(path) == len(nums):
            res.append(path[:])
            return
        
        for i in range(0, len(nums)):
            if used[i]:
                continue
            if i > 0 and nums[i] == nums[i-1] and not used[i-1]:
                continue
            path.append(nums[i])
            used[i] = True
            self.dfs(nums, path, res, used)
            path.pop()
            used[i] = False
```
