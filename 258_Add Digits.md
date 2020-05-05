# 258. Add Digits

https://leetcode.com/problems/add-digits/

Given a non-negative integer `num`, repeatedly add all its digits until the result has only one digit.

**Example:**

```
Input: 38
Output: 2 
Explanation: The process is like: 3 + 8 = 11, 1 + 1 = 2. 
             Since 2 has only one digit, return it.
```



### Solution

**O(n^2) approach**

```python
class Solution:
    def addDigits(self, num: int) -> int:
        
        temp = num
        count = 0
        while temp > 9:
            s = str(temp)
            for element in s:
                count += int(element)          
            temp = count
            count = 0
        
        return temp
            
```



