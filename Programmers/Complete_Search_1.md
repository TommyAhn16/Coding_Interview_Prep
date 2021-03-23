# 모의고사

> Level 1
> [link](https://programmers.co.kr/learn/courses/30/lessons/42840)

## My Solution

- Define pattern and search for matches
- Use list to represent patterns

```python
def solution(answers):
    # Define patterns
    pat_1 = [1, 2, 3, 4, 5]
    pat_2 = [2, 1, 2, 3, 2, 4, 2, 5]
    pat_3 = [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]
    cor_1,cor_2,cor_3 = 0,0,0
    # Increase correct ans count when pattern matches
    for i in range(len(answers)):
        p_1,p_2,p_3 = i%len(pat_1),i%len(pat_2),i%len(pat_3)
        if answers[i] == pat_1[p_1]:
            cor_1 += 1
        if answers[i] == pat_2[p_2]:
            cor_2 += 1
        if answers[i] == pat_3[p_3]:
            cor_3 += 1
    # Append answer
    ans = []
    if cor_1 == max([cor_1,cor_2,cor_3]):
        ans.append(1)
    if cor_2 == max([cor_1,cor_2,cor_3]):
        ans.append(2)
    if cor_3 == max([cor_1,cor_2,cor_3]):
        ans.append(3)
    return ans
```
