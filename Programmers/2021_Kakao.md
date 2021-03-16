# 2021 Kakao Blind Recruitment

## Probelm 1

> [link](https://programmers.co.kr/learn/courses/30/lessons/72410)
> Key point: String manipulation, regular expression

- Optimal solution

```python
import re

def solution(new_id):
    st = new_id
    # Change string to lower case
    st = st.lower()
    st = re.sub('[^a-z0-9\-_.]', '', st)
    st = re.sub('\.+', '.', st)
    st = re.sub('^[.]|[.]$', '', st)
    st = 'a' if len(st) == 0 else st[:15]
    st = re.sub('^[.]|[.]$', '', st)
    st = st if len(st) > 2 else st + "".join([st[-1] for i in range(3-len(st))])
    return st
```
