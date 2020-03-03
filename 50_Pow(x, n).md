# 50. Pow(x, n)
###### tags: `leetcode`
https://leetcode.com/problems/powx-n/
### Solution
```java=
class Solution {
    public double myPow(double x, int n) {
        
        double answer = 1;
        double flag;
        
        if(x == 0)
            return 0;   
        else if(n == 0)
            return 1;
        else if(n == 1)
            return x;
        else if(n>1){
            
            if(n%2 == 0){
                flag = myPow(x,n/2);
                answer = flag*flag;
            }
            else{
                flag = myPow(x,(n-1)/2);
                answer = x*flag*flag;
            }       
        }
        else if(n<1){
            n = -n;      
            if(n%2 == 0){
                flag = myPow(x,n/2);
                answer = flag*flag;
            }
            else{
                flag = myPow(x,(n-1)/2);
                answer = x*flag*flag;
            }
            if(answer != 0)
                answer = 1/answer;  
        }   
        
        return answer;
    }
}
```