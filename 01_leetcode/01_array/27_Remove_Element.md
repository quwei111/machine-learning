# 27. Remove Element

[https://leetcode.com/problems/remove-element/](https://leetcode.com/problems/remove-element/)

## solution

- 暴力法
  - 主要是array本身无法被in-place的修改，因此需要多加一个循环
  - 但暴力法不是很好写

```python

```

- 双指针：记录位置

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0
        for i in range(len(nums)):
            if nums[i] != val:
                nums[slow] = nums[i]
                slow += 1
        return slow
```

## summary
