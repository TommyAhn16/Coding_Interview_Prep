# 디스크 컨트롤러

> Level 3: couldn't solve
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/42627)

# Solution

- [Reference](https://velog.io/@younge/Python-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC-%ED%9E%99)
- key point: only push elements that fit in the timeline (rquest time is bigger than the start point and smaller or equal to )

```python
import heapq
def solution(jobs):
    ans, now, i = 0, 0 ,0
    start = -1
    heap = []

    while i < len(jobs):
        for j in jobs:
            if start< j[0] <= now:
                # heap sorted by work duration=j[1] (min heap)
                heapq.heappush(heap,[j[1],j[0]])
        if heap:
            current = heapq.heappop(heap)
            start = now
            now += current[0]
            ans += (now - current[1])
            i += 1
        else:
            now += 1
    return ans//len(jobs)
```
