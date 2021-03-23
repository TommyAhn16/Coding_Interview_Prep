# 소수 찾기

> Level 2
> [link](https://programmers.co.kr/learn/courses/30/lessons/42839)

## My Solution

- Use `permutations` from `itertools`
- Define function to find prime numbers
- 중복되지 않는 모든 숫자 조합을 확인하며 소수를 찾는다

```python
from itertools import permutations
def solution(numbers):
    # Function to find prime number
    def is_prime(n):
        if n < 2:
            return False
        half = n // 2 if n % 2 == 0 else n // 2 + 1
        for i in range(2,half+1):
            if n % i == 0:
                return False
        return True

    count = 0
    unique = set()
    # Go over each permutation and increase prime number count when finding one
    for d in range(1,len(numbers)+1):
        perm = permutations(numbers, d)
        for c in perm:
            num = ""
            for j in range(len(c)):
                num += c[j]
            if int(num) not in unique and is_prime(int(num)):
                unique.add(int(num))
                count += 1
    return count
```
