# Combination Sum

> - Difficulty: Medium
> - Type: DFS/BFS
> - [link](https://leetcode.com/problems/combination-sum/)

## Solution

- Use DFS and recursion to find combinations that add up to the target

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        result = []
        # Recursievely decrease candidate sum until reaching target (or missing)
        def dfs(csum,start,path):
            if csum < 0:
                return
            elif csum == 0:
                result.append(path)
                return
            # If no duplicates were allowed, dfs would pass i+1 instead
            for i in range(start,len(candidates)):
                dfs(csum-candidates[i],i, path+[candidates[i]])

        dfs(target,0,[])
        return result
```
