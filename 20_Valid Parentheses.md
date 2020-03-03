# 20. Valid Parentheses
###### tags: `leetcode`


![](https://i.imgur.com/6ay8MOv.png)


---
### Solution
    使用stack實作，算是資料結構的標準解法(?)
    不過同時還要考慮配對順序，不然會錯。

```python=
class Solution:
    def isValid(self, s: str) -> bool:
        
        element = list(s)
        n = len(element)
        target = ""
        
        stack = []
        
        for i in range(n): 
            if element[i] in ["(","{","["]:
                stack.insert(0,element[i])
            else:
                if element[i] == ")":
                    target = "("
                elif element[i] == "}":
                    target = "{"
                elif element[i] == ']':
                    target = "["
                
                if stack == []:
                    return False
                
                if stack[0] != target:
                    return False
                else:
                    stack.remove(stack[0])
        
        if stack == []:
            return True
        else:
            return False
            
```