# 14. Longest Common Prefix

![](https://i.imgur.com/5wAF0RW.png)


---
### Solution

```python3=
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        
        com = []
        ans = ""
        flag,minLen = 0,0

        if strs == []:
            return ""
        
        n = len(strs)
        for i in range(n):
            if i == 0 :
                minLen = len(list(strs[0]))
            com.append(list(strs[i]))
            minLen = min(len(list(strs[i])),minLen)
        
        index = 0
        while index < minLen:
            print(index)
            for i in range(n):
                target = com[0][index] 
                if com[i][index] != target:
                    flag = 0
                    break
                else:
                    flag = 1
            if flag == 1:
                ans += com[0][index]
            else:
                return ans
            index += 1
            
        return ans
```
