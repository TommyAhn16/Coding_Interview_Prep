# Reconstruct Itinerary

> Medium
>
> [link](https://leetcode.com/problems/reconstruct-itinerary/)

# Solution

- DFS to recursively search until using all tickets
- sort the graph in alphabetical order before calling DFS

```python
import collections
class Solution:
    def findItinerary(self, tickets: List[List[str]]) -> List[str]:
        graph = collections.defaultdict(list)
        for f,t in sorted(tickets, reverse=True):
            graph[f].append(t)

        path = []
        def dfs(start):
            while graph[start]:
                to = graph[start].pop()
                dfs(to)
            path.append(start)

        dfs("JFK")
        return path[::-1]
```
