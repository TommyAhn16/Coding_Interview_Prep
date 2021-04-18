# Max Area of Island

> - Difficulty: Medium
> - Type: DFS/BFS
> - [link](https://leetcode.com/problems/max-area-of-island/)

## Solution

- Search island using DFS algo
- Keep track of island size
- Return the largest island size

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        def dfs(i,j,size):
          # Stop searching when index out of range or cell equals 0
          if i < 0 or j<0 or i >= len(grid) or j >= len(grid[0])or grid[i][j] != 1:
            return size
          # Change cell to 0 so we don't visit again
          grid[i][j] = 0
          # Increment size count
          size += 1
          size = dfs(i,j+1,size)
          size = dfs(i,j-1,size)
          size = dfs(i+1,j,size)
          size = dfs(i-1,j,size)
          # Return the incremented size count
          return size
        # Find the maximum size count
        max_size = 0
        for i in range(len(grid)):
          for j in range(len(grid[0])):
            if grid[i][j] == 1:
              max_size = max(max_size,dfs(i,j,0))
        return max_size
```
