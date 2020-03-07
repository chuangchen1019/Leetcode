# 34. Find First and Last Position of Element in Sorted Array
###### tags: `leetcode`

https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/

### Solution
    用binary search可以快很多XD
```python=
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        
        if nums == []:
            return [-1,-1]
        
        start,end = 0,0
        n = len(nums)
        find = False
        for i in range(n):
            if nums[i] == target:
                if find == False:
                    start = i
                    find = True
                else:
                    end = i
        
        if start != 0 and end == 0:
            end = start
        
        if find == False:
            return [-1,-1]
        else:
            return [start,end]
       
```