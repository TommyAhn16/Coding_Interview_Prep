# Merge Intervals

> Medium
>
> [link](https://leetcode.com/problems/merge-intervals/)

# Solution

- DS: Stack for intermediate value storage, array
- Algo: Sorting
- Time complexity = O(nlog(n)), python built in sort function

```Python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        # Sort the array in ascending orders
        intervals.sort(key=lambda x: (x[0],x[1]))
        ans = []
        start = [intervals[0][0]]
        end = [intervals[0][1]]
        # Go through intervlas and compare start and end values
        for s,e in intervals:
            if s > end[-1]:
                ans.append([start.pop(),end.pop()])
                start.append(s)
                end.append(e)
            elif e > end[-1]:
                end.pop()
                end.append(e)
        # Pop remaining elements in start, end
        if start and end:
            ans.append([start.pop(),end.pop()])


        return ans
```
