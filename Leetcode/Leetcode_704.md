# Binary Search

> - Difficulty: Easy
> - Type: Binary Search
> - [link](https://leetcode.com/problems/binary-search/)

## Solution

- Binary search by iteration
- Time Complexity: O (log n)
- ((end-start) // 2) + start = (end+start)//2

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        start = 0
        end = len(nums)

        # Binary Search
        while start < end:
            mid = ((end-start) // 2) + start
            # Mid point is target
            if nums[mid] == target:
                return mid
            # Mid point bigger than target
            elif nums[mid] > target:
                end = mid
            # Mid point smaller than target
            elif nums[mid] < target:
                start = mid+1

        return -1
```

- Solution using built-in Python module for binary search

```python
import bisect
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # Returns the index where 'target' should be inserted
        # If target already exists, returns the index of where it is
        index = bisect.bisect_left(nums, target)

        if index < len(nums) and nums[index] == target:
            return index
        else:
            return -1

```
