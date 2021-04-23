# K Closest Points to Origin

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/k-closest-points-to-origin/)

## Solution

- Sorting solution
- Time Complexity: O(n log n)

```python
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        points.sort(key= lambda x: x[0]**2 + x[1]**2)
        return points[:k]
```

- Priority Que solution
- Time complexity: O(n)

```python
import heapq
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        points = [((x**2+y**2),[x,y]) for x,y in points] # O(n)
        heapq.heapify(points) # O(log n)
        return list(map(lambda x: x[1],heapq.nsmallest(k,points))) # O(log n)
```
