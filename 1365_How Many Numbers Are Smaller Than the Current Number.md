# 1365. How Many Numbers Are Smaller Than the Current Number
###### tags: `leetcode`

![](https://i.imgur.com/QA0ZEDY.png)

---
### Solution
    中間有使用到sort index mapping等等的做法
```python=
class Solution:
    def smallerNumbersThanCurrent(self, nums: List[int]) -> List[int]:
        
        original = []
        n = len(nums)
            
        for i in range(n):
            original.append(nums[i]) 
                    
        location = sorted(range(len(nums)), key=lambda k: nums[k])
        nums.sort()
         
        original[location[0]] = 0
        
        for j in range(1,n):     
            
            if nums[j-1] < nums[j]:
                original[location[j]] = j
            else:
                original[location[j]] = original[location[j-1]]
                   
     
        return original
```