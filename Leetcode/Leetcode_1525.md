# Number of Good Ways to Split a String

> - Difficulty: Medium
> - Type: Stack/Que, String
> - [link](https://leetcode.com/problems/number-of-good-ways-to-split-a-string/)

## Solution

- Time Complexity: O(n)

```python
import collections
class Solution:
    def numSplits(self, s: str) -> int:
        count = 0
        left = set()
        right = set(s)
        deq = collections.deque(s)
        for _ in range(len(s)-1):
            popped = deq.popleft()
            left.add(popped)
            if popped not in deq:
                right.remove(popped)
            if len(left) == len(right):
                count += 1
        return count
```
