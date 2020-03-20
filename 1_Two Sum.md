# 1. Two Sum
###### tags: `leetcode`
https://leetcode.com/problems/two-sum/

### Solution
    備註：人生第一題leetcode
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