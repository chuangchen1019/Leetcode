# 99. Recover Binary Search Tree
https://leetcode.com/problems/recover-binary-search-tree/


### Solution-1
- 先跑一次樹將植存起來
- 用inorder跑的話，value會從小到大排列
- 兩兩比較找出需要被swap的兩個值
- 再跑一次tree，完成swap的動作
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def recoverTree(self, root):
        """
        :type root: TreeNode
        :rtype: None Do not return anything, modify root in-place instead.
        """
        rec = []
        fir, sec = 0, 0
        count = 0
        
        self.inorder(root, rec)
        
        for index in range(len(rec)):
            if index < len(rec)-1:
                if rec[index] > rec[index+1]:
                    count += 1
                    if count == 1:
                        fir = rec[index]
                        sec = rec[index+1]
                    else:
                        sec = rec[index+1]

        self.swap(root, fir, sec)
        
        return
                    
    
    def inorder(self, root, rec):
        if root != None:
            self.inorder(root.left, rec)
            rec.append(root.val)
            self.inorder(root.right, rec)
        else:
            return
    
    def swap(self, root, fir, sec):
        if root != None:
            if root.val == fir:
                root.val = sec
            elif root.val == sec:
                root.val = fir
            self.swap(root.left, fir, sec)
            self.swap(root.right, fir, sec)
        else:
            return
```