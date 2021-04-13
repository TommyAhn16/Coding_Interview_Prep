# Convert Sorted Array to Binary Search Tree

> Easy
>
> [link](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

# Solution

- Recursively call function to always choose the middle as the attaching node in a sorted array (it would guarantee to have the least height difference between both sides)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import collections
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        if not nums:
            return None
        elif len(nums) == 1:
            return TreeNode(nums[0])

        mid = len(nums) // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root

```
