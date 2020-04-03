# 53. Maximum Subarray

https://leetcode.com/problems/maximum-subarray/

### Solution

第一次多宣告了不需要的變數所以超級慢，又做了一次刪減然後把debug用的print拿掉QQ

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        
        if nums == []:
            return 
        right = 0
        maxValue,total = nums[0],0
        n = len(nums)
        while right < n:
            total += nums[right]
            maxValue = max(maxValue,total)
            if total < 0:
                total = 0
            
            right += 1
            
        return maxValue
            
```

