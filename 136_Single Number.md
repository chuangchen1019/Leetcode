# 136. Single Number

https://leetcode.com/problems/move-zeroes/

### Solution

brute force --- 

可用hash table optimize，之後再更新

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        
        if nums == []:
            return 
        nums.sort()
        n = len(nums)
        index = 0
        target = nums[0]
        count = 0
        
        while index != n:
            if nums[index] == target :
                count += 1
            else:
                if count == 1:
                    return nums[index-1]
                else:
                    target = nums[index]
                    count = 1
            
            if index == n-1:
                if count == 1:
                    return nums[index]
                    
            index += 1
```

