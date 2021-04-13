# Minimum Height Trees

> Medium
>
> [link](https://leetcode.com/problems/minimum-height-trees/)

# Solution

- Eliminate leaf nodes iteratively until finding the minimum tree height roots.

```python
import collections
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        if not edges:
            return [0]
        # Create graph to show connections
        graph = collections.defaultdict(list)
        for i,j in edges:
            graph[i].append(j)
            graph[j].append(i)

        leaves = []
        # Find and save leaf nodes (node with only 1 connection)
        for i in range(n+1):
            if len(graph[i]) == 1:
                leaves.append(i)
        # Repeat until no leaf nodes left (roots with minimum height)
        while n > 2:
            n -= len(leaves)
            new_leaves = []
            for leaf in leaves:
                neighbor = graph[leaf].pop()
                graph[neighbor].remove(leaf)
                if len(graph[neighbor]) == 1:
                    new_leaves.append(neighbor)
            leaves = new_leaves
        # Last remaining nodes are the roots with minimum tree heights
        return leaves

```
