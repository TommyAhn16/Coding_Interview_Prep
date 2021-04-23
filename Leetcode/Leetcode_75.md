# Sort Colors

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/sort-colors/)

## Solution

- Dutch National Flag Problem (Three Pointers)
- Time complexity: O(n)

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        # mid value equals 1 in this problem
        start = 0
        cur = 0
        end = len(nums)

        while cur < end:
            # Swap with the start pointer when value in current pointer is smaller than mid
            if nums[cur] < 1:
                nums[start], nums[cur] = nums[cur], nums[start]
                start += 1
                cur += 1
            # Swap with the end pointer when value in current pointer is bigger than mid
            elif nums[cur] > 1: # mid
                end -= 1
                nums[cur], nums[end] = nums[end], nums[cur]
            # Do not swap but increase current pointer by 1 if value in cur pointer = mid
            else:
                cur += 1

```
