# Perform String Shifts

* Example 1

  ```
  Input: s = "abc", shift = [[0,1],[1,2]]
  Output: "cab"
  Explanation: 
  [0,1] means shift to left by 1. "abc" -> "bca"
  [1,2] means shift to right by 2. "bca" -> "cab"
  ```

* Example 2

  ```
  Input: s = "abcdefg", shift = [[1,1],[1,1],[0,2],[1,3]]
  Output: "efgabcd"
  Explanation:  
  [1,1] means shift to right by 1. "abcdefg" -> "gabcdef"
  [1,1] means shift to right by 1. "gabcdef" -> "fgabcde"
  [0,2] means shift to left by 2. "fgabcde" -> "abcdefg"
  [1,3] means shift to right by 3. "abcdefg" -> "efgabcd"
  ```



### Solution

先算完總step再進行rotation

```python
class Solution:
    def stringShift(self, s: str, shift: List[List[int]]) -> str:
        
        if shift == []:
            return s
        direct = 0
        n = len(shift)
        for i in range(n):
            if shift[i][0] == 1:
                direct += shift[i][1]
            else:
                direct -= shift[i][1]
        
        if direct == 0:
            return s     

        if direct > 0:
            for i in range(direct):
                s = s[-1] + s[:-1]      
        elif direct < 0:
            for i in range(-direct):
                s = s[1:] + s[0:1]
        
        return s
```