# 并查集

- 某些题可以用DFS/BFS，DFS/BFS可能会有找不到某些点，只能用union find
- 并查集常用来解决连通性问题，当我们需要判断两个元素是否在同一个集合里的时候，想到用并查集

```python
class DSU:
    def __init__(self):
        self.par = range(10001)

    def find(self, x):
        if x != self.par[x]:
            self.par[x] = self.find(self.par[x])
        return self.par[x]
    
    def union(self, x, y):
        self.par[self.find(x)] = self.find(y)
    
    def same(self, x, y):
        return self.find(x) == self.find(y)

```
