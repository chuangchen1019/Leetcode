# 119. Pascal's Triangle II
###### tags: `leetcode`

https://leetcode.com/problems/pascals-triangle-ii/
### Solution

```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        
        ans = [[1],[1,1]]

        if rowIndex == 0:
            return ans[0]
        elif rowIndex == 1:
            return ans[1]
        else:
            
            for n in range(rowIndex-1):
                temp = []
                temp.append(1)
                apd = ans[n+1]
                for i in range(len(apd)-1):
                    temp.append(apd[i]+apd[i+1])
                temp.append(1) 
                ans.append(temp)
           
           
        
        return ans[rowIndex] 
```