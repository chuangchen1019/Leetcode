# 21. Merge Two Sorted Lists
###### tags: `leetcode`

![](https://i.imgur.com/XOIQxJJ.png)

---
### Solution

    下面是同時比較兩個linked list的第一個node，將較小的加入新的linked list。
    有想到另一種做法->直接修改第一個linked list，將第二條的各個node依序插入。

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        
        ans = ListNode(0)
        head = ans
        count = 0
        
        while True:
            
            if l1 == None:
                ans.next = l2
                break
            elif l2 == None:
                ans.next = l1
                break
            else:
                if l1.val <= l2.val:
                    temp = l1
                    l1 = l1.next
                    temp.next = None
                    ans.next = temp                   
                else:
                    temp = l2
                    l2 = l2.next
                    temp.next = None
                    ans.next = temp
 
                ans = ans.next
                
        
        return head.next
```