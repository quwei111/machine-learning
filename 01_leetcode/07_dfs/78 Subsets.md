# 78 Subsets
[https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)

Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

## solution

```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        path = []
        res =[]
        self.dfs(nums, path, res, start=0)
        return res

    def dfs(self, nums, path, res, start):
        res.append(path[:])
        if start == len(nums):
            return

        for i in range(start, len(nums)):
            path.append(nums[i])
            self.dfs(nums, path, res, i+1)
            path.pop()
```

## follow up
[90. Subsets II](https://leetcode.com/problems/subsets-ii/)
- 重复数字需要去重
  - 排序，符合的ignore

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        path = []
        res = []
        nums.sort()
        self.dfs(nums, path, res, start=0)
        return res

    def dfs(self, nums, path, res, start):
        res.append(path[:])

        if start >= len(nums):
            return

        for i in range(start, len(nums)):
            if i > start and nums[i] == nums[i-1]:  # 注意需要i>start
                continue
            else:
                path.append(nums[i])
                self.dfs(nums, path, res, i+1)
                path.pop()
```
