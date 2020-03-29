# 217. Contains Duplicate

https://leetcode.com/problems/contains-duplicate/

### Soluotion

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        
        if nums == []:
            return
        com = set()
        n = len(nums)
        for i in range(n):
            if nums[i] in com:
                return True
            else:
                com.add(nums[i])
                
        return False
```

