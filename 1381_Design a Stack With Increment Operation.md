# 1381. Design a Stack With Increment Operation
###### tags: `leetcode`
https://leetcode.com/problems/design-a-stack-with-increment-operation/

### Solution
```python
class CustomStack:

    def __init__(self, maxSize: int):
        self.stack = []
        self.maxVal = maxSize

    def push(self, x: int) -> None:    
         if len(self.stack) < self.maxVal:
            self.stack.insert(0,x)
            
    def pop(self) -> int:
        if len(self.stack) == 0:
            return -1
        else:
            top = self.stack[0]
            self.stack.pop(0)
            return top
        
    def increment(self, k: int, val: int) -> None:

        n = len(self.stack)
        if n < k:
            for i in range(n):
                self.stack[i] += val
        else:
            for j in range(n-k,n):
                self.stack[j] += val

# Your CustomStack object will be instantiated and called as such:
# obj = CustomStack(maxSize)
# obj.push(x)
# param_2 = obj.pop()
# obj.increment(k,val)
```

