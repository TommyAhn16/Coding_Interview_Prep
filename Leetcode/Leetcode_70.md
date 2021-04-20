# Climbing Stairs

> - Difficulty: Easy
> - Type: Dynamic Programming
> - [link](https://leetcode.com/problems/climbing-stairs/)

## Solution

- Problem is essentially same as the Fibonacci Number problem
- Memoization (Top-Down) solution

```python
import collections
class Solution:
    dp = collections.defaultdict(int)
    def climbStairs(self, n: int) -> int:
        if n <= 2:
            return n
        elif self.dp[n]:
            return self.dp[n]
        self.dp[n] = self.climbStairs(n-1) + self.climbStairs(n-2)
        return self.dp[n]
```

- Tabulation (Bottom-Up) solution

```python
import collections
class Solution:
    dp = collections.defaultdict(int)
    def climbStairs(self, n: int) -> int:
        self.dp[1],self.dp[2] = 1,2

        for i in range(3,n+1):
            self.dp[i] = self.dp[i-1] + self.dp[i-2]

        return self.dp[n]
```
