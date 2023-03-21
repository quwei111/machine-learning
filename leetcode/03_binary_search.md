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

显式二分法：
Leetcode 34. Find First and Last Position of Element in Sorted Array
Leetcode 33. Search in Rotated Sorted Array
Leetcode 1095. Find in Mountain Array
Leetcode 162. Find Peak Element
Leetcode 278. First Bad Version
Leetcode 74. Search a 2D Matrix
Leetcode 240. Search a 2D Matrix II
隐式二分法：
Leetcode 69. Sqrt(x)
Leetcode 540. Single Element in a Sorted Array
Leetcode 644. Maximum Average Subarray II
Leetcode 528. Random Pick with Weight
Leetcode 1300. Sum of Mutated Array Closest to Target
Leetcode 1060. Missing Element in Sorted Array
Leetcode 1062. Longest Repeating Substring
Leetcode 1891. Cutting Ribbons
Leetcode 410. Split Array Largest Sum (与1891类似)

## Reference
- https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/discuss/14714/16-line-Python-solution-symmetric-and-clean-binary-search-52ms