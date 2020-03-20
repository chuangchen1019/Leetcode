# 62. Unique Paths
###### tags: `leetcode`
https://leetcode.com/problems/unique-paths/

### Solution
    faster than 89.68% submissions!!
    在做階乘上有花了點心思讓計算量少一點(?)
```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:

        if m >= n:
            m = m-1
            n = n-1
        else:
            temp = m
            m = n-1
            n = temp-1
                
        return int(self.factorial(n+1,m+n) / self.factorial(1,m))
    
    
    def factorial(self,start:int,end:int) -> int:
        re = 1
        for i in range(start,end+1):
            re *= i
        
        return re
```