# 155. Min Stack
###### tags: `leetcode`
![](https://i.imgur.com/EM08q48.png)

---
### Solution
    製作一個stack滿足基本功能，這邊大概比較要注意的是self的用法，基本宣告之類的

```python
class MinStack:

    def __init__(self):
        
        self.stack = []
        self.minStack = []
                
    def push(self, x: int) -> None: 
        
        self.stack.append(x)
        if len(self.stack) == 1:
            self.minStack.append(self.stack[0])
        else:
            self.minStack.append(min(self.minStack[-1],x))
       
        
    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()
        

    def top(self) -> int:
        return self.stack[-1]
    
    def getMin(self) -> int:
        return self.minStack[-1]
        

# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

