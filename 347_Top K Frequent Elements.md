# 347. Top K Frequent Elements
Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.

**Example 1:**

**Input:** nums = [1,1,1,2,2,3], k = 2
**Output:** [1,2]

**Example 2:**

**Input:** nums = [1], k = 1
**Output:** [1]

**Constraints:**

-   `1 <= nums.length <= 105`
-   `k` is in the range `[1, the number of unique elements in the array]`.
-   It is **guaranteed** that the answer is **unique**.

### Solution
- 先將次數跟element用dict存起來，進行sorting之後再輸出次數最多的兩個元素
- lambda x:x[1]
- 熟悉Dict的用法，但是跑超級慢，懷疑是因為全部Sort一遍的關係。
- 另外可以注意 ```x[0] for x in result[:k] ```寫法

```python 
class Solution(object):
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """

        rec = {}

        for element in nums:
            if element not in rec.keys():
                rec[element] = 1
            else:
                rec[element] += 1
        
        result = sorted(rec.items(), key=lambda x: x[1], reverse=True)
        
        return [x[0] for x in result[:k]]
```
