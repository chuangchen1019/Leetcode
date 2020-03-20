# 153. Find Minimum in Rotated Sorted Array
###### tags: `leetcode`
![](https://i.imgur.com/MlQ48z8.png)

---
### Solution
    這題直接跑loop竟然會過，原本以為會TLE，另外一提Rotated Sorted的也是這個情況，有點意外XD

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        
        n = len(nums)
        minVal = nums[0]
        for i in range(n):        
            if nums[i] <= minVal:
                minVal = nums[i]
        
        return minVal
```