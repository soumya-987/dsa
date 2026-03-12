## problem
max subarray 53
## brute force 
check the sum of all the subarrays -> TC very high 
## edge cases 
-> all the numbers ngative ->output must be -1 and not reset to 0 
-> single element returns that element only 
## approach 
class Solution {
    public int maxSubArray(int[] nums) {
        int t=nums[0];
        int g=nums[0];
        int n=nums.length;
        for (int i=1;i<n;i++){
            if(t<0){
                t=0;
            }
            t=t+nums[i];
            if(t>g){
                g=t;
            }
            if (t<0){
                    t=0;
                }
        }
        return g;
        
    }
}