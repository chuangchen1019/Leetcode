# 3. Longest Substring Without Repeating Characters
###### tags: `leetcode`

![](https://i.imgur.com/zh1RLqY.png)

---
### Solution
    下面是將element加入set中去判斷有無重複，另外用slide window作法應該可以更快
    
```python=
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        
        original = list(s)
        num = len(original)
        temp = {}
        index = 0
        subSize = 0
        maxSize = 0        
        
        if original == []: return 0
        elif original[0] == ' ': return 1
              
        for i in range(num):
            if original[i] not in temp:
                temp.update({original[i]:i})
                maxSize = max(maxSize,len(temp))
            else:
                temp = {k: v for k, v in temp.items() if v > temp.get(original[i])}
                temp.update({original[i]:i})
                maxSize = max(maxSize,len(temp))
                                 
        return maxSize
```