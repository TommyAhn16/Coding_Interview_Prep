# Binary Search Tree to Greater Sum Tree

> Medium
>
> [link](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/)

# Solution

- Use in-order (start from right->current->left) to update greater value

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    greater = 0
    def bstToGst(self, root: TreeNode) -> TreeNode:
        def dfs(root):
            if not root:
                return 0

            # Use in-order tree traversal method to update greater value
            right = dfs(root.right)
            self.greater += root.val
            root.val = self.greater
            left = dfs(root.left)
            return root.val

        dfs(root)
        return root
```
