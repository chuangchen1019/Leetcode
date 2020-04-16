# 1. Two Sum
###### tags: `leetcode`
https://leetcode.com/problems/two-sum/

### Solution
    備註：人生第一題leetcode
* Hash Solution (正解)

  直到過了很久才發現two sum的真正意涵

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        d = {}
        ans = []
        n = len(nums)
        for i in range(n):
            if target-nums[i] not in d:
                d.update({nums[i]:i})
            else:
                ans.append(d.get(target-nums[i]))
                ans.append(i)
        
        return ans
```



* Froce brute

```python
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        int[] answer = new int[2];
        
        for(int i=1;i<nums.length;i++){
            for(int j=0;j<i;j++){
                if(nums[i]+nums[j]==target){
                    answer[0] = j;
                    answer[1] = i;
                }
            }   
        }
        return answer;   
    }
}
```