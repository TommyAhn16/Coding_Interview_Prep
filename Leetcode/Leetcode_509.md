# Fibonacci Number

> - Difficulty: Easy
> - Type: Dynamic Programming
> - [link](https://leetcode.com/problems/fibonacci-number/)

## Solution

- Brute force recursion solution

```python
class Solution:
    def fib(self, n: int) -> int:
        if n <= 1:
            return n
        else:
            return self.fib(n-1) + self.fib(n-2)
```

- Memoization (Top-Down) solution

```python
import collections
class Solution:
    dp = collections.defaultdict(int)
    def fib(self, n: int) -> int:
        if n <= 1:
            return n

        if self.dp[n]:
            return self.dp[n]
        self.dp[n] = self.fib(n-1) + self.fib(n-2)

        return self.dp[n]
```

- Tabulation (Bottom-Up) solution

```python
import collections
class Solution:
    dp = collections.defaultdict(int)
    def fib(self, n: int) -> int:
        self.dp[1] = 1

        for i in range(2,n+1):
            self.dp[i] = self.dp[i-1] + self.dp[i-2]

        return self.dp[n]
```
