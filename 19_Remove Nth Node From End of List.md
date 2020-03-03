# 19. Remove Nth Node From End of List
###### tags: `leetcode`

![](https://i.imgur.com/6CZBuhZ.png)

---
### Solution
    題目下面有hint只做一輪就能得到解答，但目前還沒嘗試XD

```=python3
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        
        tar = head
        count = 0
        
        if n == 0 :
             return head
        
        while tar != None:
            count += 1
            tar = tar.next
         
        tar = head
        if count == 1:
            return 
        else:
            count = count - n
            if count == 0:
                tar = tar.next
                return tar
            else:
                for i in range(count-1):
                    tar = tar.next
                tar.next = tar.next.next

                return head
```