# 88. Merge Sorted Array
###### tags: `leetcode`
https://leetcode.com/problems/merge-sorted-array/

### Solution

```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
             
        if m == 0:
            for j in range(n+m):
                nums1[j] = nums2[j]
            return nums1
        if n == 0:
            return nums1
             
        index1 = m-1
        index2 = n-1
        
        for i in range(n+m):
            
            print(nums1[index1],nums2[index2],max(nums1[index1],nums2[index2]))
            print("index1:"+str(index1)+" index2:"+str(index2))
            
            if index1 >= 0 and index2 >=0:
                nums1[n+m-i-1] = max(nums1[index1],nums2[index2])
                if nums1[n+m-i-1] == nums1[index1]:
                    index1 -= 1
                else:
                    index2 -= 1
            
            elif index1 <= -1:
                nums1[n+m-i-1] = nums2[index2]
                index2 -= 1
            
            elif index2 <= -1:
                nums1[n+m-i-1] = nums1[index1]
                index1 -= 1    
                                    
        return nums1    
```