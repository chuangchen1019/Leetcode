# 997. Find the Town Judge

In a town, there are `N` people labelled from `1` to `N`. There is a rumor that one of these people is secretly the town judge.

If the town judge exists, then:

1. The town judge trusts nobody.
2. Everybody (except for the town judge) trusts the town judge.
3. There is exactly one person that satisfies properties 1 and 2.

You are given `trust`, an array of pairs `trust[i] = [a, b]` representing that the person labelled `a` trusts the person labelled `b`.

If the town judge exists and can be identified, return the label of the town judge. Otherwise, return `-1`.

 

**Example 1:**

```
Input: N = 2, trust = [[1,2]]
Output: 2
```

**Example 2:**

```
Input: N = 3, trust = [[1,3],[2,3]]
Output: 3
```

**Example 3:**

```
Input: N = 3, trust = [[1,3],[2,3],[3,1]]
Output: -1
```

**Example 4:**

```
Input: N = 3, trust = [[1,2],[2,3]]
Output: -1
```

**Example 5:**

```
Input: N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
Output: 3
```

**Note:**

1. `1 <= N <= 1000`
2. `trust.length <= 10000`
3. `trust[i]` are all different
4. `trust[i][0] != trust[i][1]`
5. `1 <= trust[i][0], trust[i][1] <= N`

### Solution

有點像是圖學的題目，townJudge就是最後的終點，edge只進不出且數量剛好是N-1。最後還要檢查townjudge不能是起點。

```python
class Solution:
    def findJudge(self, N: int, trust: List[List[int]]) -> int:
        
        if trust == []:
            if N==1:
                return 1
            else:
                return -1
        
        d = dict()
        s = dict()
        
        for i in range(len(trust)):
            
            if trust[i][1] not in d:
                d[trust[i][1]] = 1
            else:
                d[trust[i][1]] += 1
            
            if trust[i][0] not in s:
                s[trust[i][0]] = 1
            else:
                s[trust[i][0]] += 1
        
        for key in d:
            if d[key] == N-1 and key not in s:
                return key
        
        return -1
```

