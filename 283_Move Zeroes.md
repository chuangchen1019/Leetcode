# 283. Move Zeroes

https://leetcode.com/problems/move-zeroes/

### Solution

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """

        count,index = 0,0
        n = len(nums)
        while index != n:
            if nums[index] == 0:
                count += 1
                nums.remove(nums[index])
            else:
                index += 1
            n = len(nums)
        
        for i in range(count):
            nums.insert(n,0)
```

