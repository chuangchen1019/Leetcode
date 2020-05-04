#  476. Number Complement

https://leetcode.com/problems/number-complement/

**Example 1:**

```
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

**Example 2:**

```
Input: 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```

**Note:**

1. The given integer is guaranteed to fit within the range of a 32-bit signed integer.
2. You could assume no leading zero bit in the integer’s binary representation.



### Solution

主要分為兩種做法，bit operation 跟 string convert。bin(N)可以把N轉成binary表示法string。

```python
class Solution:
    def findComplement(self, num: int) -> int:
        
        ans = 0
        count = 1
        
        if num == 0:
            return 1
        
        while num > 0:
            k = num % 2
            if k == 0:
                ans += count
            count = count << 1
            num = num >> 1
        
        return ans
            
```

