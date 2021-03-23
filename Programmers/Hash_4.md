# 베스트앨범

> Level 3

> [link](https://programmers.co.kr/learn/courses/30/lessons/42579)

## My solution

- Complicated hashing problem. But can be solved by following instructions.

```python
def solution(genres, plays):
    dic = {}
    for i, g in enumerate(genres):
        if g not in dic:
            dic[g] = [plays[i],{i:plays[i]}]
            # example: {"pop": [600,{1:600}]
        else:
            dic[g][0] += plays[i]
            # example: {"pop": [3100,{1:600, 4:2500}]
            dic[g][1].update({i:plays[i]})
    ans = []
    songs = sorted(list(dic.values()),key=lambda x: x[0],reverse=True)
    for s in songs:
        s_dic = s[1]
        temp = sorted(s_dic,key=lambda x: s_dic[x], reverse=True)
        if len(temp) == 1:
            ans.append(temp[0])
        else:
            if s_dic[temp[0]] == s_dic[temp[1]]:
                ans += sorted(temp[:2])
            else:
                ans += temp[:2]

    return ans
```
