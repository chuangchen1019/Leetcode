# 844. Backspace String Compare

https://leetcode.com/problems/backspace-string-compare/

### Solution

Stack approach (beats 90%)

```python
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        
        if self.opt(S) == self.opt(T):
            return True
        else:
            return False
    
    def opt(self, input:str) -> str:
        s = list(input)
        temp = []
        l = len(input)
        k = ""
        for i in range(l):
            if input[i] != "#":
                temp.append(input[i])
            else:
                if temp != []:
                    temp.pop()
                else:
                    continue
            
            l = len(input)
        k = k.join(temp)
        return k
```

---

Normal approach

```python
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        
        s1 = self.operation(S)
        s2 = self.operation(T)
        
        if s1 == s2:
            return True
        else:
            return False
           
    def operation(self,input: str) -> str:
        s = ""
        temp = list(input)
        n = len(temp)
        index = 0
        
        while index < n:
            if temp[index] == '#':
                if index-1 < 0:
                    temp = temp[:index] + temp[index+1:]
                    
                else:
                    temp = temp[:index-1] + temp[index+1:]
                    index -= 1
            else:
                index += 1
            n = len(temp)           
        s = s.join(temp)

        return s
            
```

