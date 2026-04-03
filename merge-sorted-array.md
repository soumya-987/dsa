## problem 
merge sorted arrays -> 88
## brute force 
create a new array of size m+n and then merge both in that then copy the result in the nums1
Time: O(m + n)
Space: O(m + n)
## optimal appraoch 
```
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int k=m+n-1;
        int j=n-1;
        int i=m-1;
        int g=m+n;
        while(i >= 0 && j >= 0){
            if (nums1[i]<=nums2[j]){
                nums1[k]=nums2[j];
                j--; 
            else{
                nums1[k]=nums1[i];
                i--;
            }
            k--;
        }
        while (j>=0){
            nums1[k]=nums2[j];
            j--;
            k--;
        }  
    }
}
```