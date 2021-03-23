# 카펫

> Level 2
> [link](https://programmers.co.kr/learn/courses/30/lessons/42842)

## My Solution

- 규칙을 찾는다
- 모서리를 제외한 테두리변은 brown - 4
- yellow 의 겉 테두리변 길이가 brown -4 가 될 수 있는 가로 세로 길이의 조합을 찾는다 (가로가 항상 더 길다)

```python
def solution(brown, yellow):
    target = brown - 4
    # Find combination to satisfy target outer length
    mul = yellow // 2 if yellow % 2 == 0 else yellow // 2 + 1
    for i in range(1,mul+1):
        if yellow % i  == 0 and ((yellow//i+i)*2) == target:
            return [max(yellow//i,i)+2, min(yellow//i,i)+2]
```
