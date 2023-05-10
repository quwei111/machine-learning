# 27. Remove Element

[https://leetcode.com/problems/remove-element/](https://leetcode.com/problems/remove-element/)

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

## solution

- 暴力法
  - 主要是array本身无法被in-place的修改，因此需要多加一个循环
  - 暴力法不是很好写


- 双指针：记录位置

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[slow], nums[i] = nums[i], nums[slow]
                slow += 1
        return slow
```
复杂度：

## summary
- 类似的双指针题目，slow记录一个位置
