# 33. Search in Rotated Sorted Array

![](https://i.imgur.com/7jSsJ9S.png)



---
### Solution

    此處是使用O(n)解法，要達到O(logn)可以使用binary search實作


```python
# python3
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        
        s = set(nums)
        if target not in s:
            return -1
        
        n = len(nums)
        for i in range(n):
            if nums[i] == target:
                return i
```