# 1380. Lucky Numbers in a Matrix
###### tags: `leetcode`
https://leetcode.com/problems/lucky-numbers-in-a-matrix/
### Solution
```python
class Solution:
    def luckyNumbers (self, matrix: List[List[int]]) -> List[int]:
        
        if matrix == []:
            return 
        elif matrix == [[]]:
            return 
        
        row = len(matrix)
        col = len(matrix[0])

        rowMin = []
        maxVal = []
        
        for i in range(row):
            minVal = matrix[i][0] 
            print(maxVal)
            for j in range(col):
                if len(maxVal) < col:
                    maxVal.append(matrix[i][j])
                else:
                    if matrix[i][j] > maxVal[j]:
                        maxVal[j] = matrix[i][j]
                if matrix[i][j] < minVal:
                    minVal = matrix[i][j]
            rowMin.append(minVal)

        colMax = set(maxVal)

        for k in range(len(rowMin)):
            if rowMin[k] in colMax:
                ans = rowMin[k]
                return [ans]
```

