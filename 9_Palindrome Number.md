# 9. Palindrome Number
###### tags: `leetcode`
![](https://i.imgur.com/52tEyfp.png)

### Solution


```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        
        if x < 0:
            return False
        
        s = list(str(x))
        
        n , times = len(s) , 0
        if n == 1:
            return True
        
        if n%2 == 0:
            times = int(n/2)
        else:
            times = int((n-1)/2)
          
        for i in range(times):
            if s[i] != s[n-1-i]:
                return False
        
        return True
        
```