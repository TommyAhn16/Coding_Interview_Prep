# Intersection of Two Arrays

> - Difficulty: Easy
> - Type: Binary Search
> - [link](https://leetcode.com/problems/intersection-of-two-arrays/)

## Solution

- Sort one list
- Iterate through the unsorted array and search for each element in the sorted array by binary search
- Time Complexity: O(n log n)
- Space Complexity: O(1) (not including the result list)

```python
import bisect
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        if not nums1 or not nums2:
            return []

        result = set()
        # Sorting: O(n log n)
        nums2.sort()
        # Binary search for n times: O(n log n)
        for n in nums1:
            i = bisect.bisect_left(nums2,n)
            if i < len(nums2) and nums2[i] == n:
                result.add(n)

        return list(result)
```

- Simple solution

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return list(set(nums1) & set(nums2))
```
