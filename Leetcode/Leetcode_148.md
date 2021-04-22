# Sort List

> - Difficulty: Medium
> - Type: Sorting
> - [link](https://leetcode.com/problems/sort-list/)

## Solution

- Using Python built-in sorting function
- Time Complexity: O(n log n)
- Space Complexity: O(n) (for the list made to store values)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def sortList(self, head: ListNode) -> ListNode:
        if not head:
            return head

        # Save values in linked list
        vals = []
        p = head
        while p:
            vals.append(p.val)
            p = p.next

        # Sort the values in desending order
        vals.sort(reverse=True)
        # Change values in link list
        p = head
        while vals:
            p.val = vals.pop()
            p = p.next

        return head
```
