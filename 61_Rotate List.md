# 61. Rotate List
###### tags: `leetcode`
https://leetcode.com/problems/rotate-list/

### Solution (2022/3)
二刷！！這次直接順利的解決了(?)而且時間是之前寫的一半XD 行數也是XDDD

```python
class Solution(object):
    def rotateRight(self, head, k):
        """
        :type head: ListNode
        :type k: int
        :rtype: ListNode
        """
        
        count = 0 
        ptr = head
        
        if head == None:
            return head
        
        while ptr.next != None:
            count += 1
            ptr = ptr.next  
        
        ptr.next = head
        count += 1
        
        for i in range(count - k%(count)):
            ptr = ptr.next
        
        head = ptr.next
        ptr.next = None
                
        return head

```

### Solution (2020/3)
    大概發生了幾次WA的問題，後來發現是count在跑的時候沒有設定好，導致last的位置不對。
    另外透過%有效減少跑linkedlist的次數才不會TLE
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        
        if k == 0:
            return head 
        
        if head == None:
            return
        elif head.next == None:
            return head
    
        last = head
        count = 0
        
        while last.next != None:
            count += 1
            last = last.next
        count += 1
        if k <= count:
            times = k
        else:
            times = count + k%count 
               
        for i in range(times):
            last = head
            for j in range(count-2):
                last = last.next
            temp = ListNode(last.next.val)
            last.next = None
            temp.next = head
            head = temp
                 
        return temp
        

```