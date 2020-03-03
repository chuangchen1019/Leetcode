# 83. Remove Duplicates from Sorted List
###### tags: `leetcode`
https://leetcode.com/problems/remove-duplicates-from-sorted-list/
### Solution

```python=
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        
        if head == None:
            return head
        
        ans = head
        now = head.val
        
        while head.next is not None:
            print(now, head.next.val)
            if now == head.next.val:
                head.next = head.next.next
            else:
                now = head.next.val
                head = head.next
                
                
        return ans
```