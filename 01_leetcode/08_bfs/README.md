# 广度优先搜索

- 解决遍历树的最短路径
- use BFS for unweighted graphs and use Dijkstra's algorithm for weighted graphs. Dijkstra is similar to BFS, the difference is using priority queue instead of queue. The priority will pop the element with higher priority


基础知识：
常见的BFS用来解决什么问题？
- 简单图（有向无向皆可）的最短路径长度，注意是长度而不是具体的路径
- 拓扑排序 
- 遍历一个图（或者树）

BFS基本模板（需要记录层数或者不需要记录层数）
多数情况下时间复杂度空间复杂度都是O（N+M），N为节点个数，M为边的个数
基于树的BFS：不需要专门一个set来记录访问过的节点

```python
bfs = [target.val]
visited = set([target.val])
for k in range(K):
    bfs = [y for x in bfs for y in conn[x] if y not in visited]
    visited |= set(bfs)
```
