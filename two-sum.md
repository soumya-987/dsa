## problem 
two sum problem -> 1
## brute force 
two nested loops working to look for the target 
## optimal approach 
using hashmap 
-> run a loop 
compute complement in each step 
check if the complement exists 
-> if it exists then return the index of prev number and this number 
-> if it does not exist then store the complement with the index 
```
import java.util.HashMap;
class Solution{
    public int[] twoSum(int[]nums,int target){
        HashMap<Integer,Integer> map=new HashMap<>();
        for (int i=0;i<nums.length;i++>){
            int complement=target-nums[i];
            if (map.containsKey(complement)){
                return new int[]{map.get(complement),i};
            }
            map.put(nums[i],i)
        }
        return new int[]{};
    }
}
```