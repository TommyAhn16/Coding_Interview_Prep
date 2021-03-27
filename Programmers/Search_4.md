# 여행경로

> Level 3: Couldn't solve
>
> [link](https://programmers.co.kr/learn/courses/30/lessons/43164)

# Solution

- Constraints: use all the tickets, all locations are connected to each other

```python
import collections
def solution(tickets):
    # Sort tickets and make graph
    graph = collections.defaultdict(list)
    for a,b in sorted(tickets,reverse=True):
        graph[a].append(b)

    # Use dfs to search for path to use all tickets
    path = []
    def dfs(start):
        # this while loop ensures that we check all the locations that we visit once
        while graph[start]:
            dest = graph[start].pop()
            dfs(dest)
        path.append(start)

    dfs('ICN')
    return path[::-1]
```

# Code to help understand

```python
import collections
tickets = ['ICN' ,'B'], ['ICN', 'C'] ,['C', 'D'], ['D', 'ICN']
graph = collections.defaultdict(list)
for a,b in sorted(tickets,reverse=True):
    graph[a].append(b)
print(graph)
path = []
def dfs(start):
    print("start: ", start)
    while graph[start]:
        dest = graph[start].pop()
        print("dest: ", dest)
        dfs(dest)

    print("appending: ", start)
    path.append(start)

dfs('ICN')
path[::-1]
```

graph: {'ICN': ['C', 'B'], 'D': ['ICN'], 'C': ['D']}
start: ICN
dest: B
start: B
appending: B
dest: C
start: C
dest: D
start: D
dest: ICN
start: ICN
appending: ICN
appending: D
appending: C
appending: ICN
path = ['ICN', 'C', 'D', 'ICN', 'B']
