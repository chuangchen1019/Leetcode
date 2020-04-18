# 200. Number of Islands

https://leetcode.com/problems/number-of-islands/

Given a 2d grid map of `'1'`s (land) and `'0'`s (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
Input:
11110
11010
11000
00000

Output: 1
```

**Example 2:**

```
Input:
11000
11000
00100
00011

Output: 3
```

### Solution

這題主要是使用DFS去把island走一遍，關鍵點是走過的設為0就可以繼續找未走過的島嶼，有些人會多設一個變數visited去紀錄有沒有走過。

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        
        res = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == "1":
                    self.dfs(grid,i,j)
                    res += 1
    
        return res
    def dfs (self,grid,i,j) -> None:
        dirs = [[-1,0],[0,1],[0,-1],[1,0]]
        grid[i][j] = '0'
        for pos in dirs:
            r = i + pos[0]
            c = j + pos[1]
            if r >= 0 and c >= 0 and r < len(grid) and c < len(grid[0]):
                if grid[r][c] == "1":
                    self.dfs(grid,r,c)
                    
```

