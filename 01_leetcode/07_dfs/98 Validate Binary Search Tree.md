# 98 Validate Binary Search Tree
[https://leetcode.com/problems/validate-binary-search-tree/](https://leetcode.com/problems/validate-binary-search-tree/)

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

- The left subtree  of a node contains only nodes with keys less than the node's key.
- The right subtree of a node contains only nodes with keys greater than the node's key.
- Both the left and right subtrees must also be binary search trees.

## solution

- 注意二叉搜索树定义：根节点大于所有左子树，小于所有右子树。按单个树递归的做法有问题

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def __init__(self):
        self.max_val = float('-inf')

    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        if root is None:
            return True

        l = self.isValidBST(root.left)

        if root.val > self.max_val:
            self.max_val = root.val
        else:
            return False
        
        r = self.isValidBST(root.right)
        return l & r
```

时间复杂度：
空间复杂度：
