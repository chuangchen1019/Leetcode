# 1008. Construct Binary Search Tree from Preorder Traversal

https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/

Return the root node of a binary **search** tree that matches the given `preorder` traversal.

*(Recall that a binary search tree is a binary tree where for every node, any descendant of `node.left` has a value `<` `node.val`, and any descendant of `node.right` has a value `>` `node.val`. Also recall that a preorder traversal displays the value of the `node` first, then traverses `node.left`, then traverses `node.right`.)*

**Example 1:**

```
Input: [8,5,1,7,10,12]
Output: [8,5,10,1,7,null,12]
```

**Note:** 

1. `1 <= preorder.length <= 100`
2. The values of `preorder` are distinct.



### Solution

由於是preorder所以list第一個元素必為root，接下來每次都從root判斷node應該要insert在哪裡(ex.比root大就往root.right移動)，最後再進行insert即可。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def bstFromPreorder(self, preorder: List[int]) -> TreeNode:
        
        if preorder == []:
            return 
        root = TreeNode(preorder[0])
        for i in range(1,len(preorder)):
            self.dfs(root,preorder[i])
                
        return root
    
    def dfs(self,root:TreeNode,val:int) ->None:
        
        temp = TreeNode(val)             
        if val < root.val:
            if root.left:
                self.dfs(root.left,val)
            else:
                root.left = temp
        elif val > root.val:
            if root.right:
                self.dfs(root.right,val)
            else:
                root.right = temp
                
```

