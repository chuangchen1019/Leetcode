# 58. Length of Last Word
###### tags: `leetcode`
https://leetcode.com/problems/length-of-last-word/
### Solution
```python
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        arr = s.split(" ");
        lastIndex = 0;
        
        if not arr:
            return 0;
        
        for index in range(len(arr)) : 
            global lastIndex;
            if len(arr[index]) != 0: 
                lastIndex = index;
       
        ansArr = list(arr[lastIndex]);
        ans = len(ansArr);
        
        return ans;
```