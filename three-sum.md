## problem 
3 sum problem -> 15
## brute force 
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        
        Set<List<Integer>> set=new HashSet<>();
        int n=nums.length;
        for (int i=0;i<n;i++){
            for (int j=i+1;j<n;j++){
                for (int k=j+1;k<n;k++){
                    if (nums[i]+nums[j]+nums[k]==0){
                        List<Integer> temp=Arrays.asList(nums[i],nums[j],nums[k]);
                        Collections.sort(temp);
                        set.add(temp);
                    }
                }
            }
        }
        return new ArrayList<>(set);
    }
}
```
## optimal approach 
-> make a list of list of integers to store 
-> sort the array given ( to avoid duplicates and use two pointer method)
-> run the loop from i to n-1
-> i is one of three elements which is set also if i epeats continue 
->set two pointers left =i+1 and right=n-1
-> check is the sum of all three is equal to zero then store in the list move the pointers and also check if left or right are repeating
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result= new ArrayList<>();
        Arrays.sort(nums);
        for (int i=0;i<nums.length;i++){
            if (i>0 && nums[i]==nums[i-1]){
                continue;
            } 
            int left=i+1;
            int right=nums.length-1;
            while(left<right){
                int sum=nums[i]+nums[left]+nums[right];
                if (sum==0){
                    result.add(Arrays.asList(nums[i],nums[left],nums[right]));
                    left++;
                    right--;
                    while(left<right && nums[left]==nums[left-1]) left++;
                    while(left<right && nums[right]==nums[right+1]) right--;
                }else if (sum<0){
                    left++;
                }else{
                    right--;
                }
            }
        }
        return result;
    }
}
```
