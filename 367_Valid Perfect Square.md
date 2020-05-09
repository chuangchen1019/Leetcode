# 367. Valid Perfect Square

https://leetcode.com/problems/valid-perfect-square/

Given a positive integer *num*, write a function which returns True if *num* is a perfect square else False.

**Note:** **Do not** use any built-in library function such as `sqrt`.

**Example 1:**

```
Input: 16
Output: true
```

**Example 2:**

```
Input: 14
Output: false
```



### Approach #1

這題的重點不能用sqrt，又不能暴力法，想了一陣子XD -> **重點：找一個適當大小的數字**

設定mid，當mid平方小於num的時候就將mid除以二，當找到小於num的mid，則跑迴圈看能不能找到num值，找到return True，沒找到return False。

```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        
        if num == 1:
            return True
        
        mid = num // 2
        endPoint = 0
        while True:
            target = mid*mid
            if target == num:
                return True
            
            elif target > num:         
                endPoint = mid
                mid = mid // 2
            else:
                for i in range(mid,endPoint+1):  
                    if i*i == num:
                        return True
                
                return False
```

### Approach #2

更加binary search的寫法，但跑起來沒有比較快。設定左跟右的範圍，算出mid比較與num的大小進而下去找值。

```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        
        left = 1
        right = num
        
        while left <= right:
            mid = (left+right)//2
            t = mid ** 2 
            if t == num:
                return True
            elif t > num:
                right = mid-1
            else:
                left = mid+1
        return False
```

