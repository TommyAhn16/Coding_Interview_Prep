# Best Time to Buy and Sell Stock 2

> Easy
>
> [link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

# Solution

- Maximize profit by only considering local cases

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        for i in range(len(prices)-1):
            # Check to see profit
            if prices[i+1] > prices[i]:
                profit += prices[i+1] - prices[i]
        return profit
```
