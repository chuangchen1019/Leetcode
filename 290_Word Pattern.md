# 290. Word Pattern

https://leetcode.com/problems/word-pattern/

### Solution

```python
class Solution:
    def wordPattern(self, pattern: str, str: str) -> bool:
        
        pat = list(pattern)
        strs = str.split(" ")
        
        temp = {}
        x = set()
        n = len(pat)
        s = len(strs)
        if n != s:
            return False
        
        for i in range(n):
            
            if pat[i] not in temp and strs[i] not in x:
                temp.update({pat[i]:strs[i]})
                x.add(strs[i])
            else:
                if strs[i] == temp.get(pat[i]):
                    continue
                else:
                    return False         
        
        return True
```

