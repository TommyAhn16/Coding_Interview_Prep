# Search a 2D Matrix II

> - Difficulty: Medium
> - Type: Binary Search
> - [link](https://leetcode.com/problems/search-a-2d-matrix-ii/)

## Solution

- Run binary search on row only if the last element is greater than the target
- Time Complexity: O(n log n) (worst case)

```python
import bisect
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        if not matrix:
            return False

        i = 0
        for row in matrix:
            if row[-1] < target:
                continue
            # Run Binary search
            elif row[-1] > target:
                i = bisect.bisect_left(row,target)
                if i < len(row) and row[i] == target:
                    return True
            else:
                return True
        return False
```

- Simplest solution
- Time Complexity: O(n log n)

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        return any(target in row for row in matrix)
```
