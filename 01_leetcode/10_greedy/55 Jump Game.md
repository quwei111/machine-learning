# 55 Jump Game
[https://leetcode.com/problems/jump-game/](https://leetcode.com/problems/jump-game/)

## solution

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        if not nums:
            return False
        if len(nums) == 1:
            return True

        i = 0
        res = 0        
       
        while i <= res:
            res = max(res, i + nums[i])
            if res >= len(nums) - 1:
                return True    
            i += 1     

        return False
```


## follow up

[45 Jump Game II](https://leetcode.com/problems/jump-game-ii/)

- 记录当前覆盖最远距离和下一次覆盖最远距离，当前距离最远时，增加一步到下一次最远距离
```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        if len(nums) == 1:
            return 0

        cur_pos = 0
        next_pos = 0
        i = 0
        res = 0
        for i in range(len(nums)):
            next_pos = max(i+nums[i], next_pos)
            if i == cur_pos:
                cur_pos = next_pos
                res += 1
                if next_pos >= len(nums) - 1:
                    break
        return res
```
