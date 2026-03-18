## problem 
majority element 169 
## brute force 
check all the elements occurance and return which is greater than n/2
## approach 
```class Solution {
    public int majorityElement(int[] nums) {
      int c=0;
      int cand=0;
      for (int num:nums){
        if (c==0){
            cand=num;
        }if (num==cand){
            c++;
        }else{
            c--;
        }
      }
      return cand;
        
    }
}
```
## problem2
majority element II 229
## brute force 
create a hashmap and store the frequency of every element then return the one greater than n/3
## optimal approach 
using boyre moore voting 
this time using two candidates because n/3+n/3+n/3=1
so there can be two elements appearing more than n/3
```
