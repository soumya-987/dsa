## problem 
length of the longest subarray with a sum equals to 0-> gfg

## brute force
twoo nested loops -> usd to track max length 
(maxLen = Math.max(maxLen, j - i + 1);) 
Time: O(n²)
Space: O(1)

## algo 
-> first make a hashmap (int,int) for storing (sum,index)
-> loop through 0 to array length
-> keep updating sum with every new element
-> check if sum=0 then update maxlen to i+1
-> also check if map contains the sum found at the current index -> as current sum will get crossed out by the sum at that index 
-> then we comapre the max len with i-prev 
-> else we just put the sum with its index in the map
-> return maxlength in last 
## optimal appraoch
```
class Solution {
    int maxLength(int arr[]) {
        HashMap<Integer,Integer> map=new HashMap<>();
        int sum=0;
        int maxlen=0;
        for (int i=0;i<arr.length;i++){
            sum=sum+arr[i];
            if (sum==0){
                maxlen=i+1;
            }
            if (map.containsKey(sum)){
                int prev=map.get(sum);
                maxlen=Math.max(maxlen,i-prev);
            }else {
                map.put(sum,i);
            }
        }
        return maxlen;
    }
}
```
