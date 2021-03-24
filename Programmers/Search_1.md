# 타겟 넘버

> Level 2: 혼자 풀지 못함
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/43165)

# Solution

- DFS using recursion
- Two operations possible: +, -
- These operations would either make the number required to sum to the target either bigger or smaller
- Only return 1 when target = 0

```python
def solution(numbers, target):
    def dfs(nums,target):
        if not nums:
            if target == 0:
                return 1
            else:
                return 0
        # 재귀적으로 dfs 를 호출한다
        return dfs(nums[1:],target+nums[0]) + dfs(nums[1:],target-nums[0])

    return dfs(numbers,target)
```
