# 102 Binary Tree Level Order Traversal
[https://leetcode.com/problems/binary-tree-level-order-traversal/](https://leetcode.com/problems/binary-tree-level-order-traversal/)

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

## solution
- 如果需要区分bfs的每一层，需要每一层更新队列；如果不区分每层，采用队列的push、pop

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None:
            return None

        level = [root]
        res = []
        while level:
            this_res = []
            this_level = []
            for node in level:
                this_res.append(node.val)
                if node.left:                    
                    this_level.append(node.left)
                if node.right:                    
                    this_level.append(node.right)
            level = this_level
            res.append(this_res)
        return res
```

时间复杂度：


## follow-up
- [429. N-ary Tree Level Order Traversal](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if root is None:
            return []
        
        level = [root]
        res = []

        while level:
            this_level = []
            this_res = []

            for node in level:
                this_res.append(node.val)

                for child in node.children:
                    this_level.append(child)
            
            level = this_level
            res.append(this_res)
        return res
```