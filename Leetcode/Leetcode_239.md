# Sliding Window Maximum

> - Difficulty: Hard
> - Type: Slidng Window
> - [link](https://leetcode.com/problems/sliding-window-maximum/)

## Solution

- Solution using max heap(priority que)
- Save (number, index) in heap
- Check heap head if index is within the sliding window range
- Append max heap head to the output list
- Time Complexity: O(n log n)

```python
import heapq
class Solution:
    def maxSlidingWindow(self, nums: 'List[int]', k: 'int') -> 'List[int]':
        if len(nums) <= k:
            return [max(nums)]

        hp = [(-n,i) for i,n in enumerate(nums[:k])]
        heapq.heapify(hp)
        ans = [-hp[0][0]]

        for i,num in enumerate(nums[k:],start=k):
            # Check if heap head is within window frame range
            while hp and i - hp[0][1] >= k:
                heapq.heappop(hp)
            heapq.heappush(hp,(-num,i))
            ans.append(-hp[0][0])

        return ans
```
