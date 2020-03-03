# 12. Integer to Roman
###### tags: `leetcode`

![](https://i.imgur.com/0C4elCl.png)

---
### Solution
```python=
class Solution:
    def intToRoman(self, num: int) -> str:
        
        value = {1:"I",
                 4:"IV",
                 5:"V",
                 9:"IX",
                 10:"X",
                 40:"XL",
                 50:"L",
                 90:"XC",
                 100:"C",
                 400:"CD",
                 500:"D",
                 900:"CM",
                 1000:"M"}
        index = []
        k = len(index)-1
        for key in value.keys():
            index.append(key)
        ans = ""
          
        while num > 0:
            if num >= index[k]:
                num -= index[k]
                ans += value.get(index[k])
            else:
                k -= 1
        
        return ans
```
