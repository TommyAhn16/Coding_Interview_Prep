# 주식가격

> Level 2
> [link](https://programmers.co.kr/learn/courses/30/lessons/42584)

## My Solution

Approach

- Use `deque` data structure (access start and end in constant time) for storing prices
- Pop price form start and compare with the remaining prices until finding a lower price.
- O(n^2) time complexity

```python
import collections
def solution(prices):

    ans = []
    prices = collections.deque(prices)
    while prices:
        cur_price = prices.popleft()
        count = 0

        for p in prices:
            if (p < cur_price):
                count += 1
                break
            else:
                count += 1
        ans.append(count)
    return ans
```
