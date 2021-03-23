# 더 맵게

> Level 2
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42626)

# My Solution

- used `heap` methods from `heapq`
- 정렬과 pop을 동시에 해야할 때 heap 이 가장 효율적이다.
- Heap: 정렬 = O(log N), 삽입 = O(log N)

```python
import heapq
def solution(scoville, K):
    h = scoville
    h.sort()
    # Impossible when k = 0
    if K == 0:
        return -1

    count = 0
    # Pop, push until all element is above K
    while h[0] < K:
        if len(h) >= 2:
            min_1 = heapq.heappop(h)
            min_2 = heapq.heappop(h)
            new_score = min_1 + min_2*2
            heapq.heappush(h,new_score)
            count += 1
        else:
            return -1
            break
    return count
```
