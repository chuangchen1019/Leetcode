# 118. Pascal's Triangle
###### tags: `leetcode`
https://leetcode.com/problems/pascals-triangle/
### Solution
```python=
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        
        ans = [[1],[1,1]]
        target = []
        
        if numRows == 0:
            ans = []
            return ans
        elif numRows == 1:
            ans = [[1]]
            return ans
        elif numRows == 2:
            return ans
        
        elif numRows > 2:
            for n in range(numRows-2):
                apd = ans[n+1]
                for i in range(len(apd)-1):
                    k = apd[i] + apd[i+1]
                    target.append(k)

                target.insert(0,1)
                target.insert(numRows-1,1)
                ans.append(target)
                target = []
                 
        return ans    
            
```