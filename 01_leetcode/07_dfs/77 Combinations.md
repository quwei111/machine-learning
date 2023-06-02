# 77 Combinations
[https://leetcode.com/problems/combinations/](https://leetcode.com/problems/combinations/)

Given two integers n and k, return all possible combinations of k numbers chosen from the range [1, n].

You may return the answer in any order.

## solution

回溯
- 整体输出结果、单次尝试的path、本次选择的选项
- 本题回溯时，注意不需要重复项，通过控制**开始index**不从前面选

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        res = []
        path = []
        self.dfs(res, path, n, k, start=1)
        return res

    def dfs(self, res, path, n, k, start):
        if len(path) == k:
            res.append(path[:])  # [:]和下面的copy保留一个即可
            return
        
        for i in range(start, n+1):            
            path.append(i)
            self.dfs(res, path.copy(), n, k, i+1)
            path.pop()
```

时间复杂度：
空间复杂度：
