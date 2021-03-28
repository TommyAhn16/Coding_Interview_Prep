# 체육복

> Level 1
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42862#)

# Solution

```python
def solution(n, lost, reserve):
    total = n - len(lost)
    reserve = set(reserve)
    to_remove = []
    for i in lost:
        if i in reserve:
            total += 1
            reserve.remove(i)
            to_remove.append(i)
    for i in to_remove:
        lost.remove(i)
    for i in lost:
        if i - 1 in reserve:
            reserve.remove(i-1)
            total += 1
        elif i + 1 in reserve:
            reserve.remove(i+1)
            total += 1
    return total
```
