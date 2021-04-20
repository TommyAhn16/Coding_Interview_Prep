# Maximum Subarray

> - Difficulty: Easy
> - Type: Dynamic Programming
> - [link](https://leetcode.com/problems/maximum-subarray/)

## Solution

- Memoization (Top-Down) solution

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        sums = [nums[0]]
        for i in range(1,len(nums)):
            # Only add previous sum if it is bigger than 0
            sums.append(nums[i]+(sums[i-1] if sums[i-1]>0 else 0))
        return max(sums)
```
