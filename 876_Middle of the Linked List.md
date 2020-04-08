# 876. Middle of the Linked List

https://leetcode.com/problems/middle-of-the-linked-list/

### Solution

```python
class Solution:
    def middleNode(self, head: ListNode) -> ListNode:
        
        if head.next == None:
            return head
        count = 0
        temp = head
        while head != None:
            if count%2 : 
                temp = temp.next
            count += 1
            head = head.next
        
        return temp
```



