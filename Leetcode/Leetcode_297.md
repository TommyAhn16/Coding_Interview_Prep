# Serialize and Deserialize Binary Tree

> Hard
>
> [link](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

# Solution

- Use BFS to wrap and unwrap tree to string and string to tree

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
import collections
class Codec:

    def serialize(self, root):
        """Encodes a tree to a single string.

        :type root: TreeNode
        :rtype: str
        """
        if not root:
            return ""
        # BFS to convert tree to string
        visited = [root.val]
        que = collections.deque([root])
        while que:
            for _ in range(len(que)):
                cur_node = que.popleft()
                if cur_node.left:
                    que.append(cur_node.left)
                    visited.append(cur_node.left.val)
                else:
                    visited.append('null')
                if cur_node.right:
                    que.append(cur_node.right)
                    visited.append(cur_node.right.val)
                else:
                    visited.append('null')
        return ",".join(map(str,visited))



    def deserialize(self, data):
        """Decodes your encoded data to tree.

        :type data: str
        :rtype: TreeNode
        """
        if not data:
            return
        data = collections.deque([None if x == "null" else int(x) for x in data.split(",") ])
        # BFS to unwrap string to a tree again
        root = TreeNode(data.popleft())
        que = collections.deque([root])
        while que:
            for _ in range(len(que)):
                cur_node = que.popleft()
                if not data:
                    break
                left = data.popleft()
                right = data.popleft()
                if left != None:
                    left = TreeNode(left)
                    cur_node.left = left
                    que.append(left)
                if right != None:
                    right = TreeNode(right)
                    cur_node.right = right
                    que.append(right)
        return root


# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))
```
