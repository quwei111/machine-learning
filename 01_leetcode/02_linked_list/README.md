# 链表

```python
class ListNode():
    self.val = val
    self.next = next    
```

## 基础
- 单链表
- 双链表
- 循环链表

与列表的区别
- 列表的增和删复杂度O(n),查找O(1)
- 链表的增和删O(1)，查找O(n)

## 技巧

- 头部加dummy node 0，便于返回整个链表头节点
```python
dummy = ListNode(-1)
dummy.next = head
```
