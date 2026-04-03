## problem
arr[i]>2*arr[j] in a particular pair -> 493
## brute force 
go through every number and check all paossible piar 
for i....
    for j....
        if....
            c++;
TC=O(n^2)
SC=O(1)
## optimal appraoch 
using merge sort 
```
class Solution {
    public int reversePairs(int[] nums) {
        return mergeSort(nums,0,nums.length-1);
    }
    private int mergeSort(int[] nums,int left,int right){
        if (left>=right) return 0;
        int mid=left+(right-left)/2;
        // left and right pairs counted and sorted
        int count=mergeSort(nums,left,mid)+mergeSort(nums,mid+1,right);
        int j=mid+1;
        // cross array pairs left
        //left array
        for (int i=left;i<=mid;i++){
            //comparing with right array elements
            while(j<=right && (long) nums[i]>2L*nums[j]){
                //moving the pointer on left array forward 
                j++;
            }
            count=count+(j-(mid+1));
            //adding all the elements from mid to j 
        }
        merge(nums,left,mid,right);
        return count;
    }
    private void merge(int[]nums,int left,int mid,int right){
        int[]temp=new int[right-left+1];
        //final sorted array
        int i=left,j=mid+1,k=0;
        while(i<=mid&&j<=right){
            if (nums[i]<=nums[j]) temp[k++]=nums[i++];
            else temp[k++]=nums[j++];
        }
        while (i<=mid) temp[k++]=nums[i++];
        while (j<=right) temp[k++]=nums[j++];
        // copying leftover elements 
        for (int p=0;p<temp.length;p++){
            nums[left+p]=temp[p];
        //cppying tamp array into original array nums
        }
    }
}
```