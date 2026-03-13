## problem 
rearranging array elements by sign 2149
## brute force 
->make a positive and negative arrray then join them consequently 
arr[2i]=pos[i]
arr[2i+1]=neg[i]
TC-> O(n)+O(n)
SC-> O(n)
## edge cases 
## approach
TC-O(n)
SC-O(n)
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int n=nums.length;
        int[] arr= new int[n];
        int pos=0;
        int neg=1;
        for (int i=0;i<n;i++){
            if (nums[i]>0){
                arr[pos]=nums[i];
                pos=pos+2;
            }else {
                arr[neg]=nums[i];
                neg=neg+2;
            }
        }
        return arr;
    }
}