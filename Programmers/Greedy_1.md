# 체육복

> Level 1
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42862#)

# Solution

- DS: array (set)
- Algo: Greedy

```python
def solution(n, lost, reserve):
    # Remove intersections of both input
    reserve, lost = set(reserve) - set(lost), set(lost) - set(reserve)
    total = n - len(lost)
    # Increment total count for every reserve item which could be used
    for i in lost:
        if i - 1 in reserve:
            reserve.remove(i-1)
            total += 1
        elif i + 1 in reserve:
            reserve.remove(i+1)
            total += 1
    return total
```
