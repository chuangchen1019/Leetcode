# 69. Sqrt(x)
###### tags: `leetcode`

https://leetcode.com/problems/sqrtx/
### Solution
    慢到發瘋的寫法，還沒查優化的寫法
```cpp
class Solution {
public:
    int mySqrt(int x) {
        
        int base = 1;
        long int i, target=1;
        if(x==0)
            return 0;
        
        while(true){
            
            target = base * base;
            if(target == x)
                break;
            
            else if(target < x){
                
                if( x - target < 2*base + 1){
                    break;
                }else
                    base++;
            }else 
                break;
        }
        return base;
    }
};
```