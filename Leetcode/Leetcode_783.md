# Minimum Distance Between BST Nodes

> Easy
>
> [link](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

# Solution

- Use in-order tree traversal to find the minmum value difference

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import math
class Solution:
    pre_node = 0 # To save previouse node value
    distance = math.inf
    def minDiffInBST(self, root: TreeNode) -> int:
        def dfs(node):
            if not node:
                return
            dfs(node.left)
            # Using in-order tree traversal
            if not self.pre_node:
                self.pre_node = node.val
            else:
                self.distance = min(self.distance, abs(self.pre_node - node.val))
                self.pre_node = node.val

            dfs(node.right)

        dfs(root)
        return self.distance

```
