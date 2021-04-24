# Maximum Points You Can Obtain from Cards

> - Difficulty: Medium
> - Type: Dynamic Programming
> - [link](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

## Solution

- key observation: when selecting i cards from the front, k-i cards are selected from the back
- Make two lists (front,back) that saves the sum of selecting i cards from both front and back
- Run every combination and find the maximum sum
- Time Complexity: O(k)
- Tabulation (Bottom-Up) Solution

```python
class Solution:
    def maxScore(self, cardPoints: List[int], k: int) -> int:
        max_sum = 0
        front = [0]
        back = [0]
        for i in range(k):
            front.append(front[-1]+cardPoints[i])
            back.append(back[-1]+cardPoints[-(i+1)])
        for i in range(k+1):
            max_sum = max(max_sum,front[i]+back[k-i])
        return max_sum
```
