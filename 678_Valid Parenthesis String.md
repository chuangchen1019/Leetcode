# 678. Valid Parenthesis String

https://leetcode.com/problems/valid-parenthesis-string/

Given a string containing only three types of characters: '(', ')' and '*', write a function to check whether this string is valid. We define the validity of a string by these rules:

1. Any left parenthesis `'('` must have a corresponding right parenthesis `')'`.
2. Any right parenthesis `')'` must have a corresponding left parenthesis `'('`.
3. Left parenthesis `'('` must go before the corresponding right parenthesis `')'`.
4. `'*'` could be treated as a single right parenthesis `')'` or a single left parenthesis `'('` or an empty string.
5. An empty string is also valid.

**Example 1:**

```
Input: "()"
Output: True
```

**Example 2:**

```
Input: "(*)"
Output: True
```

**Example 3:**

```
Input: "(*))"
Output: True
```

**Note:**

1. The string size will be in the range [1, 100].

### Solution

這題主要是base on 合法的括號配對之上，又加上*的題型，主要也是用stack做，但這題比較不一樣的是要多個stack去存星號，以用來跟左括弧或是右括弧進行配對的動作。

```python
class Solution:
    def checkValidString(self, s: str) -> bool:
        
        stack = []
        star = [] 
        
        temp = list(s)
        
        for index in range(len(temp)):
            if s[index] == "(":
                stack.append(index)
                
            elif s[index] == "*":
                star.append(index)
                
            else:
                if stack != []:
                    stack.pop()
                else:
                    if star != []:
                        star.pop()
                    else:
                        return False        
        
        while stack != [] and star != []:
            if stack[-1] > star[-1]:
                return False
            else:
                stack.pop()
                star.pop()
        
        if stack == []:
            return True
        else:
            return False
```

