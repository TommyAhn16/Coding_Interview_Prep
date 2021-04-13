# Balanced Binary Tree

> Easy
>
> [link](https://leetcode.com/problems/balanced-binary-tree/)

# Solution

- DFS recursion to update tree height and check height differences

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    balanced = True
    def isBalanced(self, root: TreeNode) -> bool:
        def dfs(node):
            if not node:
                return -1
            left = dfs(node.left)
            right = dfs(node.right)
            # Make balanced false if hegiht difference is greater than 1
            if abs(left-right) > 1:
                self.balanced = False
            return max(left,right)+1
        dfs(root)
        return self.balanced

```
