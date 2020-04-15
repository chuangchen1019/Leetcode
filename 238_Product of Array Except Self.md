# 238. Product of Array Except Self

https://leetcode.com/problems/product-of-array-except-self/

Given an array `nums` of *n* integers where *n* > 1,  return an array `output` such that `output[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

**Example:**

```
Input:  [1,2,3,4]
Output: [24,12,8,6]
```

**Constraint:** It's guaranteed that the product of the elements of any prefix or suffix of the array (including the whole array) fits in a 32 bit integer.

**Note:** Please solve it **without division** and in O(*n*).

**Follow up:**
Could you solve it with constant space complexity? (The output array **does not** count as extra space for the purpose of space complexity analysis.)

### Solution

不能用除法....還要O(n) QQ

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        
        ans = []
        n = len(nums)
        product = 1
        
        
        for i in range(n):
            ans.append(product)
            product *= nums[i]
            
        product = 1
        
        for k in range(n-1,-1,-1):
            ans[k] *= product
            product *= nums[k]
        
        return ans
```

