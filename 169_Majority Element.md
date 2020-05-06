# 169. Majority Element

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

```
Input: [3,2,3]
Output: 3
```

**Example 2:**

```
Input: [2,2,1,1,1,2,2]
Output: 2
```



### Solution

設定一個dict讓他存 {key:出現次數} 最後再iterating dict 看出現次數是否大於一半。

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        
        n = len(nums) // 2 +1
        
        seen = dict()
        for key in nums:
            if key not in seen:
                seen[key] = 1
            else:
                seen[key] += 1
        
        for key in seen:
            if seen[key] >= n:
                return key
```



只寫一行的做法運用python的collection library，Counter(iterable)可以製成一個hashmap (顧名思義用counter把清單的東西點一遍)，most_common()會返回一個陣列，最前面的代表最常出現，裡面會返回所有元素。

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        return collections.Counter(nums).most_common()[0][0]
```

