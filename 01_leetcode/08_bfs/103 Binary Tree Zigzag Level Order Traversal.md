# 103 Binary Tree Zigzag Level Order Traversal
[https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

## solution
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:
            return []

        level = [root]
        res = []
        flag = 0

        while level:
            this_level = []
            this_res = []

            for node in level:
                this_res.append(node.val)

                if node.left:
                    this_level.append(node.left)
                if node.right:
                    this_level.append(node.right)
            
            if flag % 2 == 1:
                this_res = this_res[::-1]
            
            res.append(this_res)
            level = this_level
            flag += 1
        return res
```
时间复杂度：
