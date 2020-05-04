

# 1009. Complement of Base 10 Integer

https://leetcode.com/problems/complement-of-base-10-integer/

Every non-negative integer `N` has a binary representation. For example, `5` can be represented as `"101"` in binary, `11` as `"1011"` in binary, and so on. Note that except for `N = 0`, there are no leading zeroes in any binary representation.

The *complement* of a binary representation is the number in binary you get when changing every `1` to a `0` and `0` to a `1`. For example, the complement of `"101"` in binary is `"010"` in binary.

For a given number `N` in base-10, return the complement of it's binary representation as a base-10 integer.

**Example 1:**

```
Input: 5
Output: 2
Explanation: 5 is "101" in binary, with complement "010" in binary, which is 2 in base-10.
```

**Example 2:**

```
Input: 7
Output: 0
Explanation: 7 is "111" in binary, with complement "000" in binary, which is 0 in base-10.
```

**Example 3:**

```
Input: 10
Output: 5
Explanation: 10 is "1010" in binary, with complement "0101" in binary, which is 5 in base-10.
```

**Note:**

1. `0 <= N < 10^9`
2. This question is the same as 476: https://leetcode.com/problems/number-complement/



### Solution

這題和476是同樣的題目，但改用string的處理方法。過程中腦子轉不過來的部分是在重組字串的時候使用res = res.join(iterable things)，這造成每次loop的時候res的值都被覆蓋。所以直接做字串加法就好了QQ。

另外int(res,2)後面的2應該是指2進位。

這樣的做法蠻快的，faster than 90% ＾＾

```python
class Solution:
    def bitwiseComplement(self, N: int) -> int:
        
        bit = (bin(N))
        res = ""
        for element in bit[2:]:
            if element == "0":
                res += "1"
            else:
                res += "0"
           
        # Clear >>>
        # res = ''.join(['0' if r == '1' else '1' for r in bit[2:]])
                    
        return int(res,2)
```

