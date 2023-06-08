# 124 Binary Tree Maximum Path Sum
[https://leetcode.com/problems/binary-tree-maximum-path-sum/](https://leetcode.com/problems/binary-tree-maximum-path-sum/)

A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any non-empty path.

## solution

- 首先计算单个节点的最大路径 val + max(l, r)
- 但只能发生一次，整体路径最大：max(res, l + r + root.val)
- 在1的计算过程中，找到2最大的

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def __init__(self):
        self.res = float('-inf')
    
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        self.dfs(root)
        return self.res

    def dfs(self, root):
        if root is None:
            return 0
        
        l = self.dfs(root.left)
        r = self.dfs(root.right)
        self.res = max(self.res, l + r + root.val)
        return max(root.val + max(l, r), 0)
```
