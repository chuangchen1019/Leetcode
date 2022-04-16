# 538. Convert BST to Greater Tree
https://leetcode.com/problems/convert-bst-to-greater-tree/


### Solution
- 用一個rec紀錄每個Node的值
- 下一次跑node的時候每次用loop去計算比該node要大的值總，並且設定。
- 算是暴力解法XD

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def convertBST(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """

        if root == None:
            return root
        
        rec = []
        self.getNode(root, rec)
        self.setNode(root, rec)
        
        return root
        
    def getNode(self, root, rec):
        if root != None:
            rec.append(root.val)
            self.getNode(root.left, rec)
            self.getNode(root.right, rec)
        
        else:
            return
        
    def setNode(self, root, rec):
        if root != None:
            temp = 0
            for num in rec:
                if num > root.val:
                    temp += num
            root.val = root.val + temp
            self.setNode(root.left, rec)
            self.setNode(root.right, rec)
        else:
            return
```