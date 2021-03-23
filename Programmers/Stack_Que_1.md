# 다리를 지나는 트럭

> Level 2
> [link](https://programmers.co.kr/learn/courses/30/lessons/42583)

## My solution

Approach:

- iterate process with a while loop until all the truck is in the passed list
- keep length count of truck passing
- pop waiting truck when passing weight is less than the limit
- pop passing truck when length count reaches expected

```python
def solution(bridge_length, weight, truck_weights):
    truck_weights.reverse()
    passed = []
    passing = []
    tw = [[x,0] for x in truck_weights]
    time = 0
    goal = len(truck_weights)

    while len(passed) != goal:
        # Increment length count
        for t in passing:
            t[1] += 1

        # Check length and append to passed
        for i,t in enumerate(passing):
            if t[1] == bridge_length:
                passed.append(t)
                del passing[i]

        # Append new truck to passing
        bw = sum([x[0] for x in passing])
        # Consider weight coming in too
        if  tw and bw + tw[-1][0] <= weight:
            passing.append(tw.pop())

        time += 1
    return time
```
