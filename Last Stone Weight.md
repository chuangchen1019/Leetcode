# Last Stone Weight

Merge to max weight stone until there is only one stone or nothing, return the last stone's weight.

We have a collection of stones, each stone has a positive integer weight.

Each turn, we choose the two **heaviest** stones and smash them together. Suppose the stones have weights `x` and `y` with `x <= y`. The result of this smash is:

- If `x == y`, both stones are totally destroyed;
- If `x != y`, the stone of weight `x` is totally destroyed, and the stone of weight `y` has new weight `y-x`.

At the end, there is at most 1 stone left. Return the weight of this stone (or 0 if there are no stones left.)

**Example 1:**

```
Input: [2,7,4,1,8,1]
Output: 1
Explanation: 
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of last stone.
```

**Note:**

1. `1 <= stones.length <= 30`

2. `1 <= stones[i] <= 1000`


### Solution 2022/04/08
每一輪會進行sorting，判斷最後兩顆石頭是否重量相等，如果相等就將list pop兩次（拿掉兩個石頭），否則就留下一顆重量設定為相差，另一顆pop掉。
最後低於兩顆石頭時離開迴圈，回傳剩下一顆的重量，或是全部碰撞掉就回傳0。
```python
class Solution(object):
    def lastStoneWeight(self, stones):
        """
        :type stones: List[int]
        :rtype: int
        """
        stones.sort()
        while len(stones) >= 2:
            if stones[-1] == stones[-2]:
                stones.pop()
                stones.pop()
            else:
                stones[-2] = abs(stones[-1] - stones[-2])
                stones.pop()
                stones.sort()

        if len(stones) == 0:
            return 0
        else:
            return stones[0]
```


### Solution 2020/04/12
每一輪會將stones sort一次
使用一個list temp去裝碰撞掉的石頭，再reference給stones（好像有點多此一舉？）

```python
class Solution:
    def lastStoneWeight(self, stones: List[int]) -> int:
        
        temp = []
        
        while len(stones) != 1 or 0:
            temp = []
            stones.sort()
            n = len(stones)
            s = abs(stones[-1] - stones[n-2])
            temp.append(s)
            temp += stones[:n-2]
            stones = temp
        
        if len(stones) == 1:
            return stones[0]
        else:
            return 0
            
```

