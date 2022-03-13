# 20. Valid Parentheses
###### tags: `leetcode`


![](https://i.imgur.com/6ay8MOv.png)

---

### Solution (2022/3)
使用stack實作，改善list的使用語法(更簡潔)
遇到左括號系列就推進stack，遇到右括號系列就pop出來比較是否配對
並且使用dict rec將左右括號的配對整合 ex左括號小和右括號都對應到數字1，這樣後面在寫判斷式的時候可以用更少的行數達成

```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        
        stack = []
        rec = {'(':1, ')':1, '[':2, ']':2, '{':3, '}':3 }
        
        for char in s:
            if char == '(' or char == '[' or char == '{':
                stack.append(char)
            else:
                if stack == []:
                    return False
                if rec.get(char) == rec.get(stack[-1]):
                    stack.pop()
                else:
                    return False
            
        if stack != []:
            return False
        else:
            return True

```


### Solution (2020/2)
使用stack實作，算是資料結構的標準解法(?)
不過同時還要考慮配對順序，不然會錯。

```python
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