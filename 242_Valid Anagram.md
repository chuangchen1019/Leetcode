# 242. Valid Anagram

https://leetcode.com/problems/valid-anagram/

Given two strings *s* and *t* , write a function to determine if *t* is an anagram of *s*.

**Example 1:**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```
Input: s = "rat", t = "car"
Output: false
```

**Note:**
You may assume the string contains only lowercase alphabets.

**Follow up:**
What if the inputs contain unicode characters? How would you adapt your solution to such case?

### Solution

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        
        a,b = "",""
        a = a.join(sorted(s))
        b = b.join(sorted(t))
        
        if a == b:
            return True
        else:
            return False
```

