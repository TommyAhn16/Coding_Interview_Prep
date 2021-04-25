# Employee Importance

> - Difficulty: Easy
> - Type: DFS/BFS
> - [link](https://leetcode.com/problems/employee-importance/)

## Solution

- BFS solution to search and add all the importance related to the query employee

```python
"""
# Definition for Employee.
class Employee:
    def __init__(self, id: int, importance: int, subordinates: List[int]):
        self.id = id
        self.importance = importance
        self.subordinates = subordinates
"""
import collections
class Solution:
    def getImportance(self, employees: List['Employee'], id: int) -> int:
        total = 0
        employees = {em.id:em for em in employees}
        que = collections.deque([id])
        # BFS
        while que:
            em_id = que.popleft()
            total += employees[em_id].importance
            for i in employees[em_id].subordinates:
                que.append(i)

        return total
```

- DFS Solution

```python
"""
# Definition for Employee.
class Employee:
    def __init__(self, id: int, importance: int, subordinates: List[int]):
        self.id = id
        self.importance = importance
        self.subordinates = subordinates
"""
class Solution:
    total = 0
    def getImportance(self, employees: List['Employee'], id: int) -> int:
        employees = {em.id:em for em in employees}
        # DFS
        def dfs(em_id):
            if em_id not in employees:
                return
            self.total += employees[em_id].importance
            for i in employees[em_id].subordinates:
                dfs(i)
            return
        dfs(id)
        return self.total
```
