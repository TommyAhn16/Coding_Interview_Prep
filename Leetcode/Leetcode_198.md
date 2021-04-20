# House Robber

> - Difficulty: Medium
> - Type: Dynamic Programming
> - [link](https://leetcode.com/problems/house-robber/)

## Solution

- Memoization (Top-Down) solution
- Keep making the sum the largest number possible
- Adding sum must have index difference greater than or equal to 2

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        sums = []
        for i in range(0,len(nums)):
            if i >2:
                to_sum = max(sums[:i-1])
            elif i == 2:
                to_sum = sums[0]
            else:
                to_sum = 0
            sums.append(nums[i] + to_sum)
        return max(sums)
```

- Tabulation (Bottom-Up) solution

```python
import collections
class Solution:
    def rob(self, nums: List[int]) -> int:
        if not nums:
            return 0
        if len(nums) <= 2:
            return max(nums)

        dp = collections.OrderedDict()
        dp[0], dp[1] = nums[0], max(nums[0],nums[1])

        for i in range(2, len(nums)):
            dp[i] = max(dp[i-1], dp[i-2] + nums[i])

        return dp.popitem()[1]
```
