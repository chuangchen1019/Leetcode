# 74. Search a 2D Matrix
###### tags: `leetcode`
https://leetcode.com/problems/search-a-2d-matrix/

### Solution
    faster than 96%超開心XD，做法是用每一個row的第一個元素去比大小，省掉跑其他row的時間。
    卻定數字範圍進去找，再回傳有沒有找到
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        
        if matrix == []:
            return False
        elif matrix == [[]]:
            return False
        row = len(matrix)
        column = len(matrix[0])
        for i in range(row):
            if target == matrix[i][0]:
                return True
            elif target < matrix[i][0]:
                for j in range(column):
                    if matrix[i-1][j] == target:
                        return True
                return False
            elif target > matrix[row-1][0]:
                for k in range(column):
                    if matrix[row-1][k] == target:
                        return True
                return False
            else:
                continue
```