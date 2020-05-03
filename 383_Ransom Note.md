# 383. Ransom Note

https://leetcode.com/problems/ransom-note/

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**Note:**
You may assume that both strings contain only lowercase letters.

```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```



### Solution

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        
        d = dict()
        for key in magazine:
            if key not in d:
                d.update({key:1})
            else:
                d[key] += 1

        for key in ransomNote:
            if key not in d:
                return False
            else:
                if d[key] > 0:
                    d[key] -= 1
                else:
                    return False
        
        return True
```

