# 深度优先搜索

主函数用于遍历所有的搜索位置，判断是否可以开始搜索，如果 可以即在辅函数进行搜索。辅函数则负责深度优先搜索的递归调用

- 一维 or 二维(二叉树) dfs
- 记录状态的dfs (图)

基于图的DFS: 和BFS一样一般需要一个set来记录访问过的节点，避免重复访问造成死循环; Word XXX 系列面试中非常常见，例如word break，word ladder，word pattern，word search

基于排列组合的DFS: 其实与图类DFS方法一致，但是排列组合的特征更明显

记忆化搜索（DFS + Memoization Search）：算是用递归的方式实现动态规划，递归每次返回时同时记录下已访问过的节点特征，避免重复访问同一个节点，可以有效的把指数级别的DFS时间复杂度降为多项式级别; 注意这一类的DFS必须在最后有返回值（分治法），不可以用回溯法; for循环的dp题目都可以用记忆化搜索的方式写，但是不是所有的记忆化搜索题目都可以用for循环的dp方式写。


## recursive and nonrecursive

graph1 = {
    'A': ['B', 'S'],
    'B': ['A'],
    'C': ['D', 'E', 'F', 'S'],
    'D': ['C'],
    'E': ['C', 'H'],
    'F': ['C', 'G'],
    'G': ['F', 'S'],
    'H': ['E', 'G'],
    'S': ['A', 'C', 'G']
}


def dfs(graph, node):
    visited = [False] * len(graph)
    dfs_utils(node, visited)


def dfs_utils(graph, node, visited):
    visited[node] = True
    for i in graph[node]:
        if visited[i] == False:
            dfs_utils(graph, i, visited)


def dfs1(graph, node, visited):
    if node not in visited:
        visited.append(node)
        for n in graph[node]:
            dfs1(graph, n, visited)
    return visited


def dfs2(graph, node):
    visited = [node]
    stack = [node]
    while stack:
        node = stack[-1]
        if node not in visited:
            visited.extend(node)
        remove_from_stack = True
        for next in graph[node]:
            if next not in visited:
                stack.extend(next)
                remove_from_stack = False
                break
        if remove_from_stack:
            stack.pop()
    return visited


def dfs_iterative(graph, start_vertex):
    visited = set()
    traversal = []
    stack = [start_vertex]
    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            traversal.append(vertex)
            stack.extend(reversed(graph[vertex]))   # add vertex in the same order as visited
    return traversal

if __name__ == '__main__':
    print(dfs(graph1, 'A', []))
    print(dfs2(graph1, 'A'))



基础知识：
常见的DFS用来解决什么问题？
- 1 图中（有向无向皆可）的符合某种特征（比如最长）的路径以及长度
- 2 排列组合
- 3 遍历一个图（或者树）
- 4 找出图或者树中符合题目要求的全部方案

DFS基本模板（需要记录路径，不需要返回值 and 不需要记录路径，但需要记录某些特征的返回值）
除了遍历之外多数情况下时间复杂度是指数级别，一般是O(方案数×找到每个方案的时间复杂度)
递归题目都可以用非递归迭代的方法写，但一般实现起来非常麻烦
基于树的DFS：需要记住递归写前序中序后序遍历二叉树的模板


## 矩阵的DFS

四个方向初始化和遍历
```python
self.directions = [(1,0),(-1,0),(0,1),(0,-1)]

for direction in self.directions:
    x, y = i + direction[0], j + direction[1]
```

DFS辅助函数
```python
def dfs(self, i, j, matrix, visited, m, n):
    if visited: 
        # return or return a value
    for dir in self.directions:
        x, y = i + direction[0], j + direction[1]
        if x < 0 or x >= m or y < 0 or y >= n or matrix[x][y] <= matrix[i][j] (or a condition you want to skip this round):
            continue
        # do something like
        visited[i][j] = True
        # explore the next level like
        self.dfs(x, y, matrix, visited, m, n)
```

# 树
- preorder/ inorder/ postorder/ level


```
#https://stackoverflow.com/questions/2598437/how-to-implement-a-binary-tree

class tree_node:
    def __init__(self,value):
        self.left=None
        self.right=None
        self.val=value


class binary_tree:
    def __init__(self):
        self.root=None

    def add(self,value):
        if self.root==None:
            self.root=tree_node(value)
        else:
            self._add(value,self.root)

    def _add(self,value,node):

        if value<node.val:
            if node.left!=None:
                self._add(value,node.left)
            else:
                node.left=tree_node(value)

        else:
            if node.right!=None:
                self._add(value,node.right)
            else:
                node.right=tree_node(value)

    def find(self,value):
        if self.root!=None:
            return self._find(value,self.root)
        else:
            print("None")


    def _find(self,value,node):
        if node.val==value:
            print("I am in")
            return node
        elif (node.val>value and node.left!=None):
            self._find(value,node.left)
        elif (node.val<value and node.right!=None):
            self._find(value,node.right)
        print("I am not in")


    def print(self):
        if self.root!=None:
            self._print(self.root)



    def _print(self,node):
        if node!=None:
            self._print(node.left)
            print('i am',node.val)
            self._print(node.right)

    def delete(self):
        self.root=None


tree=binary_tree()
tree.add(3)
tree.add(1)
tree.add(4)
tree.add(8)
tree.add(2)
tree.print()
tree.find(3)

```




# 回溯 backtracking
需要记录节点状态的深度优先搜索。记录节点状态的原因是

- N叉树
- 无返回

回溯中递归函数的项：
- paths 路径，已经做过的选择
- 选择列表，当期可以做出的选择
- res 结果列表

每个节点既有路径也有选择。

[Backtrack Summary: General Solution for 10 Questions](https://leetcode.com/problems/permutations/solutions/18284/backtrack-summary-general-solution-for-10-questions-python-combination-sum-subsets-permutation-palindrome/)


# 树
- preorder/ inorder/ postorder/ level

- [了解]空间优化 Morris traversal: iterative approach to leverage preorder traversal that the the entire left subtree would be placed between the node and its right subtree

```
#https://stackoverflow.com/questions/2598437/how-to-implement-a-binary-tree

class tree_node:
    def __init__(self,value):
        self.left=None
        self.right=None
        self.val=value


class binary_tree:
    def __init__(self):
        self.root=None

    def add(self,value):
        if self.root==None:
            self.root=tree_node(value)
        else:
            self._add(value,self.root)

    def _add(self,value,node):

        if value<node.val:
            if node.left!=None:
                self._add(value,node.left)
            else:
                node.left=tree_node(value)

        else:
            if node.right!=None:
                self._add(value,node.right)
            else:
                node.right=tree_node(value)

    def find(self,value):
        if self.root!=None:
            return self._find(value,self.root)
        else:
            print("None")


    def _find(self,value,node):
        if node.val==value:
            print("I am in")
            return node
        elif (node.val>value and node.left!=None):
            self._find(value,node.left)
        elif (node.val<value and node.right!=None):
            self._find(value,node.right)
        print("I am not in")


    def print(self):
        if self.root!=None:
            self._print(self.root)



    def _print(self,node):
        if node!=None:
            self._print(node.left)
            print('i am',node.val)
            self._print(node.right)

    def delete(self):
        self.root=None


tree=binary_tree()
tree.add(3)
tree.add(1)
tree.add(4)
tree.add(8)
tree.add(2)
tree.print()
tree.find(3)

```
