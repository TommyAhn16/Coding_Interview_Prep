# 완주하지 못한 선수

> Level 1

> [link](https://programmers.co.kr/learn/courses/30/lessons/42576)

## My solution

```python
def solution(participant, completion):
    p = set(participant)
    c = set(completion)
    if len(p) != len(c):
        dif = list((p - c))[0]
        return dif
    else:
        p_sorted = sorted(participant)
        c_sorted = sorted(completion)
        for i in range(len(participant)):
            if p_sorted[i] != c_sorted[i]:
                return p_sorted[i]
```
