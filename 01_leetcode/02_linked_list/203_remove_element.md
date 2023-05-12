# 203. Remove Linked List Elements
[https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

## solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        dummy = ListNode(-1)
        dummy.next = head
        pre = dummy
        cur = dummy.next

        while cur is not None:
            if cur.val == val:
                pre.next = cur.next
                cur = cur.next
            else:
                cur = cur.next
                pre = pre.next
        return dummy.next  

```
时间复杂度
空间复杂度
