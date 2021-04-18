# Permutations

> - Difficulty: Medium
> - Type: DFS/BFS
> - [link](https://leetcode.com/problems/permutations/)

## Solution

- Using python built in permutation function

```python
import itertools
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        return list(map(list,itertools.permutations(nums,len(nums))))
```

- Using DFS recursively

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        results = []
        prev_elements = []
        def dfs(elements):
            # Return when reaching leaf node
            if len(elements) == 0:
                results.append(prev_elements[:])

            # Iterate through elements and call dfs
            for e in elements:
                next_elements = elements[:]
                next_elements.remove(e)
                prev_elements.append(e)
                dfs(next_elements)
                prev_elements.pop()
        dfs(nums)
        return results
```
