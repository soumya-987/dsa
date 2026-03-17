## problem 
make a pascals triangle 118
## brute force
nCr=
r!(n−r)!
n!
loop through rows from 0 to numrows-1
compute each element with nCr formula 
## optiomal appproach 
make a list in which all the rows will be stored as lists 
eg-
[[1]
[1,1]]
->loop through 0 to numrows-1 (i)
->make a list at every iteration
->loop though 0 to i (j)
-> for every corner set 1 else compute the elements with 
result.get(i-1).get(j-1)+ result.get(i-1).get(j)
## code 
```
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result=new ArrayList<>();
        for (int i=0;i<numRows;i++){
            List<Integer> row=new ArrayList<>();
            for (int j=0;j<=i;j++){
                if (j==0||j==i){
                    row.add(1);
                }else{
                    int val= result.get(i-1).get(j-1)+ result.get(i-1).get(j);
                    row.add(val);
                }
            }
            result.add(row);
        }
        return result;
        
    }
}
```
