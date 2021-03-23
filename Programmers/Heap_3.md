# 이중우선순위큐

> Level 3
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42628)

# My solution

- solution using array and sorting
- time complexity: number of operations \* O(log n) = O (M log(n))

```python
def solution(operations):
    h = []
    for op in operations:
        op = op.split()
        if op[0] == "I":
            h.append(int(op[1]))
        elif h and op[0] == "D" and op[1] == "-1":
            del h[0]
        elif h and op[0] == "D" and op[1] == "1":
            del h[-1]
        # O(log n)
        h.sort()
    if h:
        return [h[-1],h[0]]
    else:
        return [0,0]
```

- Solution using heap
- O(M log(n)) Time complexity

```python
import heapq
def solution(operations):
    h = []
    for op in operations:
        op = op.split()
        if op[0] == "I":
            heapq.heappush(h,int(op[1]))
        elif h and op[0] == "D" and op[1] == "-1":
            heapq.heappop(h)
        elif h and op[0] == "D" and op[1] == "1":
            del h[-1]
    if h:
        return [max(h),h[0]]
    else:
        return [0,0]
```
