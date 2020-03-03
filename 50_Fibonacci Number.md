# 509. Fibonacci Number
###### tags: `leetcode`
https://leetcode.com/problems/fibonacci-number/
### Solution
```cpp=
class Solution {
public:
    int fib(int N) {
        
        int a=0,b=1,c,i;
        if(N == 0)
            return a;
        else if(N == 1)
            return b;
        
        for(i=2 ; i<=N ; i++){
            c = a+b;
            a = b;
            b = c;
        }
        return c;
    }
};
```