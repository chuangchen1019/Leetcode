# 983. Minimum Cost For Tickets
https://leetcode.com/problems/minimum-cost-for-tickets/

You have planned some train traveling one year in advance. The days of the year in which you will travel are given as an integer array `days`. Each day is an integer from `1` to `365`.

Train tickets are sold in **three different ways**:

-   a **1-day** pass is sold for `costs[0]` dollars,
-   a **7-day** pass is sold for `costs[1]` dollars, and
-   a **30-day** pass is sold for `costs[2]` dollars.

The passes allow that many days of consecutive travel.

-   For example, if we get a **7-day** pass on day `2`, then we can travel for `7` days: `2`, `3`, `4`, `5`, `6`, `7`, and `8`.

Return _the minimum number of dollars you need to travel every day in the given list of days_.

**Example 1:**

**Input:** days = [1,4,6,7,8,20], costs = [2,7,15]
**Output:** 11
**Explanation:** For example, here is one way to buy passes that lets you travel your travel plan:
On day 1, you bought a 1-day pass for costs[0] = $2, which covered day 1.
On day 3, you bought a 7-day pass for costs[1] = $7, which covered days 3, 4, ..., 9.
On day 20, you bought a 1-day pass for costs[0] = $2, which covered day 20.
In total, you spent $11 and covered all the days of your travel.

**Example 2:**

**Input:** days = [1,2,3,4,5,6,7,8,9,10,30,31], costs = [2,7,15]
**Output:** 17
**Explanation:** For example, here is one way to buy passes that lets you travel your travel plan:
On day 1, you bought a 30-day pass for costs[2] = $15 which covered days 1, 2, ..., 30.
On day 31, you bought a 1-day pass for costs[0] = $2 which covered day 31.
In total, you spent $17 and covered all the days of your travel.

**Constraints:**

-   `1 <= days.length <= 365`
-   `1 <= days[i] <= 365`
-   `days` is in strictly increasing order.
-   `costs.length == 3`
-   `1 <= costs[i] <= 1000`


### Solution (DP)
- 現在的cost = min(1daypass的錢+n-1天的最小cost, 7daypass的錢+n-7天的最小cost, 30daypass的錢+n-30的最小cost
- list要先initial裝東西，不然會沒辦法reference值
- 如果是沒有要travel的天數，則cost值跟前一天相同

```python
class Solution(object):
    def mincostTickets(self, days, costs):
        """
        :type days: List[int]
        :type costs: List[int]
        :rtype: int
        """ 
        dp = []
        
        # Initial
        for i in range(days[-1]):
            dp.append(0)
        
        # DP
        for i in range(days[-1]):
            # 1-day pass
            if i-1 < 0:
                p1 = 0
            else:
                p1 = dp[i-1]
            # 7-day pass
            if i-7 < 0:
                p2 = 0
            else:
                p2 = dp[i-7]
            # 30-day pass
            if i-30 < 0:
                p3 = 0
            else:
                 p3 = dp[i-30]
            
            if i+1 not in days:
                if i > 0:
                    dp[i] = dp[i-1]
            else:
                dp[i] = min(p1+costs[0], p2+costs[1], p3+costs[2])
        
            # print(dp)
            
        return dp[-1]
            
```