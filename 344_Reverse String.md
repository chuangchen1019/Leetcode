# Reverse String
#easy 

https://leetcode.com/problems/reverse-string/

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with `O(1)` extra memory.

**Example 1:**

**Input:** s = ["h","e","l","l","o"]
**Output:** ["o","l","l","e","h"]

**Example 2:**

**Input:** s = ["H","a","n","n","a","h"]
**Output:** ["h","a","n","n","a","H"]

--- 
### Solution (Swap Solution)
- 看了解法後忘記mirror的東西可以直接交換就好，時間省超多
- 設定兩個指標lo, hi分別指向頭尾，總共跑len(s)/2次，將lo, hi內容交換
- 當lo > hi時跳出迴圈
- 180ms / 21.9MB

```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        #swap solution
        
        lo, hi = 0, len(s)-1
        for i in range(len(s)):
            if lo <= hi:
                temp = s[hi]
                s[hi] = s[lo]
                s[lo] = temp
            lo += 1
            hi -= 1
```

--- 
### Soution (Queue Solution)
- 直觀暴力法...將S由後往前掃一遍，將掃到的字元append到尾端，再pop掉前面一半長度的字元。
- 但是非常慢，跑完全部測資花了1秒鐘QQ，可能是因為要一直增加後面的長度又一直pop導致。
- 1000ms / 21.3MB
```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        length = len(s)
        
        if length != 1:
        
            for i in range(length-1, -1, -1):
                s += s[i]

            for i in range(length):
                s.pop(0)
```