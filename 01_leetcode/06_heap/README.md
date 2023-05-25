# Heap／Priority Queue

- 基础
  - python中只有小顶堆（min heap），大顶堆可以通过所有元素变为其负数
```python
import heapq

raw = [3, 1, 5]
heapq.heapify(raw)

print(heapq.heappop(raw))
print(heapq.heappushpop(raw, -1))  # 先push 再pop
```
