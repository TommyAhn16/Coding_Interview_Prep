# Network Delay Time

> - Dfficulty: Medium
> - Type: Dijkstra's Algorithm
> - [link](https://leetcode.com/problems/network-delay-time/)

## Solution

- Use Dikstra's Algorithm to greedly select the shortes path to the leaf node when searching through the whole graph.
- Heap(min-heap) was used to maintain order among weight to reach each node.
- Return the maximum time(weight) taken to reach the leaf node

```python
import heapq
import collections
class Solution:
    def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
        # Make graph from input 'times'
        graph = collections.defaultdict(list)
        for u, v, w in times:
            graph[u].append((v,w))

        # Q will be used as a min-heap of weight(time) needed to reach the node
        # [[time cost, node]]
        Q = [[0,k]]

        # Dict to save time taken to reach each node ({node:time taken})
        dist = collections.defaultdict(int)


        while Q:
            # Pop value with minimum weight
            time,node = heapq.heappop(Q)
            # When node was not visited
            if node not in dist:
                dist[node] = time
                for v,w in graph[node]:
                    added_time = time + w
                    heapq.heappush(Q,[added_time,v])

        # When all nodes were visited, find the maximum time needed to reach node
        if len(dist) == n:
            return max(list(dist.values()))
        # When not all nodes were visited, return -1
        return -1
```
