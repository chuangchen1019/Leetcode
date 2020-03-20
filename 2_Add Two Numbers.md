# 2. Add Two Numbers
###### tags: `leetcode`
https://leetcode.com/problems/add-two-numbers/

### Solution
```python
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        
        ListNode answer = new ListNode(0);
        ListNode first = answer;
        int flag = 0;

        while(l1 != null && l2 != null){     
            
            int ans = l1.val + l2.val + flag;
            if(ans <10){
                flag = 0;
            }
            else{
                flag = 1;
                ans -= 10;
            }     
            answer.next = new ListNode(ans);
            answer = answer.next;
            l1 = l1.next;
            l2 = l2.next;
        }

        ListNode notNull = null;

        if(l1 != null){
            notNull = l1; 
        }
        else if(l2 != null){
            notNull = l2;
        }
        
        while(notNull != null){
            int ans = notNull.val + flag;
            if(ans < 10)
                flag = 0;
            else{
                flag = 1;
                ans -= 10;
            }
            answer.next = new ListNode(ans);
            answer = answer.next;
            notNull = notNull.next;
            
        }
        
        if(flag == 1){
            answer.next = new ListNode(1);
            answer = answer.next;
        }
            
        return first.next;
    }   
}
```