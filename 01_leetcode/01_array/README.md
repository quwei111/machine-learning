# 列表

- 二次遍历

对于需要考虑后面信息的任务，经常需要二次遍历。第一次遍历得到



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



# 双指针

双指针只针对都是正数，如果有负数，hash


## 滑动窗口

注意滑动窗口适用的条件，当只有一方


背向双指针：(基本上全是回文串的题)
Leetcode 409. Longest Palindrome
Leetcode 125. Valid Palindrome (I、II)
Leetcode 5. Longest Palindromic Substring
Leetcode 647. Palindromic Substrings
相向双指针：(以two sum为基础的一系列题)
Leetcode 1. Two Sum (这里使用的是先排序的双指针算法，不同于hashmap做法)
Leetcode 167. Two Sum II - Input array is sorted
Leetcode 15. 3Sum
Leetcode 16. 3Sum Closest
Leetcode 18. 4Sum
Leetcode 454. 4Sum II
Leetcode 277. Find the Celebrity
Leetcode 11. Container With Most Water
Leetcode 186 Reverse Words in a String II

Leetcode 283. Move Zeroes
Leetcode 26. Remove Duplicate Numbers in Array
Leetcode 395. Longest Substring with At Least K Repeating Characters
Leetcode 340. Longest Substring with At Most K Distinct Characters
Leetcode 424. Longest Repeating Character Replacement
Leetcode 76. Minimum Window Substring
Leetcode 3. Longest Substring Without Repeating Characters
Leetcode 1004 Max Consecutive Ones III
Leetcode 1658 Minimum Operations to Reduce X to Zero