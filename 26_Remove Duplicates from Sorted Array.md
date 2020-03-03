# 26. Remove Duplicates from Sorted Array
###### tags: `leetcode`

![](https://i.imgur.com/SRdmeAB.png)

![](https://i.imgur.com/Lvghjaq.png)

---
### Solution
    下面的做法是透過remove element去除重複物件，其他做法有直接把array對應index的值改掉(此法會更快一點)
```python=
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
  
        num = len(nums)
        index = 0
        if nums == []:
            return 0
        while True:
            if index == num-1:
                break
            if nums[index+1] == nums[index]:
                nums.remove(nums[index+1])
            else:
                index += 1
            num = len(nums)
  
```