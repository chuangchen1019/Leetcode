# 64. Minimum Path Sum

https://leetcode.com/problems/minimum-path-sum/

Given a *m* x *n* grid filled with non-negative numbers, find a path from top left to bottom right which *minimizes* the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.

**Example:**

```
Input:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
Output: 7
Explanation: Because the path 1→3→1→1→1 minimizes the sum.
```

### Solution

使用dp去更新到grid的位置所需的累積最小步數，而dp表格的最後一個element為解答。

```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        
        m = len(grid)
        n = len(grid[0])       
        dp = [[0 for i in range(n)] for j in range(m)]
        
        for r in range(m):
            for c in range(n):    
                if r == 0:
                    if c == 0:
                        dp[r][c] += grid[r][c]
                    else:
                        dp[r][c] = dp[r][c-1] + grid[r][c]
                elif c == 0:
                    dp[r][c] = dp[r-1][c] + grid[r][c]
                else:
                    dp[r][c] = min(dp[r-1][c],dp[r][c-1]) + grid[r][c]
                    

        return dp[m-1][n-1]
```

