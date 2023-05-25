# 101 Symmetric Tree
[https://leetcode.com/problems/symmetric-tree/](https://leetcode.com/problems/symmetric-tree/)

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

## solution

- 注释掉的部分，到导致结果错误。因此没有往下判断，写法上是一个前序遍历

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if root is None:
            return True
        
        return self.isSym(root.left, root.right)

    def isSym(self, l, r):
        if l is None and r is not None:
            return False
        elif l is not None and r is None:
            return False
        elif l is None and r is None:
            return True
        
        if l.val != r.val:
            return False
        # else:
        #     return True
        
        return self.isSym(l.left, r.right) and self.isSym(l.right, r.left)        
```
