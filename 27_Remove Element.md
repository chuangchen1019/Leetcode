# 27. Remove Element
###### tags: `leetcode`
https://leetcode.com/problems/remove-element/
### Solution
```java=
class Solution {
    public int removeElement(int[] nums, int val) {
        
        int i=0;
        for(int j=0;j<nums.length;j++){
        
            if(nums[j] != val){
                nums[i] = nums[j];
                i++;
            }
        }     
        for(int k=0;k<nums.length;k++)
            System.out.print(nums[k]+" ");
    
        return i;

    }
}
```