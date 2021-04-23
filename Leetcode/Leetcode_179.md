# Largest Number

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/largest-number/)

## Solution

- Bubble Sort
- Time Complexity: O(n^2)

```python
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        nums = list(map(str,nums))
        # Bubble sort
        for _ in range(len(nums)):
            for i in range(len(nums)-1):
                if int(nums[i]+nums[i+1]) < int(nums[i+1]+nums[i]):
                    nums[i], nums[i+1] = nums[i+1], nums[i]

        return str(int("".join(nums)))
```

- Insertion sort
- Time Complexity: O(n^2) (worst), O(n) (best)

```python
class Solution:
    def largestNumber(self, nums: List[int]) -> str:
        nums = list(map(str,nums))
        # Insertion sort
        i = 1
        while i < len(nums):
            j = i
            while j > 0 and int(nums[j-1]+nums[j]) < int(nums[j]+nums[j-1]):
                # swap
                nums[j], nums[j-1] = nums[j-1], nums[j]
                j -= 1
            i += 1

        return str(int("".join(nums)))
```
