## problem
rotate matrix by 90 degree -> 48
## brute force 
create a new matrix and set the elements in rotated position
Time: O(n²)
Space: O(n²)
## optimal approach 
first do transpose of the matrix then reverse each row 
class Solution {
    public void rotate(int[][] matrix) {
        int n=matrix.length;
        for (int i=0;i<n;i++){
            for (int j=i;j<n;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[j][i];
                matrix[j][i]=temp;
            }
        }
        for (int i=0;i<n;i++){
            for (int j=0;j<n/2;j++){
                int temp=matrix[i][j];
                matrix[i][j]=matrix[i][n-1-j];
                matrix[i][n-1-j]=temp;
            }
        }
    }
}