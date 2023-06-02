# 17 Letter Combinations of a Phone Number
[https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

## solution

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        
        mydict = {
            "2": ["a", "b", "c"],
            "3": ["d", "e", "f"],
            "4": ['g', 'h', 'i'],
            "5": ['j', 'k', 'l'],
            "6": ['m', 'n', 'o'],
            "7": ['p', 'q', 'r', 's'],
            "8": "t u v".split(),
            "9": "w x y z".split()
        }
        res = []
        path = []
        self.dfs(res, path, mydict, digits, index=0)
        return res

    def dfs(self, res, path, mydict, digits, index):
        if len(path) == len(digits):
            res.append("".join(path))
            return
        
        letters = digits[index]     
    
        for i in mydict[letters]:
            path.append(i)
            self.dfs(res, path, mydict, digits, index+1)
            path.pop()
```
