#  Counting Elements

### Solution

```python
class Solution:
    def countElements(self, arr: List[int]) -> int:
        
        count = 0
        n = len(arr)
        for i in range(n):
            if arr[i]+1 in arr:
                count += 1
        return count
```

