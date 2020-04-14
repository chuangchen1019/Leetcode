# Contiguous Array

* Example1

  ```
  Input: [0,1]
  Output: 2
  Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.
  ```

* Example2

  ```
  Input: [0,1,0]
  Output: 2
  Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.
  ```

  題意：長度n的array中0跟1的個數相同，找最大的n

### Solution

紀錄0、1的個數比，遇到1就+1，遇到0就-1。在每一個index紀錄0,1累積的個數比然後存進dict。前置作業dict存取方式為{value(0,1值),index}

Step:

1. 從後面看回來(因為找最大)，如果temp[index]是零的話代表找到，則return到index的陣列長
2. 如果temp[index]不為零的話則進去dict找是否有跟temp[index]值相同的數字(才可相消)，如果有的話就取得dict key的值與index算長度並不斷更新maxLen

```python
class Solution:
    def findMaxLength(self, nums: List[int]) -> int:
        
        if nums == []:
            return 0
        
        # {value:index}
        d = {}
        temp = []
        count = 0
        maxLen = 0
        n = len(nums)
        for i in range(n):
            if nums[i] == 0:
                count -= 1
            else:
                count += 1
            
            temp.append(count)
            if count in d:
                continue
            else:
                d.update({count:i})
        
        for i in range(n):
            if temp[n-1-i] == 0:
                maxLen = max(maxLen,n-i)
                
            elif temp[n-1-i] in d:
                maxLen = max(maxLen,n-i-1-d.get(temp[n-1-i]))
        
        return maxLen
```

