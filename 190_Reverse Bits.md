# 190. Reverse Bits
###### tags: `leetcode`
https://leetcode.com/problems/reverse-bits/
### Solution
```python=
class Solution:
    def reverseBits(self, n: int) -> int:
        
        if n == 0:
            return 0
        count,ans = 32,0
        while count != 0:
            k = n % 2
            n = int(n/2)
            ans *= 2
            if k == 1:
                ans += k
            count -= 1
    
        return ans
```