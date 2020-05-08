# 993. Cousins in Binary Tree

https://leetcode.com/problems/cousins-in-binary-tree/

### Solution

做dfs，dict用來存每個node的parent和depth，整個dict只會存target的兩個node。dfs一率都要跑左也要跑右所以trace的recursion要寫兩個。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isCousins(self, root: TreeNode, x: int, y: int) -> bool:
        self.info = {}
        self.hasX = False
        self.hasY = False
        
        self.trace(root,x,y,-1,0)
        if self.info[x][0] != self.info[y][0]:
            if self.info[x][1] == self.info[y][1]:
                return True
        return False
        
    def trace(self,node:TreeNode,x:int,y:int,parent:int,depth:int) -> bool:
    
        if node == None:
            return 
        
        if node.val == x or node.val == y:
            self.info[node.val] = [parent,depth]
            
            if node.val == x:
                self.hasX = True
            if node.val == y:
                self.hasY = True            
                
        if self.hasX and self.hasY:
            return
        
        newDepth = depth+1
        
        self.trace(node.left,x,y,node.val,newDepth)
        self.trace(node.right,x,y,node.val,newDepth)
        
        
```

