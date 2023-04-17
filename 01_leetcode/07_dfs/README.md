# 深度优先搜索

主函数用于遍历所有的搜索位置，判断是否可以开始搜索，如果 可以即在辅函数进行搜索。辅函数则负责深度优先搜索的递归调用

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
常见的DFS用来解决什么问题？(1) 图中（有向无向皆可）的符合某种特征（比如最长）的路径以及长度（2）排列组合（3） 遍历一个图（或者树）（4）找出图或者树中符合题目要求的全部方案
DFS基本模板（需要记录路径，不需要返回值 and 不需要记录路径，但需要记录某些特征的返回值）
除了遍历之外多数情况下时间复杂度是指数级别，一般是O(方案数×找到每个方案的时间复杂度)
递归题目都可以用非递归迭代的方法写，但一般实现起来非常麻烦
基于树的DFS：需要记住递归写前序中序后序遍历二叉树的模板


基于图的DFS: 和BFS一样一般需要一个set来记录访问过的节点，避免重复访问造成死循环; Word XXX 系列面试中非常常见，例如word break，word ladder，word pattern，word search。
Leetcode 341 Flatten Nested List Iterator (339 364)
Leetcode 394 Decode String
Leetcode 51 N-Queens (I II基本相同)
Leetcode 291 Word Pattern II (I为简单的Hashmap题)
Leetcode 126 Word Ladder II （I为BFS题目）
Leetcode 93 Restore IP Addresses
Leetcode 22 Generate Parentheses
Leetcode 856 Score of Parentheses
Leetcode 301 Remove Invalid Parentheses
Leetcode 37 Sodoku Solver
Leetcode 212 Word Search II （I, II）
Leetcode 1087 Brace Expansion
Leetcode 399 Evaluate Division
Leetcode 1274 Number of Ships in a Rectangle
Leetcode 1376 Time Needed to Inform All Employees
Leetcode 694 Number of Distinct Islands
Leetcode 131 Palindrome Partitioning
基于排列组合的DFS: 其实与图类DFS方法一致，但是排列组合的特征更明显
Leetcode 17 Letter Combinations of a Phone Number
Leetcode 39 Combination Sum（I, II, III相似， IV为动态规划题目）
Leetcode 78 Subsets （I, II 重点在于如何去重）
Leetcode 46 Permutation (I, II 重点在于如何去重)
Leetcode 77 Combinations (I, II 重点在于如何去重)
Leetcode 698 Partition to K Equal Sum Subsets
Leetcode 526 Beautiful Arrangement (similar to 46)
记忆化搜索（DFS + Memoization Search）：算是用递归的方式实现动态规划，递归每次返回时同时记录下已访问过的节点特征，避免重复访问同一个节点，可以有效的把指数级别的DFS时间复杂度降为多项式级别; 注意这一类的DFS必须在最后有返回值（分治法），不可以用回溯法; for循环的dp题目都可以用记忆化搜索的方式写，但是不是所有的记忆化搜索题目都可以用for循环的dp方式写。
Leetcode 139 Word Break II
Leetcode 72 Edit Distance
Leetcode 377 Combination Sum IV
Leetcode 1235 Maximum Profit in Job Scheduling
Leetcode 1335 Minimum Difficulty of a Job Schedule
Leetcode 1216 Valid Palindrome III
Leetcode 97 Interleaving String
Leetcode 472 Concatenated Words
Leetcode 403 Frog Jump
Leetcode 329 Longest Increasing Path in a Matrix


# 回溯 backtracking
