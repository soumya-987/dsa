## problem
sort colours 75
## brute force 
any sorting algo taking O(n log n) TC
## edge cases 
if all elements same or single element return as it is 
## approach 
class Solution {
    public void sortColors(int[] nums) {
        int low=0;
        int mid=0;
        int high=nums.length-1;
        while (mid<=high){
            if (nums[mid]==0){
                int temp=nums[low];
                nums[low]=nums[mid];
                nums[mid]=temp;
                low++;
                mid++;
            }else if(nums[mid]==1){
                mid++;
            }else{
                int temp=nums[mid];
                nums[mid]=nums[high];
                nums[high]=temp;
                high--;
            }
        }
        
    }
}