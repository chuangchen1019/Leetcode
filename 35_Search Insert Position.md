# 35. Search Insert Position
###### tags: `leetcode`

![](https://i.imgur.com/xKQwQUf.png)

---
### Solution


```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        
        n = len(nums)
        for i in range(n):
            if nums[i] >= target:
                return i
            else:
                if target < nums[0]:
                    return 0
                elif target > nums[n-1]:
                    return n
```