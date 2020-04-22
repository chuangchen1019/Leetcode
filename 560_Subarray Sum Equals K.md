# 560. Subarray Sum Equals K

https://leetcode.com/problems/subarray-sum-equals-k/

Given an array of integers and an integer **k**, you need to find the total number of continuous subarrays whose sum equals to **k**.

**Example 1:**

```
Input:nums = [1,1,1], k = 2
Output: 2
```

**Note:**

1. The length of the array is in range [1, 20,000].
2. The range of numbers in the array is [-1000, 1000] and the range of the integer **k** is [-1e7, 1e7].



### Solution

第一個想法是用sliding window但是若list內有負數就會出error。使用累積區間扣減的技巧才可以都兼顧到。

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        
        n = len(nums)
        index = 0
        val = 0
        count = 0
        s = {}
        num = 1
        
        while index < n:
            val += nums[index]
            
            if val - k == 0:
                count += 1
            if val - k in s:
                count += s.get(val-k)
            
            if val not in s:
                s.update({val:1})
            else:
                s.update({val:s.get(val)+1})
            
            index += 1
        
        return count
```

