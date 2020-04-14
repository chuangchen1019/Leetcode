# Diameter of Binary Tree

**Example:**
Given a binary tree

```
          1
         / \
        2   3
       / \     
      4   5    
```

Return **3**, which is the length of the path [4,2,1,3] or [5,2,1,3].

**Note:** The length of path between two nodes is represented by the number of edges between them.

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

