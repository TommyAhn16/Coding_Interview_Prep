# H-Index

> Level 2
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42747#)

## My solution

- O(n^2) time complexity

```python
import collections
def solution(citations):
    max_c = max(citations)
    cd = collections.Counter(citations)

    for i in range(max_c+1)[::-1]:
        count = 0
        for c in cd.items():
            if c[0] >= i:
                count += c[1]
        if count >= i:
            return i
    return 0
```

## Better Solution

- O(n) time complexity
- sort the list first in descending order
- enumerate(list) would result in iterations of (number of citations >= itself, itself)

```python
import collections
def solution(citations):
    citations.sort(reverse=True)
    h = 0
    for i in enumerate(citations, start=1):
        h = max(h,min(i))

    return h
```
