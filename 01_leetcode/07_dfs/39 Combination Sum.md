# 39 Combination Sum
[https://leetcode.com/problems/combination-sum/](https://leetcode.com/problems/combination-sum/)

Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the 
frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

## solution
- 有放回+控制重复
- 回溯时，每次的开始start仍然由i进行，小于0时进行剪枝（因此需要排序）
- 寻找某个target的dfs，都是target-item来递归。回溯是否需要再加回去？

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        path = []
        candidates.sort(reverse=True)
        self.dfs(path, res, candidates, target, start=0)
        return res

    def dfs(self, path, res, candidates, target, start):
        if target < 0:
            return
        
        if target == 0:
            res.append(path[:])
            return
        
        for i in range(start, len(candidates)):
            path.append(candidates[i])
            self.dfs(path, res, candidates, target - candidates[i], i)  # 有放回i, 无放回i+1
            path.pop()
```


## follow up

[40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
- 无放回，控制开始的index每次i+1，而不是i
- 控制重复，采用排序加剪枝。for循环横向遍历，对同一层使用过的元素跳过

```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []
        path = []
        start = 0
        candidates.sort(reverse=True)
        self.dfs(candidates, target, path, res, start)
        return res
    
    def dfs(self, candidates, target, path, res, start):
        if target < 0:
            return
        if target == 0:
            res.append(path[:])
            return
        
        for i in range(start, len(candidates)):
            if i > start and candidates[i] == candidates[i-1]:
                continue
            path.append(candidates[i])            
            self.dfs(candidates, target-candidates[i], path, res, i+1)
            path.pop()
```

[216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)
- 不重复，开始从i+1
- 规定了选取的个数

```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        res = []
        path = []
        self.dfs(k, n, res, path, start=1)
        return res

    def dfs(self, k, n, res, path, start):
        if len(path) == k:
            if n == 0:
                res.append(path[:])
            return
        
        for val in range(start, 10):
            path.append(val)
            self.dfs(k, n-val, res, path, val+1)
            path.pop()
```
