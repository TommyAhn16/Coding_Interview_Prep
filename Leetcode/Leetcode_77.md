# Combinations

> Medium
>
> [link](https://leetcode.com/problems/combinations/)

# Solution

- Using itertools combinations

```python
import itertools
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        return itertools.combinations(range(1,n+1),k)
```

- Using DFS

```python

```
