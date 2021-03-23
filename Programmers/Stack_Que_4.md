# 프린터

> Level 2
> [link](https://programmers.co.kr/learn/courses/30/lessons/42587)

## My Solution

- Use `deque` to popleft
- pop the object and decide whether to reattach it to deque or compare its index wiht the target location.

```python
import collections
def solution(priorities, location):
    priorities = [(p,i) for i,p in enumerate(priorities)]
    p = collections.deque(priorities)
    order = 0

    while p:
        J = p.popleft()
        # Any will return true if at least one of the number is bigger
        if any(J[0] < q[0] for q in p):
            p.append(J)
        else:
            order += 1
            if J[1] == location:
                return order
```
