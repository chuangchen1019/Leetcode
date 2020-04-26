# 55. Jump Game

https://leetcode.com/problems/jump-game/

Given an array of non-negative integers, you are initially positioned at the first index of the array.

Each element in the array represents your maximum jump length at that position.

Determine if you are able to reach the last index.

**Example 1:**

```
Input: [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
```

**Example 2:**

```
Input: [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum
             jump length is 0, which makes it impossible to reach the last index.
```

### Solution

一開始想用dp做但是設計的沒有很好，原本是先創了一個adjacent matrix去存任兩個index中間有沒有路徑，但在trace的時候發生了一點問題導致不是很順利。

後來上網查了以下這個解法：最大步數maxVal和當下的index i進行比較，如果i > maxVal代表走不到i這個index，每輪都更新前一個index的最大步數。

```
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        
        n=len(nums)
        maxVal = 0
        for i in range(n):
            if i > maxVal:
                return False
            maxVal = max(nums[i]+i,maxVal)
        
        return True
        
```





