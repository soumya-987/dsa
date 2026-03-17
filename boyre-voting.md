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
}```