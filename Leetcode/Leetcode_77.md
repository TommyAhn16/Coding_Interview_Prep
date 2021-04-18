# Combinations

> - Difficulty: Medium
> - Type: DFS/BFS question
> - [link](https://leetcode.com/problems/combinations/)

## Solution

- Using itertools combinations

```python
import itertools
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        return itertools.combinations(range(1,n+1),k)
```

- Using DFS recursively

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        result = []
        def dfs(combination,start,k):
            if k == 0:
                result.append(combination[:])
                return
            # Recursively call dfs on unseen words
            for i in range(start,n+1):
                combination.append(i)
                dfs(combination,i+1,k-1)
                combination.pop()
        dfs([],1,k)
        return result

```
