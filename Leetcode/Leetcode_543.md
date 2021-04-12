# Diameter of Binary Tree

> Easy
>
> [link](https://leetcode.com/problems/diameter-of-binary-tree/)

# Solution

- Tree traversal using DFS
- Post-order tree traversal. Left -> Right -> Current Node
- Update longest length while traversing

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    longest: int = 0
    def diameterOfBinaryTree(self, root: TreeNode) -> int:
        def dfs(node: TreeNode) -> int:
            # Return when reaching leaf node
            if not node:
                return 0
            # Search left and right node upto leaf node
            left = dfs(node.left)
            right = dfs(node.right)
            # Update longest path
            self.longest = max(self.longest,left+right)
            # Current state, +1 for distance between parent and child
            return max(left,right) + 1
        dfs(root)
        return self.longest
```
