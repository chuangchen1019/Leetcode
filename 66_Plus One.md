# 66. Plus One
###### tags: `leetcode`
https://leetcode.com/problems/plus-one/
### Solution
    use C language
```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize){
    int i,j,k;
    
    int *arr = malloc((digitsSize+1) * sizeof(int));
    arr[0] = 0;
    for (i=1;i<=digitsSize; i++) {
        arr[i] = *(digits+i-1);
        //printf("arr[%d]:%d\n", i ,arr[i]);
    }
    
    for(j=digitsSize;j>=0; j--){
        if(arr[j]+1 == 10){
            arr[j] = 0;
        }
        else{
            arr[j] = arr[j]+1;
            break;
        }    
    }
    
    if(arr[0]!=1){
        *returnSize = digitsSize;
        
        return arr+1;
    }
    else{
        *returnSize = digitsSize+1;
        
        return arr;
    }
   
}

```

