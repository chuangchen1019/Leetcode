# 5353. Bulb Switcher III
###### tags: `leetcode`
https://leetcode.com/contest/weekly-contest-179/problems/bulb-switcher-iii/
### Solution
    用暴力解跑回圈->不意外的TLE。
    最後用index去比目前位置的最大來檢查位置序列是否valid
```python
class Solution:
    def numTimesAllBlue(self, light: List[int]) -> int:
        
        n = len(light)
        blue,maxVal = 0,0

        if light[0] == n:
            return 1     
                
        for i in range(1,n+1):
            maxVal = max(maxVal,light[i-1])
                   
            if i == maxVal:
                blue += 1
            
        
        return blue
                
```
