# 24. Swap Nodes in Pairs
###### tags: `leetcode`
https://leetcode.com/problems/swap-nodes-in-pairs/
### Solution
```python=
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def swapPairs(self, head: ListNode) -> ListNode:
        
        if head == None:
            return
        
        dump = ListNode(-1)
        dump.next = head
        index = dump
        while head != None:
            if head.next == None:
                break
            nextIndex = head.next.next
            temp = head.next
            temp.next = head
            dump.next = temp
            head.next = nextIndex
            head = nextIndex
            dump = dump.next.next
        
        return index.next
```