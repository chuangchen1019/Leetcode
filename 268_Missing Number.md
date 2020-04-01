# 268. Missing Number

https://leetcode.com/problems/missing-number/

### Solution 

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        
        if nums == []:
            return 
        
        nums.sort()
        for i in range(len(nums)):
            if nums[i] != i:
                return nums[i]-1
        
        return len(nums)
```

