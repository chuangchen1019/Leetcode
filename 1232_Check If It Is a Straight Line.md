# 1232. Check If It Is a Straight Line

https://leetcode.com/problems/check-if-it-is-a-straight-line/

You are given an array `coordinates`, `coordinates[i] = [x, y]`, where `[x, y]` represents the coordinate of a point. Check if these points make a straight line in the XY plane.

**Example 1:**

![img](https://assets.leetcode.com/uploads/2019/10/15/untitled-diagram-2.jpg)\

```
Input: coordinates = [[1,2],[2,3],[3,4],[4,5],[5,6],[6,7]]
Output: true
```

**Example 2:**

**![img](https://assets.leetcode.com/uploads/2019/10/09/untitled-diagram-1.jpg)**

```
Input: coordinates = [[1,1],[2,2],[3,4],[4,5],[5,6],[7,7]]
Output: false
```

 

**Constraints:**

- `2 <= coordinates.length <= 1000`
- `coordinates[i].length == 2`
- `-10^4 <= coordinates[i][0], coordinates[i][1] <= 10^4`
- `coordinates` contains no duplicate point.



### Solution

基本上就是考數學觀念實作

```python
class Solution:
    def checkStraightLine(self, coordinates: List[List[int]]) -> bool:
        
        x = coordinates[1][0] - coordinates[0][0]
        y = coordinates[1][1] - coordinates[0][1]
          
        for i in range(1,len(coordinates)):
            if x == 0:
                if coordinates[i][0] != coordinates[i-1][0]:
                    return False
            elif y == 0:
                if coordinates[i][1] != coordinates[i-1][1]:
                    return False
            else:      
                t1 = coordinates[i][0] - coordinates[i-1][0]
                t2 = coordinates[i][1] - coordinates[i-1][1]
            
                if t1/x != t2/y:
                    return False
        
        return True
```

