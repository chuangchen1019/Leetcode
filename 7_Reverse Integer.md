# 7. Reverse Integer
###### tags: `leetcode`
https://leetcode.com/problems/reverse-integer/

### Solution
```python
class Solution {
    public int reverse(int x) {
     
        int val = x;
        long ans = 0;
        ArrayList<Integer> digit = new ArrayList<Integer>();
        
        while(val >= 1 || val <= -1){
            digit.add(val%10);
            val /= 10;
        }
        
            
        for(int i=0;i<digit.size();i++){
            ans += digit.get(i)*tenpow(10,digit.size()-i-1);        
        }
              
        if(ans >= tenpow(2,31)-1 || ans <= -tenpow(2,31))
            return 0;
        else 
            return (int)ans;
    }
    
    public long tenpow(int count,int power){
        long base = 1;
        
        for(int i=0;i<power;i++){
            base *= count;
        }
        
        return base;
    }
}
```

