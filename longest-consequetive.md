## problem 
longest consequetive sequence 128
## brute force 
for every number keep checking and storing the sequence length and return the longest one
Tc=O(n²)
Sc=O(1)
## better appraoch
sort the array and then keep adding to the length with consequetive sequence 
TC=O(n log n)
SC=O(1) or O(log n)
## optimal approach 
store the elements in a hash set -> avoid duplicasy 
traverse through the hashset and for every element check if n-1 does NOT exists then start the length count and then keep adding till the sequence exists 
## code 
import java.util.HashSet;
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set=new HashSet<>();
        for (int n:nums){
            set.add(n);
        }
        int l=0;
        for (int n:set){
            if (!set.contains(n-1)){
                int current=n;
                int length=1;
                while (set.contains(current+1)){
                    length++;
                    current++;
                }
                l=Math.max(l,length);
            }
        }
        return l;
        
        
    }
}