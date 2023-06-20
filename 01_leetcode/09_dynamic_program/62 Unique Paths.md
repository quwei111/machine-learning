# 62 Unique Paths
[]()


## solution

```python

```

## follow up
[63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)

```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        n_row = len(obstacleGrid)
        n_col = len(obstacleGrid[0])

        if obstacleGrid[n_row - 1][n_col - 1] == 1 or obstacleGrid[0][0] == 1:
            return 0

        res = [[0 for _ in range(n_col)] for _ in range(n_row)]
        for i in range(n_row):
            if obstacleGrid[i][0] == 1:
                break
            res[i][0] = 1
        
        for i in range(n_col):
            if obstacleGrid[0][i] == 1:
                break
            res[0][i] = 1
        
        for i in range(1, n_row):
            for j in range(1, n_col):
                if obstacleGrid[i][j] == 1:
                    continue
                else:
                    res[i][j] = res[i-1][j] + res[i][j-1]
        return res[-1][-1]
```
