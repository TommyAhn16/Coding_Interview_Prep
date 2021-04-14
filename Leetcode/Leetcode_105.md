# Construct Binary Tree from Preorder and Inorder Traversal

> Medium
>
> [link](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

# Solution

- Nodes in preorder are parent nodes
- These nodes divide inorder as left branch and right branch
- Recursively attach left and right branch

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import collections
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:
        if inorder and preorder:
            index = inorder.index(preorder.pop(0))
            node = TreeNode(inorder[index])
            node.left = self.buildTree(preorder,inorder[:index])
            node.right = self.buildTree(preorder,inorder[index+1:])

            return node
```
