# 202. Happy Number

https://leetcode.com/problems/happy-number/

### Solution

Beats 96.98% solution

關鍵是用set去看有沒有循環，看了一下前面很快的作法基本上都是用set去做，另外有看到一個在轉string的時候把"0"全部換成""應該可以再省一點計算量。

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        
        target = n
        result = 0
        record = set()
        while True:
            if target == 1:
                return True
            temp = list(str(target))
            for i in range(len(temp)):
                result += int(temp[i])**2
            target = result
            result = 0
            if target not in record:
                record.add(target)
            else:
                return False
```

