### Leetcode 73 - Microsoft | Amazon
- given matrix[m][n], if matrix[i][j] == 0, then make entire i row and j col zero
- inplace solution
- example:
  ```
  input
  1 1 1    
  1 0 1
  1 1 1
  output
  1 0 1
  0 0 0
  1 0 1
  ```

#### Brute force
- TC : O(m * n * (m+n)) SC : O(m * n)
- take a temp[m][n] matrix
  ```
  for(i = 0 to m-1) {
    for(j = 0 to n-1) {
      temp[i][j] = arr[i][j]
    }
  }
  for(i = 0 to m - 1) {
    for(j = 0 to n - 1) {
      if arr[i][j] == 0 {
        for(k = 0 to m-1) temp[k][j] = 0; // entire col
        for(k = 0 to n-1) temp[i][k] = 0; // entire row
      }
    }
  }
  arr = temp
  ```

#### Better Approach 
- TC : O(m*n) SC : O(m + n)
- take two arrays row[m] and col[n] predefined to false
- when arr[i][j] = 0, then row[i] = true, col[j] = true
- row[i] = true, means entire ith row should be made 0
- col[j] = true, means entire jth col should be made 0
  ```
  boolean[] row = new boolean[m]
  boolean[] col = new boolean[n]
  for(i = 0 to m-1) {
    for(j = 0 to n-1) {
      if arr[i][j] == 0, then row[i] = true and col[j] = true
    }
  }
  for(i = 0 to m-1){
    for(j = 0 to n-1) {
      if row[i] || col[j], then arr[i][j] = 0
    }
  }
  ```

#### Optimal Approach
- TC : O(m * n) SC : O(1)
- traverse 1st row and 1st col to whether they were impacted or not
- start from excluding 1st row and 1st col to check which all rows and cols are impacted, and mark the first elements of rows and cols as 0
- finally if 1st row impacetd make it zero, same with 1st col
  ```
  arr[m][n]
  firstRowZero = false, firstColZero = false;
  for(row = 0 to m) {
    if arr[row][0] == 0, then firstColZero = true
  }
  for(col = 0 to n) {
    if arr[0][col] == 0, then firstRowZero = true
  }
  for(row = 0 to m) {
    for(col = 0 to n) {
      if arr[row][col] == 0 {
        arr[row][0] = 0, arr[0][col] = 0
      }
    }
  }
  for(row = 1 to m) {
    for(col = 1 to n) {
      if(arr[row][0] == 0 || arr[0][col] == 0) arr[row][col] = 0
    }
  }
  if(firstRowZero) {
    for(col = 0 to n) {
      arr[0][col] = 0
    }
  }
  if(firstColZero) {
    for(row = 0 to m) {
      arr[row][col] = 0
    }
  }
  ```
