# 191. Number of 1 Bits

https://leetcode.com/problems/number-of-1-bits/

### Solution

​	brute force, can use bit operation to optimize

``` python
class Solution:
    def hammingWeight(self, n: int) -> int:
        
        if n == 0:
            return 0
        ans = 0
        while n != 0:
            temp = n%2
            if temp == 1:
                ans += 1         
            n = int(n/2)
        
        return ans
```

