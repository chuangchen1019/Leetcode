# 67. Add Binary
###### tags: `leetcode`
https://leetcode.com/problems/add-binary/

### Solution
    

```python=
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        num_list = list(a)
        input1 = [int(x) for x in num_list]
        
        num_list = list(b)
        input2 = [int(y) for y in num_list]
        
        if len(input1) >= len(input2):
            maxStr = input1
            minStr = input2
        else:
            maxStr = input2
            minStr = input1
        
        minIndex = len(minStr)-1
        
        for index in range(len(maxStr)-1,-1,-1):
            if minIndex >= 0:
                maxStr[index] += minStr[minIndex]
            
            if maxStr[index] >= 2 :
                maxStr[index] = maxStr[index]%2
                if index - 1 >= 0:
                    maxStr[index-1] += 1
                else:
                    maxStr.insert(0,1)    
            minIndex = minIndex - 1
            
        
        ans = ""
        for i in range(len(maxStr)):
            ans += str(maxStr[i])
            
        
        
        return ans
```