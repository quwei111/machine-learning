# 深度优先搜索

# recursive and nonrecursive

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
Leetcode 543 Diameter of Binary Tree (分治)
Leetcode 124 Binary Tree Maximum Path Sum (分治)
Leetcode 226 Invert Binary Tree (分治)
Leetcode 101 Symmetric Tree (回溯 or 分治)
Leetcode 951 Flip Equivalent Binary Trees (分治)
Leetcode 236 Lowest Common Ancestor of a Binary Tree (相似题：235、1650) (回溯 or 分治)
Leetcode 105 Construct Binary Tree from Preorder and Inorder Traversal (分治)
Leetcode 104 Maximum Depth of Binary Tree (回溯 or 分治)
Leetcode 987 Vertical Order Traversal of a Binary Tree
Leetcode 1485 Clone Binary Tree With Random Pointer
Leetcode 572 Subtree of Another Tree (分治)
Leetcode 863 All Nodes Distance K in Binary Tree
Leetcode 1110 Delete Nodes And Return Forest (分治)
二叉搜索树（BST）：BST特征：中序遍历为单调递增的二叉树，换句话说，根节点的值比左子树任意节点值都大，比右子树任意节点值都小，增删查改均为O（h）复杂度，h为树的高度；注意不是所有的BST题目都需要递归，有的题目只需要while循环即可
Leetcode 230 Kth Smallest element in a BST
Leetcode 98 Validate Binary Search Tree
Leetcode 270 Cloest Binary Search Tree Value
Leetcode 235 Lowest Common Ancestor of a Binary Search Tree
Leetcode 669 Trim a Binary Search Tree (分治)
Leetcode 700 Search in a Binary Search Tree
Leetcode 108 Convert Sorted Array to Binary Search Tree (分治)
Leetcode 333 Largest BST Subtree (与98类似) (分治)
Leetcode 285 Inorder Successor in BST (I, II)
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
