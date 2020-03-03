# 120. Triangle
###### tags: `leetcode`
https://leetcode.com/problems/triangle/

### Solution
```python=
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        
        ans = triangle
        
        for i in range(len(triangle)):
            if i == 0:
                ans[0][0] = triangle[0][0]
                continue             
            for j in range(len(triangle[i])):
                if j == 0 :
                    ans[i][j] = ans[i][j] + ans[i-1][0]
                elif j == len(triangle[i])-1:
                    ans[i][j] = ans[i][j] + ans[i-1][len(triangle[i])-2]
                else:
                    ans[i][j] = ans[i][j] + min(ans[i-1][j-1], ans[i-1][j])
                    
        
        minPath =  ans[len(ans)-1][0]
        for k in range(len(ans)):
            if ans[len(ans)-1][k] <= minPath:
                minPath = ans[len(ans)-1][k]
                
        return minPath
```