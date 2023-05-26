# 二分查找


- 排序是前提
- 对于一个长度为 O(n) 的数组，二分查找的时间复杂度为 O(log n)
- 注意 "区间不变量"，每一次边界处理都根据区间的定义来操作
  - 左闭右闭 [left, right]
    - while循环
    - 左右区间迭代
  - 左闭右开 [left, right)
    - while循环 
    - 左右区间迭代
- 对Java或C，start+end可能会overflow，需要用start + (end - start) // 2
- 避免死循环用 (start + 1) < end，注意左右迭代时是否加1


```
def binary_search(key, nums):
    left = 0
    right = len(nums)-1

    while left <= right:
        mid = (left + right) // 2

        if key < nums[mid]:
            right = mid - 1
        elif key > nums[mid]:
            left = mid + 1
        else:
            return mid
    return False


if __name__ == '__main__':
    print(binary_search(5, [1, 2, 4, 5, 9]))
```



## Reference
- https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/discuss/14714/16-line-Python-solution-symmetric-and-clean-binary-search-52ms
