# Queue Reconstruction by Height

> Medium
>
> [link](https://leetcode.com/problems/queue-reconstruction-by-height/)

# Solution

- Sort people:
  - In the descending order by height
  - Among the guys of the same height, in the ascending order by k-values
- Take guys one by one, and place them in the output array at the indexes equal to their k-values.

```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        # Sort in descending order for height, ascending order for k
        people.sort(key=lambda x:(x[0],-x[1]),reverse=True)
        ans = []
        for p in people:
            # Insert to the location of k
            ans.insert(p[1],p)
        return ans
```
