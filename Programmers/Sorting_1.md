# Sorting Question 1

> [link](https://programmers.co.kr/learn/courses/30/lessons/42748)

## My solution

- Simply follow instructions

```python
def solution(array, commands):
    ans = [sorted(array[c[0]-1:c[1]])[c[2]-1] for c in commands]

    return ans
```
