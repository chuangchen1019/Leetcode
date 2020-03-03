# 167. Two Sum II - Input array is sorted
https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

### Solution
```python=
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        
        index1 = 0
        index2 = len(numbers)-1
        find = 0
        ans = []
        
        while find != 1:
            if numbers[index1] + numbers[index2] > target:
                index2 -= 1
            elif numbers[index1] + numbers[index2] < target:
                index1 += 1
            else:
                ans = [index1+1, index2+1]
                find = 1
        return ans        
```