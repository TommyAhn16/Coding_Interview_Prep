# My Calendar I

> - Difficulty: Medium
> - Type: Binary Tree
> - [link](https://leetcode.com/problems/my-calendar-i/)

## Solution

- Binary tree solution
- Time Complexity: (From Leetcode Solution) O(n^2) worst case, with O(n log n) on random data. For each new event, we insert the event into our binary tree. As this tree may not be balanced, it may take a linear number of steps to add each event.

```python
# Create Binary Tree
class Node:
    def __init__(self,start,end):
        self.start = start
        self.end = end
        self.right,self.left = None, None

    def insert(self,node):
        if node.start >= self.end:
            if not self.right:
                self.right = node
                return True
            return self.right.insert(node)
        elif node.end <= self.start:
            if not self.left:
                self.left = node
                return True
            return self.left.insert(node)
        else:
            return False


class MyCalendar:

    def __init__(self):
        self.root = None

    def book(self, start: int, end: int) -> bool:
        if not self.root:
            self.root = Node(start,end)
            return True
        return self.root.insert(Node(start,end))



# Your MyCalendar object will be instantiated and called as such:
# obj = MyCalendar()
# param_1 = obj.book(start,end)
```

- Brute Force solution
- Time Complexity: O(n^2) (n = number for events booked)
- Space complexity: O(n)

```python
class MyCalendar:

    def __init__(self):
        self.calender = {}

    def book(self, start: int, end: int) -> bool:
        if not self.calender:
            self.calender[start] = end
            return True

        for k in self.calender.keys():
            if k < start and self.calender[k] > start:
                return False
            elif k > start and k < end:
                return False
            elif k == start:
                return False

        self.calender[start] = end
        return True



# Your MyCalendar object will be instantiated and called as such:
# obj = MyCalendar()
# param_1 = obj.book(start,end)
```
