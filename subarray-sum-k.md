## problem
return the num of subarrays with sum k 
## brute force 
two nestes loops
adding on elements with the beginning position fixed then moving to the next element (next to beginning)
time complexity-on^2
## approach 
1) prefix sum
subarray sum (i,j)=PS[j]-PS[i-1]
2) k= PS[j] - PS[i-1]
PS[i-1]=PS[j]-k
3) unordered map 
PS|frequency(table)
eg-[9,4,0,20,3,10,5]
9|1
13|2
33|1
36|1

## algo
PS[n]
PS[0]=arr[o]
for (i=1 to n){
    PS[i]=PS[i-1]+arr[i];
}
for (j=0 to m){
    if (PS[j]==k) count ++
    val=PS[j]-k
    (9-33)
    check val in map and add count with freq or if not then add the PS with freq in table
}
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

