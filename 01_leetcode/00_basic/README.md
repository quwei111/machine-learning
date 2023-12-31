# Python 基础

## 基础知识
- 垃圾回收机制gc
- 全局锁GIL

## Python常用操作

- 从列表list中找出目标值a **第一个匹配项的索引** 位置
```python
list.index(a) 
```

- python中使用列表实现队列
```python
list.pop(0)
# list.remove()
# list.append()
```

- 往某个位置插入某个元素
```python
list.insert(0, num)
```

- 列表排序
```python
l = sorted(l)
l = sorted(l, key = lambda x: x[0])
l = sorted(l, reverse=True)

l.sort()  # 注意这是in-place
```

- 列表索引
```python
# 左闭右开
# 从右边取，注意为0会取全体值是否是想要的
list[-1:]  # 取最后一个
list[-0:]  # 取全体list
list[::2]  # 每间隔2个取
```

- deque
```python
# BFS常用
from collections import deque

depuq.popleft()
```

- 定义二维列表
```python
matrix = [[0 for _ in range(col)] for _ in range(row)]
matrix1 = [[0] * col for _ in range(row) ]

# 错误，都是引用导致值相同
[[0] * col] * row
```

- 二维列表转置
```python

```

- 字典按value排序
```python
dict(sorted(x.items(), key=lambda item: item[1]))


```

- 字典获得key值
```python
dict.get(key, default) 
```

- 删除键值
```python
del dict[key]

my_dict.pop('key', None)
```

- 个位是否为1
```python
x % 10 == 1 
```

- heapq 堆的操作
```python
import heapq
```

- 链表循环内容涉及两个节点判断时
```python
# 根据head / head.next / head & head.next 来决定迭代终点
while head is not None and head.next is not None:
    pass
```

- 字符串前的空格 
```python
s.strip()
```

- 字符串 

```python
# ord
ord(s[0])/ s[0].isdigit()

# 小写
s.lower()
```

- 两层循环中的break，break的是相应层的循环
```python

```

- 多个条件判断时，条件是有先后顺序的。是否越界和是否符合条件可以写在一起

```
正确
while s[l] == s[r] and l >= 0 and r < len(s)

错误
while l >= 0 and r < len(s) and s[l] == s[r]
```

- for循环：提前已知遍历的所有元素；while循环：根据循环过程来决定所有遍历元素

- 最小与最大

```python
float('inf')
float('-inf') 
```

- flag来交替
```python
# 280. Wiggle Sort

```

## 排序


###  冒泡排序

- 记忆点：两层for循环，相邻比较
```python
def bubble_sort(list):
    for i in range(len(list)):
        for j in range(len(list)-i-1):
            if list[j] > list[j+1]:
                list[j], list[j+1] = list[j+1], list[j]
    return list


def test_bubble():
    sorted_l = bubble_sort([5,1,2,4,6,3])
    assert sorted_l == [1, 2, 3, 4, 5, 6]
```

### 插入排序

算法导论第一个介绍的算法
- 记忆点：算法导论中的扑克
```python
def insert_sort(list):
    for i in range(1, len(list)):
        j = i
        while j > 0 and list[j-1] > list[j]:
            list[j], list[j-1] = list[j-1], list[j]
            j -= 1
    return list
```

- 递归写法
```python
def insert_sort_rec(list,m):
    if m==0:
        return
    mmax=m
    for i in range(m):
        if list[i]>list[mmax]:
            mmax = i
    list[m],list[mmax]=list[mmax],list[m]
    insert_sort_rec(list,m-1)
```

### 选择排序
```python
def selection_sort(list):
    for i in range(len(list)):
        mini=min(list[i:])
        mini_index=list[i:].index(mini)
        list[i+mini_index]=list[i]
        list[i]=mini
    return list

print(selection_sort([4,2,1,10,5,3,100]))
```


### 归并排序

- 树的后序遍历
- divide & conquer: top down & bottom up

```python
# merge sort

def merge(lista, listb):
    output=[]
    i, j = 0, 0
    while i < len(lista) and j < len(listb):
        if lista[i] > listb[j]:
            output.append(listb[j])
            j += 1
        else:
            output.append(lista[i])
            i += 1
    if i < len(lista):
        output += lista[i:]
    if j < len(listb):
        output += listb[j:]
    return output


def merge_sort(list):
    if len(list) <= 1:
        return list
    mid = len(list)//2
    return merge(merge_sort(list[:mid]), merge_sort(list[mid:]))

#print(merge([1,4,5],[2,3,6,8]))
print(merge_sort([5,1,2,4,6,3]))
```

### 快速排序

- 树的前序遍历
- average O(NLOGN) 最好O(1) 最差O(N^2)
- 注意左闭右开

```python
# quick sort
import numpy as np

def quick_sort(list):
    if len(list) <= 1:
        return list
    left, right = [], []
    key = np.random.choice(list)
    for i in range(len(list)):
        if list[i] <= key:
            left.append(list[i])
        else:
            right.append(list[i])
    return quick_sort(left) + quick_sort(right)


def partition(list, p, r):
    # 选择list中[p, r]区间返回位置i，左边都小于，右边都大于
    key = list[r]
    i = p - 1
    for j in range(p, r - 1):
        if list[j] <= key:
            i = i + 1
            list[i], list[j] = list[j], list[i]
    list[i+1], list[r] = list[r], list[i+1]
    return i + 1


def quick_sort_op(list, p, r):
    if p < r:
        q = partition(list, p, r)
        quick_sort_op(list, p, q - 1)
        quick_sort_op(list, q + 1,r)


list=[5, 2, 1, 4, 6, 3]
quick_sort_op(list, 0, len(list)-1)
print(list)
```

### 堆排序

```python
# https://stackoverflow.com/questions/13979714/heap-sort-how-to-sort

def max_heapify(list, end, i):
    l = 2 * i + 1
    r = 2 * (i + 1)
    max = i
    if l < end and list[i] < list[l]:
        max = l
    if r < end and list[max] < list[r]:
        max = r
    if max != i:
        list[i], list[max] = list[max], list[i]
        max_heapify(list, end, max)


def heap_sort(list):
    end = len(list)
    start = end // 2 + 1
    for i in range(start, -1, -1):
        max_heapify(list, end, i)
    for i in range(end-1, 0, -1):
        list[i], list[0] = list[0], list[i]
        max_heapify(list, i, 0)

list = [2, 7, 1, -2, 56, 5, 3]
heap_sort(list)
print(list)
```

### 拓扑排序
- 拓扑排序也可以被看成是[广度优先搜索](../08_bfs/README.md)的一种情况
- 一般用于解决有方向的图，non-directed graph不能用， 需要用union find或者普通的DFS/BFS

```python
# https://zh.wikipedia.org/wiki/%E6%8B%93%E6%92%B2%E6%8E%92%E5%BA%8F

```


### 计数排序
```python
from collections import defaultdict

def counting_sort(A, key=lambda x: x):
    B, C = [], defaultdict(list) # Output and "counts"
    for x in A:
        C[key(x)].append(x) # "Count" key(x)
    print('C:',C)

    for k in range(min(C), max(C)+1): # For every key in the range
        B.extend(C[k]) # Add values in sorted order
        print(C[k],'/n')
    print(B)
    return B

counting_sort([2,5,3,0,2,3,3,4])
```
