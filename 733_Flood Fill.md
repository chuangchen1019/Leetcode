# 733. Flood Fill

An `image` is represented by a 2-D array of integers, each integer representing the pixel value of the image (from 0 to 65535).

Given a coordinate `(sr, sc)` representing the starting pixel (row and column) of the flood fill, and a pixel value `newColor`, "flood fill" the image.

To perform a "flood fill", consider the starting pixel, plus any pixels connected 4-directionally to the starting pixel of the same color as the starting pixel, plus any pixels connected 4-directionally to those pixels (also with the same color as the starting pixel), and so on. Replace the color of all of the aforementioned pixels with the newColor.

At the end, return the modified image.

**Example 1:**

```
Input: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
Output: [[2,2,2],[2,2,0],[2,0,1]]
Explanation: 
From the center of the image (with position (sr, sc) = (1, 1)), all pixels connected 
by a path of the same color as the starting pixel are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected
to the starting pixel.
```

**Note:**

The length of `image` and `image[0]` will be in the range `[1, 50]`.

The given starting pixel will satisfy `0 <= sr < image.length` and `0 <= sc < image[0].length`.

The value of each color in `image[i][j]` and `newColor` will be an integer in `[0, 65535]`.



### Solution

dfs的一種，跟之前numbers of islands 題型基本上是一樣的，另外存一個visit table去記有沒有走過，因為有時候newColor和oldColor是一樣的(其實直接return就好XDD)。用dirs存要走的四個方向。

```python
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, newColor: int) -> List[List[int]]:
        visit = [[False for i in range(len(image[0]))] for j in range(len(image))]
        oldColor = image[sr][sc]
        self.fillColor(image,sr,sc,oldColor,newColor,visit)
        
        return image    
        
    def fillColor(self,image: List[List[int]], sr:int, sc:int, oldColor:int, newColor:int, visit:List[List[bool]]) -> None:   
        visit[sr][sc] = True
        image[sr][sc] = newColor
        dirs = [[1,0],[0,1],[-1,0],[0,-1]]
        for pos in dirs:
            r = sr + pos[0]
            c = sc + pos[1]
            if r < len(image) and c < len(image[0]) and r >= 0 and c >= 0:
                if image[r][c] == oldColor and visit[r][c] == False:
                    self.fillColor(image,r,c,oldColor,newColor,visit)
```

