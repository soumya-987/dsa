## problem
return the num of subarrays with sum k -> 560
## brute force 
two nestes loops
adding on elements with the beginning position fixed then moving to the next element (next to beginning)
Time: O(n²)
Space: O(1)

## approach 
PS=prefix sum
-> prefix sum
subarray sum (i to j)=PS[j]-PS[i-1]
-> k= PS[j] - PS[i-1]
PS[i-1]=PS[j]-k
-> unordered map 
PS|frequency(table)
eg-[9,4,0,20,3,10,5]
9|1 (9)
13|2 (9+4)
33|1 (9+4+0)
36|1 (etc)

## algo
-> first make a hashmap (int,int) to store (PS,frequency).
-> map.put(0,1) is imp as later when we get sum 0 we add it to the frequency
-> loop trough nums by elements
-> keep updating sum with new element
-> check if hashmap contains (sum-k) total sum - target
-> if yes then do (c=c+map.get(sum-k);) -> this will give the freq of subarrays ending at currect position giving k sum.
-> then do this (map.put(sum,map.getOrDefault(sum,0)+1);) ->this will add the current sum in the hashmap if it is not there or add to the freq if already exists
-> atlast return the count 

## edge case 
if array has only one elemnt 
if all elements are zero 
negative numbers

## code
```class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap <Integer,Integer> map=new HashMap<>();
        map.put(0,1);
        int sum=0;
        int c=0;
        for (int num:nums){
            sum=sum+num;
            if (map.containsKey(sum-k)){
                c=c+map.get(sum-k);
            }
            map.put(sum,map.getOrDefault(sum,0)+1);
        }
        return c;
        
    }
}```
TC & SC = O(n)
