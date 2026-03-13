## problem 
tell the next permutation according to lexicographical order 31
## brute force 
find all the possible permutations and place them in the required order and then tell the next permutation 
TC= O(n!+nlogn!)
SC=O(n!)
## edge case 
if the whole array is descending then we return the smallest permutation 
## approach 
class Solution{
    public void nextPermutation(int[]nums){
        int n=nums.length;
        int i=n-2;
        while(i>=0&& nums[i]>=nums[i+1]){
            i--;
        }
        if (i>=0){
            int j=n-1;
            while (nums[j]<=nums[i]){
                j--;
            }
            int temp=nums[j];
            nums[j]=nums[i];
            nums[i]=temp;
        }
        reverse(nums,i+1,n-1);
    }
    public void reverse(int [] nums,int l,int r){
        while(l<r){
            int temp=nums[r];
            nums[r]=nums[l];
            nums[l]=temp;
            l++;
            r--;
        }
    }
}
TC=O(n)
SC=O(1)
## eg
eg[5,7,4,6,3,2]
pivot=4
then we find the greatest number after 4 i.e=6
then we swap 4 with 6
[5,7,6,4,3,2]
then we reverse the subarray after 6 or i=2
[5,7,6,2,3,6]