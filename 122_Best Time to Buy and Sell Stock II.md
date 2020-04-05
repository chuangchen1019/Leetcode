# 122. Best Time to Buy and Sell Stock II

https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/

### Solution

速度沒有到非常快，n<2那行可以擋掉小list的測資所以有提速一點。整體看最快的邏輯並沒有差到多少。

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:

        ans = 0
        n = len(prices)
        if n < 2:
            return 0
        for index in range(1,n):
            if prices[index-1] < prices[index]:
                ans += prices[index] - prices[index-1]      
            index += 1
        
        return ans
```

