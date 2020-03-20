# 80. Remove Duplicates from Sorted Array II
###### tags: `leetcode`

https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/

### Solution

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        
        if nums == []:
            return 
        
        index = 0
        count = 0
        temp = nums[0]
        
        while True:
            n = len(nums)
            if index == n:
                break
                
            if nums[index] == temp:
                if count < 2:
                    count += 1 
                    index += 1
                else:
                    nums.remove(nums[index])         
            else:
                temp = nums[index]
                count = 1
                index += 1
```

