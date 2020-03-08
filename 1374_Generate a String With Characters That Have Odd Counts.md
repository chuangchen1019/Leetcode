# 1374. Generate a String With Characters That Have Odd Counts

### Solution
    Weekly Contest 題目，難度easy，正規題目網址還沒出來
```python=
import string
import random
class Solution:
    def generateTheString(self, n: int) -> str:
        
        ans = ""
        if n%2 == 0:
            temp = random.choice(string.ascii_lowercase)
            for i in range(n-1):
                ans += temp       
            temp2 = random.choice(string.ascii_lowercase)
            if temp2 != temp:
                ans += temp2
            else:
                temp2 = random.choice(string.ascii_lowercase)
                ans += temp2
        else:
            temp = random.choice(string.ascii_lowercase)
            for k in range(n):
                ans += temp
        
        return ans
            
```