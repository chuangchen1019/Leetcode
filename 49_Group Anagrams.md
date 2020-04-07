# 49. Group Anagrams

https://leetcode.com/problems/group-anagrams/

### Solution

str可以sort，然後用hashtable可以減少時間，但目前整體還是很慢，可再優化。

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        
        n = len(strs)
        index = 0
        ans = []
        point = dict()
        
        for i in range(n):
            if ans == []:
                ans.append([strs[i]])
                s = self.convert(strs[i])
                point.update({s:index})
                index += 1
            else:
                target = self.convert(strs[i])
                if target in point:
                    ans[point.get(target)].append(strs[i])
                else:
                    ans.append([strs[i]])
                    s = self.convert(strs[i])
                    point.update({s:index})   
                    index += 1

        return ans
                
    def convert(self, original: str) -> str:
        a = list(original)
        a.sort()
        temp = ""
        temp = temp.join(a)
        return temp
            
```

