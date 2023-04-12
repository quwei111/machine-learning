
# Python 基础

## 基础知识
- 垃圾回收机制gc
- 全局锁GIL


## Python常用操作

- 从列表list中找出某值a第一个匹配项的索引位置
```python
list.index(a) 
```
- python中使用列表实现队列
```python
list.pop(0)
```

- 往某个位置插入某个元素
```python
list.insert(0, num), 
```

- 列表排序
```python
l = sorted(l)
l.sorted()
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
```

- 个位是否为1
```python
x%10==1 
```

- heapq 堆的操作
```python

```

- 链表循环内容涉及两个节点判断时
```python
while head is not None and head.next is not None
```

- 字符串前的空格 
```python
s.strip()
```

- 字符串 
```python
ord(s[0])/ s[0].isdigit()
```

- 两层循环中的break，break的是相应层的循环
```python

```

- 多个条件判断时，是否越界和是否符合条件可以写在一起。也就是有先后顺序的

```
正确
while s[l] == s[r] and l >= 0 and r < len(s)

错误
while l >= 0 and r < len(s) and s[l] == s[r]
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

- 树的后续遍历
```python
# merge sort

def merge(lista,listb):
    output=[]
    i,j=0,0
    while i<len(lista) and j<len(listb):
        if lista[i]>listb[j]:
            output.append(listb[j])
            j+=1
        else:
            output.append(lista[i])
            i+=1
    if i<len(lista):
        output+=lista[i:]
    if j<len(listb):
        output+=listb[j:]
    return output


def merge_sort(list):
    if len(list) <= 1:
        return list
    mid=len(list)//2
    return merge(merge_sort(list[:mid]),merge_sort(list[mid:]))

#print(merge([1,4,5],[2,3,6,8]))
print(merge_sort([5,1,2,4,6,3]))
```

### 快速排序

- 树的前序遍历
```python
#quick sort
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

#print(quick_sort([5,1,2,4,6,3]))

def partition(ls, p, r):
    key = ls[r]
    i = p - 1
    for j in range(p, r-1):
        if ls[j] <= key:
            i = i + 1
            ls[i], ls[j] = ls[j], ls[i]
    ls[i+1], ls[r] = ls[r], ls[i+1]
    return i + 1

def quick_sort_op(list, p, r):
    if p < r:
        q = partition(list, p, r)
        quick_sort_op(list, p, q - 1)
        quick_sort_op(list, q + 1,r)


list=[5,2,1,4,6,3]
quick_sort_op(list,0,len(list)-1)
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

list=[2, 7, 1, -2, 56, 5, 3]
heap_sort(list)
print(list)
```

### 拓扑排序


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


## 参考
- https://github.com/wangzheng0822/algo/tree/master/python
