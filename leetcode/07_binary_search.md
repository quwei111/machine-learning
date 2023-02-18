# 二分查找
- lower bound/ upper bound

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