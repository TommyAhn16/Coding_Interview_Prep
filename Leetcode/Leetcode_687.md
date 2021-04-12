# Longest Univalue Path

> Medium
>
> [link](https://leetcode.com/problems/longest-univalue-path/)

# Solution

- Post-order tree traversal: need to check left and right child first before checking node itself
- DFS to search tree
- Update longest unival path length in every search

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    # Initialize longest univalue path
    longest = 0
    def longestUnivaluePath(self, root: TreeNode) -> int:
        def dfs(node):
            # Return 0 for leaf node
            if not node:
                return 0
            # Left, right univalue path
            left = dfs(node.left)
            right = dfs(node.right)
            # Update longest path if values match
            if node.left and node.left.val == node.val:
                left += 1
            else:
                left = 0
            if node.right and node.right.val == node.val:
                right += 1
            else:
                right = 0
            self.longest = max(self.longest, left+right)
            # Only return the maximum path of either left or right
            # Because path is unidirectional (can't visited both left and right child)
            return max(right,left)
        dfs(root)
        return self.longest
```
