# 13. Roman to Integer
###### tags: `leetcode`

題目跟integer to roman一樣。
![](https://i.imgur.com/IOUT2RF.png)


---
### Solution
    完全的暴力解法，從此之後知道大量的對應資料可以存在dic或是map中QQ

```python=
class Solution:
    def romanToInt(self, s: str) -> int:
        
        n = len(s)
        ans = 0
        index = n-1
        final = 0
       
        while index >= 0 :
            
            if index-1 == -1:
                final = 1
                
            if s[index] == "I":
                ans += 1
            elif s[index] == "V":
                ans += 5
                if s[index-1] == "I" and final != 1:
                    ans -= 1
                    index -= 1

            elif s[index] == "X":
                ans += 10
                if s[index-1] == "I" and final != 1:
                    ans -= 1
                    index -= 1

            elif s[index] == "L":
                ans += 50
                if s[index-1] == "X" and final != 1:
                    ans -= 10 
                    index -= 1
            elif s[index] == "C":
                ans += 100
                if s[index-1] == "X" and final != 1:
                    ans -= 10 
                    index -= 1
            elif s[index] == "D":
                ans += 500
                if s[index-1] == "C" and final != 1:
                    ans -= 100 
                    index -= 1
            elif s[index] == "M":
                ans += 1000
                if s[index-1] == "C" and final != 1:
                    ans -= 100 
                    index -= 1
            index -= 1
           
        
        return ans
```