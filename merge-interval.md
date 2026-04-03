## problem 
merge intervals -> 56
## brute force 
nested loops 
## optimal approach 
-> first sort the array based on the first number 
-> create a list of arrays
-> assign the first element to a variable (current)
-> run a loop 
-> check if the first element's interval start is less than the end of the current's interval (if (intervals[i][0]<=current[1]))
-> if yes then change current's end of the interval to whatever is max (interval[i][1] or current[1])
-> else add current into the result and assign the next element as current
-> at last add current to result for last element
-> then turn the list into array 
## code 
```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals,(a,b)->a[0]-b[0]);
        List<int[]> res= new ArrayList<>();
        int[] current=intervals[0];
        for (int i=0;i<intervals.length;i++){
            if (intervals[i][0]<=current[1]){
                current[1]=Math.max(current[1],intervals[i][1]);
            }else{
                res.add(current);
                current=intervals[i];
            }
            
        }
        res.add(current);
        return res.toArray(new int[res.size()][]);
    }
}
```