# 203. Remove Linked List Elements

https://leetcode.com/problems/remove-linked-list-elements/

Remove all elements from a linked list of integers that have value ***val\***.

**Example:**

```
Input:  1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5
```

### Solution

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        
        start = ListNode(-1)
        start.next = head
        temp = start
        while head:
            if head.val == val: 
                if head.next:
                    temp.next = head.next
                    head = head.next
                    continue
                else:
                    temp.next = None
            temp = temp.next
            head = head.next
                
        return start.next
```

