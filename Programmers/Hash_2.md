# 전화번호 목록

> Level 2

> [link](https://programmers.co.kr/learn/courses/30/lessons/42577)

## My solution

- 길이가 짧은 전화 번호를 lookup 이라는 set 에 저장하여 일부분이 일치하는 다른 전화번호를 찾는다

```python
def solution(phone_book):
    phone_book.sort(key=len)
    length = {len(num) for num in phone_book}
    lookup = set()
    for num in phone_book:
        for lens in length:
            if len(num) > lens:
                lookup.add(num[:lens])
    for num in phone_book:
        if num in lookup:
            return False

    return True
```
