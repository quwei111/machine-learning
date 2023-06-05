# Heap／Priority Queue

## 基础
  - 完全二叉树
  - python中只有小顶堆（min heap），最小的元素总是在根结点：heap[0]，父节点元素始终小于或等于所有子节点元素
  - 大顶堆可以通过所有元素变为其负数
  - heap中的item可以是多元素，例如包括其频次

## 代码
```python
# 创建一个堆，可以使用list来初始化为 [] ，或者通过函数 heapify() ，把一个list转换成堆

import heapq

raw = [3, 1, 5]
heapq.heapify(raw)

print(heapq.heappop(raw))
print(heapq.heappushpop(raw, -1))  # 先push 再pop
```
