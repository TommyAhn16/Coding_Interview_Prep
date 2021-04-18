# Letter Combinations of a Phone Number

> - Difficulty: Medium
> - Type: DFS/BFS
> - [link](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

## Solution

- Time complexity: O(4^N N), where N is the length of digits. Note that 4 in this expression is referring to the maximum value length in the hash map, and not to the length of the input.

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        # Lookup table for number to character
        dic = {"2":"abc" , "3":"def", "4":"ghi","5":"jkl","6":"mno","7":"pqrs","8":"tuv", "9":"wxyz"}

        # Implement DFS
        def dfs(index,path):
            if len(path) == len(digits):
                result.append(path)
                return
            for i in range(index,len(digits)):
                for j in dic[digits[i]]:
                    dfs(i+1,path+j)


        # Exception handling
        if not digits:
            return []
        # Run dfs
        result = []
        dfs(0,"")
        return result
```
