# 네트워크

> Level 3
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/43162)

# Solution

- 재귀적으로 DFS를 불러 문제 해결

```python
def solution(n, computers):
    # Make the grid
    # example: {index: [connected index]}, {0: [0, 1], 1: [0, 1], 2: [2]}
    grid = {i:[] for i in range(n)}
    for i in range(len(computers)):
        for j in range(len(computers[i])):
            if computers[i][j] == 1:
                grid[i].append(j)

    # Define dfs
    def dfs(i,visited):
        for j in grid[i]:
            if j not in visited:
                visited.add(j)
                visited = dfs(j,visited)
        return visited

    # Find unique network using dfs
    ans = []
    for i in grid.keys():
        network = dfs(i,set())
        if network not in ans:
            ans.append(network)
    return len(ans)
```
