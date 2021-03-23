# 위장

> Level 2

> [link](https://programmers.co.kr/learn/courses/30/lessons/42578)

## My solution

- 의상종류가 3개면 각각의 부위에서 안입는것,첫번째,두번째,세번째 총 4개의 선택이 가능하고 부위별로 가능한 선택 수를 곱하면 모든 조합나 최소 하나는 입어야 해서 1을 뺀다

```python
def solution(clothes):
    # Make hash map of {type:cloths}
    hash = {}
    for i in clothes:
        if i[1] not in hash:
            hash[i[1]] = [i[0]]
        else:
            hash[i[1]].append(i[0])
    ans = 1
    for key in hash:
        ans *= len(hash[key]) + 1
    return ans -1
```
