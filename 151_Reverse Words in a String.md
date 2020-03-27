# 151. Reverse Words in a String

https://leetcode.com/problems/reverse-words-in-a-string/

### Solution

​	faster than 97%

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        
        temp = s.split(" ")
        n = len(temp)
        ans,index = "",0
        
        while index < n:
            print(index)
            if temp[index] == '':
                temp.remove(temp[index])
            else:
                index += 1
            n = len(temp)

        for i in range(n):
            ans += temp[n-1-i]
            if i == n-1:
                break
            else:
                ans += " "
        
        return ans
```

