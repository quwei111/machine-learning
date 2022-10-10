# 树

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