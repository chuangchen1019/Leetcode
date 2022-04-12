
# 289. Game of Life
https://leetcode.com/problems/game-of-life/

### Solution
- 活細胞少於兩個活鄰居 -> 這個細胞會死亡
  活細胞有兩個或是三個活鄰居 -> 這個細胞會繼續活著
  活細胞如果有超過三個活鄰居 -> 這個細胞會死掉
  死細胞如果有三個活鄰居 -> 這個細胞會復活
- 使用pos記住該位置周邊的相對位置調整量，就可以不用寫一堆if statement
- 直接修改board，所以先開result存board的值要變成1還是0

```python
class Solution(object):
    def gameOfLife(self, board):
        """
        :type board: List[List[int]]
        :rtype: None Do not return anything, modify board in-place instead.
        """
        
        pos = [(-1,-1), (-1,0), (-1,1), (0,-1), 
		        (0,1), (1,-1), (1,0), (1,1)]
        result = []
        
        for i in range(len(board)):
            temp = []
            for j in range(len(board[0])):
                count = 0
                for index in pos:
                    row = i+index[0]
                    col = j+index[1]
                    if row > -1 and row < len(board) and col > -1 
	                    and col < len(board[0]):
                        
                        if board[row][col] == 1:
                            count += 1
                
                if board[i][j] == 0:
                    if count == 3:
                        temp.append(True)
                    else:
                        temp.append(False)
                else:
                    if count < 2:
                        temp.append(False)
                    elif count > 3:
                        temp.append(False)
                    else:
                        temp.append(True)
                
            result.append(temp)
        
        for i in range(len(board)):
            for j in range(len(board[0])):
                if result[i][j] == True:
                    board[i][j] = 1
                else:
                    board[i][j] = 0
                    
```