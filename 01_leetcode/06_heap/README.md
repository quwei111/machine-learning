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



Heap／Priority Queue题目：
Leetcode 973. K Closest Points
Leetcode 347. Top k Largest Elements
Leetcode 23. Merge K Sorted Lists
Leetcode 264. Ugly Number II
Leetcode 1086. High Five
Leetcode 88. Merge Sorted Arrays
Leetcode 692. Top K Frequent Words
Leetcode 378. Kth Smallest Element in a Sorted Matrix
Leetcode 295. Find Median from Data Stream （标准解法是双heap，但是SortedDict会非常容易）
Leetcode 767. Reorganize String
Leetcode 1438. Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit (这个题用单调双端队列、TreeMap、双heap都可以)
Leetcode 895. Maximum Frequency Stack
