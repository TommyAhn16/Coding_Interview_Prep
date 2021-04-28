# Two Sum II - Input array is sorted

> - Difficulty: Easy
> - Type: Two Pointer/ Binary Search
> - [link](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Solution

- Two Pointer solution
- Time complexity: O(n)
- Space complexity: O(1)

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers)-1

        # Adjust pointer position relative to the number sum
        while left != right:
            if numbers[right] + numbers[left] > target:
                right -= 1
            elif numbers[right] + numbers[left] < target:
                left += 1
            else:
                # sum equals target
                return [left+1,right+1]
```

- Binary Search solution
- Time Complexity: O(n log n)

```python
import bisect
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        for i,num in enumerate(numbers):
            expected = target - num
            ind = bisect.bisect_left(numbers,expected,i+1)
            if ind < len(numbers) and numbers[ind] == expected:
                return [i+1,ind+1]
```
