# Merge Intervals

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/merge-intervals/)

## Solution

- DS: Stack for intermediate value storage, array
- Algo: Sorting
- Time complexity = O(nlog(n)), python built in sort function
- Only merge when previous end time is greater or equal to the current start time and also less than the current end time

```Python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        # Exception handling
        if len(intervals) <= 1:
            return intervals

        # Sort the intervals in descending order
        intervals.sort(key=lambda x: (x[0],x[1]))
        ans = []

        for start,end in intervals:
            # Condition for merging
            if ans and ans[-1][1] >= start and ans[-1][1] < end:
                prev = ans.pop()
                ans.append([prev[0], end])
            # When complete overlap
            elif ans and ans[-1][1] >= end:
                continue
            # When output list is empty
            else:
                ans.append([start,end])

        return ans
```
