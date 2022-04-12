# 682. Baseball Game
https://leetcode.com/problems/baseball-game/

### Solution 
- 直接跑一個for，該做什麼事就做什麼處理。

```python
class Solution(object):
    def calPoints(self, ops):
        """
        :type ops: List[str]
        :rtype: int
        """
        
        result = []
        
        for move in ops:
            if move == "D":
                result.append(2*result[-1])
            elif move == "C":
                result.pop()
            elif move == "+":
                result.append(result[-1]+result[-2])
            else:
                result.append(int(move))
                
        return sum(result)
```