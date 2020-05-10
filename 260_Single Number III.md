# 260. Single Number III

Given an array of numbers `nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

**Example:**

```
Input:  [1,2,1,3,2,5]
Output: [3,5]
```

**Note**:

1. The order of the result is not important. So in the above example, `[5, 3]` is also correct.
2. Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?

### Solution

dict的實際運用，faster than 87%。存{key:count}最後再看只出現一次的數字。

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> List[int]:
        
        ans = []
        d = dict()
        for key in nums:
            if key not in d:
                d[key] = 1
            else:
                d[key] += 1
        for key in d:
            if d[key] == 1:
               ans.append(key)
```

