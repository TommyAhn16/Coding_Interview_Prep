# Range Sum of BST

> Easy
>
> [link](https://leetcode.com/problems/range-sum-of-bst/)

# Solution

- Brute force DFS solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    total = 0
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:

        def dfs(root):
            if not root:
                return
            # Only add values between the range
            if root.val <= high and root.val >= low:
                self.total += root.val
            dfs(root.left)
            dfs(root.right)

        dfs(root)
        return self.total
```

- Tree prunning with DFS

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:

        def dfs(root):
            if not root:
                return 0
            # Only search for nodes that are within the range
            if root.val < low:
                return dfs(root.right)
            elif root.val > high:
                return dfs(root.left)
            return root.val + dfs(root.left) + dfs(root.right)

        return dfs(root)
```

- Iterative way of prunning with DFS

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rangeSumBST(self, root: TreeNode, low: int, high: int) -> int:
        stack = [root]
        total = 0

        while stack:
            cur_node = stack.pop()
            if cur_node:
                # Only append nodes that can be in the range
                if cur_node.val > low:
                    stack.append(cur_node.left)
                if cur_node.val < high:
                    stack.append(cur_node.right)
                if low <=cur_node.val<= high:
                    total += cur_node.val

        return total
```
