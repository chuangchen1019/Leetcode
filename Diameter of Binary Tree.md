# Diameter of Binary Tree

### Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def diameterOfBinaryTree(self, root: TreeNode) -> int:
        self.length = 0
        if root == None:
            return 0
        else:
            self.maxDepth(root)
        
        return self.length
    
    def maxDepth(self,node: TreeNode) -> int:
        if node == None:
            return 0
        left_depth = self.maxDepth(node.left)
        right_depth = self.maxDepth(node.right)
        
        self.length = max(self.length, left_depth+right_depth)
        return max(left_depth,right_depth)+1
```

