# Invert Binary Tree

> Easy
>
> [link](https://leetcode.com/problems/invert-binary-tree/)

# Solution

- Tree post-order traversal method
- Implement DFS recursively

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:
        def dfs(node):
            if not node:
                return node
            left = dfs(node.left)
            right = dfs(node.right)
            # Switch left and right child nodes
            node.left,node.right = right,left
            return node
        dfs(root)
        return root
```

- Using BFS

```python
import collections
class Solution:
    def invertTree(self, root: TreeNode) -> TreeNode:

        que = collections.deque([root])
        while que:
            cur_node = que.popleft()
            if cur_node:
                cur_node.left, cur_node.right = cur_node.right, cur_node.left
                que.append(cur_node.left)
                que.append(cur_node.right)
        return root
```
