### Leetcode 304 - Amazon
- given row1, col1, row2, col2 find sum of elements in that rectangular region


### Prefix Sum:
- for an array arr[], prefix[]
- prefix[i] = arr[i] + prefix[i - 1]
- sum of range[a, b] is `prefix[b] - prefix[a - 1]`

- for 2d array, matrix[][], prefix[][]
- firstly populate 1st row and 1st col of prefix[][]
- prefix[0][j] = matrix[0][j] + prefix[0][j - 1] // 1st row
- prefix[i][0] = matrix[i][0] + prefix[i - 1][0] // 1st col
- prefix sum of matrix uptill cell (i, j) is
  ```prefix[i][j] = matrix[i][j] + prefix[i-1][j] + prefix[i][j-1] - prefix[i-1][j-1]```

#### How to find sum of elements in rectangle (row1, col1, row2, col2)
- total = prefix[row2][col2]
- total - (top of rectangle) - (left of rectangle) + (top left of rectangle)


```
public int[][] prefix;
    public NumMatrix(int[][] matrix) {
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0) return;
        int m = matrix.length;
        int n = matrix[0].length;
        prefix = new int[m][n];
        for(int i = 0; i < m; i++) {
            for(int j = 0; j < n; j++) {
                int top = (i > 0) ? prefix[i-1][j] : 0;
                int left = (j > 0) ? prefix[i][j-1] : 0;
                int topLeft = (i > 0 && j > 0) ? prefix[i-1][j-1] : 0;

                prefix[i][j] = matrix[i][j] + top + left - topLeft;
            }
        }
    }
    
    public int sumRegion(int row1, int col1, int row2, int col2) {
        int total = prefix[row2][col2];
        int top = (row1 > 0) ? prefix[row1 - 1][col2] : 0;
        int left = (col1 > 0) ? prefix[row2][col1 - 1] : 0;
        int topLeft = (row1 > 0 && col1 > 0) ? prefix[row1 - 1][col1 - 1] : 0;

        return total - top - left + topLeft;
    }
```
