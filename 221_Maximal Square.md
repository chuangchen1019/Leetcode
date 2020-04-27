# 221. Maximal Square

https://leetcode.com/problems/maximal-square/

Given a 2D binary matrix filled with 0's and 1's, find the largest square containing only 1's and return its area.

**Example:**

```
Input: 

1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0

Output: 4
```

### Solution

Brute force 爆慢

```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        
        if matrix == []:
            return 0
        self.square = 0
        n = len(matrix)
        m = len(matrix[0])
        
        for i in range(n):
            for j in range(m):
                self.findSquare(matrix,i,j,n,m)
                
        return self.square*self.square
         
    def findSquare(self,matrix:List[List[str]],i,j,n,m) -> None:
        
        valid = False
        flag = False
        l = min(n-i,m-j)
        
        for length in range(1,l+1):
            for r in range(i,i+length):
                for c in range(j,j+length):
                    if matrix[r][c] == "0":
                        flag = True
                        break
                if flag == True:
                    break
            if flag == True:
                flag = False
                continue
            else:
                self.square = max(self.square,length)
```

