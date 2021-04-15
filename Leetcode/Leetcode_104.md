# Maximum Depth of Binary Tree

> - Difficulty: Easy
> - Type: Tree problem
> - [link](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

# Solution

- BFS solution using Queue

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import collections
class Solution:
    def maxDepth(self, root: TreeNode) -> int:
        # Check for empty tree
        if not root:
            return 0
        # Make root into a queue
        que = collections.deque([root])
        depth = 0
        # Iterate until que is empty
        while que:
            depth += 1
            for _ in range(len(que)):
                cur_root = que.popleft()
                # If current root has child, append it to que
                if cur_root.left:
                    que.append(cur_root.left)
                if cur_root.right:
                    que.append(cur_root.right)
        return depth

```
