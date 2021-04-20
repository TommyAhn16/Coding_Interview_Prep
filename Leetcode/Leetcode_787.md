# Cheapest Flights Within K Stops

> - Difficulty: Medium
> - Type: Dijkstra's Algorithm
> - [link](https://leetcode.com/problems/cheapest-flights-within-k-stops/)

## Solution

- Use Dikstra's Algorithm to greedly select the shortes path to the next node
- Heap(min-heap) was used to maintain order among weight to reach each node.
- Constraint: path cannot exceed k stops, path that exceeds k stops must not be appended to heap.

```python
import collections
import heapq
class Solution:
    def findCheapestPrice(self, n: int, flights: List[List[int]], src: int, dst: int, K: int) -> int:
        # Form graph from list of flights
        graph = collections.defaultdict(list)
        for u, v, w in flights:
            graph[u].append((v,w))

        # Form Q to be used as min-heap of weights
        Q = [(0,src,K)]

        while Q:
            # Greedly choose the path with minimum weight
            weight, node, k = heapq.heappop(Q)
            # Node arrived at destination
            if node == dst:
                return weight
            # When remaining transit is bigger than 0
            if k >= 0:
                for v,w in graph[node]:
                    added_weight = weight + w
                    heapq.heappush(Q,(added_weight,v,k-1))

        return -1


```
