# Max Value of Equation

> - Difficulty: Hard
> - Type: Priority Que / Heap
> - [link](https://leetcode.com/problems/max-value-of-equation/)

## Solution

- Key observation: yi + yj + |xi - xj| = yi - xi + yj + xj, because xj is strictly greater than xi.
- Therefore, maximum value of equation would be to maximize yi - xi within the limits (xj - xi <= k )
- When going through the points, save yi - xi value in a max heap.
- Check if heap head is within the limit and if it is, find the maximum value of equation
- Time complexity: O(n log n)

```python
import heapq
import sys

class Solution:
    def findMaxValueOfEquation(self, points: List[List[int]], k: int) -> int:
        pq = []
        ans = -sys.maxsize
        for x,y in points:
            while pq and x - pq[0][1] > k:
                heapq.heappop(pq)

            if pq:
                ans = max(ans,-pq[0][0]+x+y)

            # save to max heap
            heapq.heappush(pq,(-(y-x),x))

        return ans
```
