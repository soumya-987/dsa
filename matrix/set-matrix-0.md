## problem 
if an element 0 set its whole row and column 0 -> 73
## brute force 
traverse the whole matrix and when 0 disovered mark its whole row and column with -1 then later convert it to 0
1 traverse 
2 0 discovered 
if (matrix[i][j]==0)
3 mark row 
for (int i=0;i<col;i++){
    if (matrix[i][k]!=0){
    matrix[i][k]=-1;
    }
}
4 mark column
for (int i=0;i<row;i++){
    if (matrix[k][j]!=0){
    matrix[k][j]=-1;
    }
}
5 covert -1 to 0 
if (matrix[i][j]==-1){
    matrix[i][j]=0;
}
TC= O((m*n)*(m+n))
SC= O(1)
## better approach 
store the row and col of the 0 element in two seperate arrays.
```class Solution {
    public void setZeroes(int[][] matrix) {
        int r=matrix.length;
        int c=matrix[0].length;
        int[] row=new int[r];
        int[] col=new int[c];
        for (int i=0;i<r;i++){
            for (int j=0;j<c;j++){
                if (matrix[i][j]==0){
                    row[i]=1;
                    col[j]=1;
                    
                }
            }
        }
        for (int i=0;i<r;i++){
            for (int j=0;j<c;j++){
                if (row[i]==1 || col[j]==1){
                    matrix[i][j]=0;
                }
            }
        }
        
        
    }
}```
TC=O(m*n)
SC=O(m+n)
## optimal approach 
using the first row and col as the marker
```class Solution {
    public void setZeroes(int[][] matrix) {
      int r=matrix.length;
      int c=matrix[0].length;
      boolean frow=false;
      boolean fcol=false;
      for (int i=0;i<c;i++){
        if (matrix[0][i]==0){
            frow=true;
            break;
        }
      }
      for (int i=0;i<r;i++){
        if (matrix[i][0]==0){
            fcol=true;
            break;
        }
      }
      for (int i=1;i<r;i++){
        for (int j=1;j<c;j++){
            if (matrix[i][j]==0){
                matrix[0][j]=0;
                matrix[i][0]=0;
            }
        }
      }
      for (int i=1;i<r;i++){
        for (int j=1;j<c;j++){
            if (matrix[0][j]==0 || matrix[i][0]==0){
                matrix[i][j]=0;
            }
        }
      }
      if (frow){
        for (int i=0;i<c;i++){
            matrix[0][i]=0;
        }
      }
      if (fcol){
        for (int i=0;i<r;i++){
            matrix[i][0]=0;
        }
      }
        
    }
}```
