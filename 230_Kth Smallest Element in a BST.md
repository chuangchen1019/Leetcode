# 230. Kth Smallest Element in a BST
https://leetcode.com/problems/kth-smallest-element-in-a-bst/

### Solution
- 先將tree的每個node val跑一次並存在list中
- 將list排序過
- return第k-1個list中的元素
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def kthSmallest(self, root, k):
        """
        :type root: TreeNode
        :type k: int
        :rtype: int
        """
        rec = []
        self.traversal(root, rec)
        rec.sort()
        
        return rec[k-1]
        
    def traversal(self, root, rec):
        if root != None:
            rec.append(root.val)
            self.traversal(root.left, rec)
            self.traversal(root.right, rec)
        else:
            return
```