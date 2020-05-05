# 387. First Unique Character in a String

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**Examples:**

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```

**Note:** You may assume the string contain only lowercase letters.



### Solution

這題跟first unique queue的解法幾乎是相同的，只是一個有分開寫成function，這題是直接寫在一個def裡面。

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        
        queue = []
        seen = dict()
        
        for i in range(len(s)):
            if s[i] not in seen:
                seen[s[i]] = 1
                queue.append(i)
            else:
                seen[s[i]] += 1
       
        while len(queue) > 0 and seen[s[queue[0]]] > 1:
            queue.pop(0)
           
        if queue == []:
            return -1
        else:
            return queue[0]

```

