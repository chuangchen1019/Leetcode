# 268. Missing Number

https://leetcode.com/problems/missing-number/

### Solution 

Math approach / set using

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        
        n = len(nums)
        a = []
        for i in range(n+1):
            a.append(i)
        temp = set(a)
        com = list(temp-set(nums))

        return com[0]
```



Basic approach

```	python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:     
        if nums == []:
            return 
        nums.sort()
        if nums[-1] != len(nums):
          return len(nums)
        elif nums[0]  != 0:
          return 0
        else:
          for i in range(len(nums)):
              if nums[i] != i:
                  return nums[i]-1
        
```

