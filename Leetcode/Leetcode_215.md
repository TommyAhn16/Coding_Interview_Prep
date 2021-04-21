# Kth Largest Element in an Array

> - Difficulty: Medium
> - Type: Heap/Priority Que
> - [link](https://leetcode.com/problems/kth-largest-element-in-an-array/)

## Solution

- Solution using sorting
- Time complexity: O(n log(n))
- Space complexity: O(1)

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        return sorted(nums)[-k]
```

- Solution using heapify
- Time complexity: O(n log (n-k))
- Space complexity: O(1)

```python
import heapq
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        heapq.heapify(nums)
        for _ in range(len(nums) - k):
            heapq.heappop(nums)
        return heapq.heappop(nums)
```

- Solution using heapq.nlargest()
- Time complexity: O(n log k)
- Space complexity: O(k)

```python
import heapq
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        return heapq.nlargest(k,nums)[-1]
```
