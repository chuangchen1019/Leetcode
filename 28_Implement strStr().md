# 28. Implement strStr()
###### tags: `leetcode`
https://leetcode.com/problems/implement-strstr/
### Solution
    回來看以前用java寫的東西怎麼如此巨大(?)
```java
class Solution {
    public int strStr(String haystack, String needle) {
        
        String[] input = haystack.split("");
        String[] compare = needle.split("");
        int flag = 0;
        int flag2 = 0;
        int count = 0;
        int answer = 0;
        
        if(input.length < compare.length)
            return -1;
        
        if(needle.equals(""))
            return 0;
        
        for(int i=0; i<input.length ; i++){
            System.out.print("round:"+" "+i);
            System.out.println();
            
            if(input.length - i < compare.length){
                answer = -1;
                break;
            }
            
            if(input[i].equals(compare[0])){
                
                
                for(int j=0;j<compare.length;j++){
                    if(input[i+j].equals(compare[j])){
                    
                        System.out.print(input[i+j]+" ");
                        count++;
                        answer = i;
                    }
                    else{
                        count = 0;
                        break;  
                    }
                }
                if(count == compare.length)
                    break;
                
                System.out.println("");
            }  
            else 
                answer = -1;
        }
        
        System.out.println("answer:"+answer);
       
        System.out.println("count: "+count);  
        System.out.println("compare length: "+compare.length);
        if(count != compare.length)
            answer = -1;
            
        return answer;
    }  
}
```