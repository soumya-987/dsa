## problem 
subarray with given xor (similar to longest subarray sum 0)
## brute force 
two nested loops and compute xor 
Time: O(n²)
Space: O(1)

## algo 
-> make a hashmap (int,int) to store (xor, frequency)
-> do map.put(0,1) -> as if we have 0 xor later we can add the frequency later 
-> loop through elements in the array
-> keep computing xr=xr^num for every element
-> for every xr value take out its xor with B and if it already exists then store its frequency in count 
-> also store the new frequency or the sum altoher in the hashmap 
-> return counter 
## optimal approach
``` 
public class Solution {
    public int solve(ArrayList<Integer> A, int B) {
        HashMap<Integer,Integer> map=new HashMap<>();
        int xr=0;
        int c=0;
        map.put(0,1);
        for (int num:A){
            xr=xr^num;
            if (map.containsKey(xr^B)){
                c=c+map.get(xr^B);
            }
            map.put(xr,map.getOrDefault(xr,0)+1);
            
        }
        return c;
    }
}
```
TC & SC = O(n)