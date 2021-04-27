# Search in Rotated Sorted Array

> - Difficulty: Medium
> - Type: Binary Search
> - [link](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## Solution

- Find pivot (index of the minimum value)
- Perform binary search with pivot added to the mid point
- Time Complexity: O(log n)

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if not nums:
            return -1

        # Find min
        left, right = 0, len(nums) - 1
        while left < right:
            mid = left + (right - left) // 2

            if nums[mid] > nums[right]:
                left = mid + 1
            else:
                right = mid

        pivot = left

        # Binary search relative to pivot
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = left + (right - left) // 2
            mid_pivot = (mid + pivot) % len(nums)

            if nums[mid_pivot] < target:
                left = mid + 1
            elif nums[mid_pivot] > target:
                right = mid - 1
            else:
                return mid_pivot
        return -1

```
