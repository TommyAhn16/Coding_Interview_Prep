# Stack Que Question 3

> [link](https://programmers.co.kr/learn/courses/30/lessons/42586)

## My Solution

- Use `deque` as data structure

```python
import collections
def solution(progresses, speeds):
    done = []
    ans = []
    # Save the amount of days needed to finish task
    for p,s in zip(progresses, speeds):
        if (100 - p) % s != 0:
            done.append((100 - p) // s + 1)
        else:
            done.append((100 - p) // s)

    deq = collections.deque(done)
    # pop until the amount of days needed to finish the task is bigger than the previous day
    while deq:
        count = 1
        cur = deq.popleft()
        while deq and cur >= deq[0]:
            deq.popleft()
            count +=1
        ans.append(count)
    return ans
```
