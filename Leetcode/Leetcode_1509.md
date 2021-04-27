# Minimum Difference Between Largest and Smallest Value in Three Moves

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/minimum-difference-between-largest-and-smallest-value-in-three-moves/)

## Solution

- Time Complexity: O(n log n) (for sorting numbers)
- Changing the number is same as excluding it from the candidate for minimum or maximum value (change it to the mean)

```python
import sys
class Solution:
    def minDifference(self, nums: List[int]) -> int:
        # When length is less or equal to 4, all the number could be changed to the same number
        if len(nums) <= 4:
            return 0

        nums.sort() # O(n log n)
        front = []
        back = []

        # Find every min and max after changing x amount of numbers from front and back
        for i in range(4):
            front.append(nums[i])
            back.append(nums[-(4-i)])

        # Find the minimum difference
        min_dif = sys.maxsize
        for i in range(len(front)):
            min_dif = min(min_dif,back[i]-front[i])

        return min_dif
```
