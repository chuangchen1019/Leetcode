# Check If a String Is a Valid Sequence from Root to Leaves Path in a Binary Tree

Given a binary tree where each path going from the root to any leaf form a **valid sequence**, check if a given string is a **valid sequence** in such binary tree. 

We get the given string from the concatenation of an array of integers `arr` and the concatenation of all values of the nodes along a path results in a **sequence** in the given binary tree.

 

**Example 1:**

**![img](https://assets.leetcode.com/uploads/2019/12/18/leetcode_testcase_1.png)**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,0,1]
Output: true
Explanation: 
The path 0 -> 1 -> 0 -> 1 is a valid sequence (green color in the figure). 
Other valid sequences are: 
0 -> 1 -> 1 -> 0 
0 -> 0 -> 0
```

**Example 2:**

**![img](https://assets.leetcode.com/uploads/2019/12/18/leetcode_testcase_2.png)**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,0,1]
Output: false 
Explanation: The path 0 -> 0 -> 1 does not exist, therefore it is not even a sequence.
```

**Example 3:**

**![img](https://assets.leetcode.com/uploads/2019/12/18/leetcode_testcase_3.png)**

```
Input: root = [0,1,0,0,1,0,null,null,1,0,0], arr = [0,1,1]
Output: false
Explanation: The path 0 -> 1 -> 1 is a sequence, but it is not a valid sequence.
```

**Constraints:**

- `1 <= arr.length <= 5000`
- `0 <= arr[i] <= 9`
- Each node's value is between [0 - 9].



### Solution

dfs，index指向array裡的target一邊跟node.val確認是不是相符，如果相符就繼續往下做，不相符就return回上一層。

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidSequence(self, root: TreeNode, arr: List[int]) -> bool:
        self.valid = False 
        self.tracePath(root,arr,0)
        
        return self.valid
        
    def tracePath(self, node: TreeNode, arr: List[int], index: int) -> None:
        if index > len(arr)-1:
            return
        if node.val != arr[index]:
            return 
        else:        
            if node.left:
                self.tracePath(node.left,arr,index+1)
            if node.right:
                self.tracePath(node.right,arr,index+1)
            if node.left == None and node.right == None:
                if index == len(arr)-1:
                    self.valid = True
                
```

