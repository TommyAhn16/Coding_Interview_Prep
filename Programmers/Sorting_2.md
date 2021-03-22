# Sorting Question 2

> [link](https://programmers.co.kr/learn/courses/30/lessons/42746)
>
> - very difficult question for me

## Bubble sort solution

- O(n^2) time complexity
- Timed out

```python
# Bubble sort solution
def solution(numbers):
    s_num = list(map(str, numbers))
    for i in range(len(s_num)):
        for j in range(len(s_num)-1):
            if int(s_num[j]+s_num[j+1]) < int(s_num[j+1]+s_num[j]):
                # swap values
                s_num[j],s_num[j+1] = s_num[j+1],s_num[j]
    return str(int("".join(s_num)))
```

## Insertion sort solution

- Average, worst = O(n^2)
- Best = O(n)
- Timed out

```python
# Insertion sort solution
def solution(numbers):
    i = 0
    while i < len(A):
        j = i
        while j > 0 and int(A[j-1]+A[j]) < int(A[j]+A[j-1]):
            A[j-1],A[j] = A[j], A[j-1]
            j -= 1
    i += 1
    return str(int("".join(A)))
```

## Optimal solution

- O(n log n) time complexity by using python built-in sort function
- Used 'rich comparison method': `__lt__`: define what is considered less than
  |Rich Comparison Method| Meaning|
  |---|---|
  |`__lt__`|define what is less than|
  |`__gt__`|define what is greater than|
  |`__le__`|define what is less or equal|
  |`__ge__`|define what is greater or equal|
  |`__eq__`|define what is equal|

```python
def solution(numbers):
    class LargerNumKey(str):
        def __lt__(x, y):
            return x+y > y+x

    largest_num = ''.join(sorted(map(str, numbers), key=LargerNumKey))
    return '0' if largest_num[0] == '0' else largest_num
```
