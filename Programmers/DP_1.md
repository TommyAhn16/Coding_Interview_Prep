# 멀리 뛰기

> - Difficulty: Level 3
> - Type: Dynamic Programming
> - [link](https://programmers.co.kr/learn/courses/30/lessons/12914)

## Solution

- Leetcode의 계단오르기 문제와 동일하다
- 피보나치 수열을 구하는 방식으로 풀면 답을 구할 수 있다
- Tabulation (Bottom-Up) Solution

```python
import collections
def solution(n):
    dp = collections.defaultdict(int)
    dp[1] = 1
    dp[2] = 2

    for i in range(3,n+1):
        dp[i] = dp[i-1] + dp[i-2]
    return dp[n] % 1234567
```
