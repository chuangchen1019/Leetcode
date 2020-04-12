# Last Stone Weight

Merge to max weight stone until there is only one stone or nothing, return the last stone's weight.

### Solution

可用heap optimize，目前下面為一般解法。

```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        
        temp = []
        
        while len(stones) != 1 or 0:
            temp = []
            stones.sort()
            n = len(stones)
            s = abs(stones[-1] - stones[n-2])
            temp.append(s)
            temp += stones[:n-2]
            stones = temp
        
        if len(stones) == 1:
            return stones[0]
        else:
            return 0
            
```

